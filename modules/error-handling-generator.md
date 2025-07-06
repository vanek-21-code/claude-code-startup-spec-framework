# Error Handling & Recovery Generator

## Purpose
Generate comprehensive error handling, resilience patterns, and recovery strategies for startup applications. This module creates production-ready error handling frameworks, circuit breaker patterns, and graceful degradation strategies to ensure system reliability.

## Input Dependencies
- `02-architecture/tech-stack.yaml` - Technology stack for error handling patterns
- `03-features/` - Feature specifications requiring error handling
- `07-business-rules/` - Business logic error scenarios
- `monitoring-generator.md` - Integration with monitoring and alerting

## Core Processing Logic

### 1. Error Classification Framework
```yaml
error_categories:
  user_errors:
    type: "client_side"
    severity: "low"
    handling: "user_friendly_messages"
    recovery: "user_action_required"
    
  business_logic_errors:
    type: "application_logic"
    severity: "medium"
    handling: "validation_and_feedback"
    recovery: "automatic_retry_or_user_action"
    
  system_errors:
    type: "infrastructure"
    severity: "high"
    handling: "graceful_degradation"
    recovery: "automatic_retry_with_backoff"
    
  external_service_errors:
    type: "dependency_failure"
    severity: "variable"
    handling: "circuit_breaker_pattern"
    recovery: "failover_or_degraded_mode"
```

### 2. Resilience Patterns
```yaml
resilience_patterns:
  retry_pattern:
    strategy: "exponential_backoff"
    max_attempts: 3
    backoff_multiplier: 2
    max_delay: "30_seconds"
    
  circuit_breaker:
    failure_threshold: 5
    timeout: "60_seconds"
    half_open_max_calls: 3
    recovery_timeout: "300_seconds"
    
  bulkhead:
    isolation: "thread_pool_isolation"
    timeout: "10_seconds"
    queue_size: 100
    
  timeout_pattern:
    connection_timeout: "5_seconds"
    read_timeout: "30_seconds"
    total_timeout: "60_seconds"
```

### 3. Graceful Degradation Strategy
```yaml
degradation_levels:
  full_service:
    availability: "100%"
    features: "all_features_available"
    performance: "optimal_performance"
    
  degraded_service:
    availability: "80%"
    features: "core_features_only"
    performance: "reduced_performance"
    
  minimal_service:
    availability: "50%"
    features: "essential_features_only"
    performance: "basic_functionality"
    
  emergency_mode:
    availability: "20%"
    features: "read_only_mode"
    performance: "status_page_only"
```

## Output Generation

### 1. Error Handling Middleware
```javascript
// error-handling/middleware/errorHandler.js
const logger = require('../utils/logger');
const { MonitoringService } = require('../monitoring');

class ErrorHandler {
  constructor() {
    this.monitoring = new MonitoringService();
  }
  
  // Express error handling middleware
  handleError(error, req, res, next) {
    const errorInfo = this.classifyError(error);
    
    // Log error with context
    this.logError(error, req, errorInfo);
    
    // Track error metrics
    this.monitoring.trackError(errorInfo);
    
    // Send appropriate response
    this.sendErrorResponse(res, errorInfo);
  }
  
  classifyError(error) {
    if (error.name === 'ValidationError') {
      return {
        type: 'USER_ERROR',
        severity: 'LOW',
        code: 'VALIDATION_FAILED',
        statusCode: 400,
        userMessage: 'Please check your input and try again.',
        retryable: false
      };
    }
    
    if (error.name === 'UnauthorizedError') {
      return {
        type: 'AUTH_ERROR',
        severity: 'MEDIUM',
        code: 'UNAUTHORIZED',
        statusCode: 401,
        userMessage: 'Authentication required.',
        retryable: false
      };
    }
    
    if (error.code === 'ECONNREFUSED') {
      return {
        type: 'EXTERNAL_SERVICE_ERROR',
        severity: 'HIGH',
        code: 'SERVICE_UNAVAILABLE',
        statusCode: 503,
        userMessage: 'Service temporarily unavailable. Please try again later.',
        retryable: true
      };
    }
    
    // Default to internal server error
    return {
      type: 'SYSTEM_ERROR',
      severity: 'CRITICAL',
      code: 'INTERNAL_ERROR',
      statusCode: 500,
      userMessage: 'An unexpected error occurred. Our team has been notified.',
      retryable: false
    };
  }
  
  logError(error, req, errorInfo) {
    const context = {
      error: {
        message: error.message,
        stack: error.stack,
        type: errorInfo.type,
        code: errorInfo.code
      },
      request: {
        method: req.method,
        url: req.url,
        headers: req.headers,
        body: req.body,
        user: req.user?.id
      },
      timestamp: new Date().toISOString()
    };
    
    if (errorInfo.severity === 'CRITICAL') {
      logger.error('Critical Error', context);
    } else if (errorInfo.severity === 'HIGH') {
      logger.error('High Severity Error', context);
    } else {
      logger.warn('Application Error', context);
    }
  }
  
  sendErrorResponse(res, errorInfo) {
    const response = {
      error: {
        code: errorInfo.code,
        message: errorInfo.userMessage,
        timestamp: new Date().toISOString()
      }
    };
    
    if (process.env.NODE_ENV === 'development') {
      response.error.details = errorInfo;
    }
    
    res.status(errorInfo.statusCode).json(response);
  }
}

module.exports = ErrorHandler;
```

### 2. Circuit Breaker Implementation
```javascript
// error-handling/patterns/CircuitBreaker.js
class CircuitBreaker {
  constructor(options = {}) {
    this.failureThreshold = options.failureThreshold || 5;
    this.recoveryTimeout = options.recoveryTimeout || 60000;
    this.monitoringPeriod = options.monitoringPeriod || 10000;
    
    this.state = 'CLOSED'; // CLOSED, OPEN, HALF_OPEN
    this.failureCount = 0;
    this.lastFailureTime = null;
    this.successCount = 0;
  }
  
  async execute(operation, fallback = null) {
    if (this.state === 'OPEN') {
      if (this.shouldAttemptReset()) {
        this.state = 'HALF_OPEN';
        this.successCount = 0;
      } else {
        return this.executeFallback(fallback);
      }
    }
    
    try {
      const result = await operation();
      this.onSuccess();
      return result;
    } catch (error) {
      this.onFailure();
      
      if (this.state === 'HALF_OPEN') {
        this.state = 'OPEN';
        this.lastFailureTime = Date.now();
      }
      
      if (fallback) {
        return this.executeFallback(fallback);
      }
      
      throw error;
    }
  }
  
  onSuccess() {
    this.failureCount = 0;
    
    if (this.state === 'HALF_OPEN') {
      this.successCount++;
      if (this.successCount >= 3) {
        this.state = 'CLOSED';
      }
    }
  }
  
  onFailure() {
    this.failureCount++;
    this.lastFailureTime = Date.now();
    
    if (this.failureCount >= this.failureThreshold) {
      this.state = 'OPEN';
    }
  }
  
  shouldAttemptReset() {
    return Date.now() - this.lastFailureTime >= this.recoveryTimeout;
  }
  
  async executeFallback(fallback) {
    if (typeof fallback === 'function') {
      return await fallback();
    }
    return fallback;
  }
  
  getState() {
    return {
      state: this.state,
      failureCount: this.failureCount,
      lastFailureTime: this.lastFailureTime,
      successCount: this.successCount
    };
  }
}

module.exports = CircuitBreaker;
```

### 3. Retry Pattern with Exponential Backoff
```javascript
// error-handling/patterns/RetryPattern.js
class RetryPattern {
  constructor(options = {}) {
    this.maxAttempts = options.maxAttempts || 3;
    this.baseDelay = options.baseDelay || 1000;
    this.maxDelay = options.maxDelay || 30000;
    this.backoffMultiplier = options.backoffMultiplier || 2;
    this.jitter = options.jitter || true;
  }
  
  async execute(operation, isRetryable = () => true) {
    let lastError;
    
    for (let attempt = 1; attempt <= this.maxAttempts; attempt++) {
      try {
        return await operation();
      } catch (error) {
        lastError = error;
        
        if (attempt === this.maxAttempts || !isRetryable(error)) {
          throw error;
        }
        
        const delay = this.calculateDelay(attempt);
        await this.sleep(delay);
      }
    }
    
    throw lastError;
  }
  
  calculateDelay(attempt) {
    let delay = this.baseDelay * Math.pow(this.backoffMultiplier, attempt - 1);
    delay = Math.min(delay, this.maxDelay);
    
    if (this.jitter) {
      delay = delay * (0.5 + Math.random() * 0.5);
    }
    
    return Math.floor(delay);
  }
  
  sleep(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
  }
}

// Usage example
const retryPattern = new RetryPattern({
  maxAttempts: 3,
  baseDelay: 1000,
  maxDelay: 10000
});

const isRetryableError = (error) => {
  return error.code === 'ECONNREFUSED' || 
         error.code === 'ETIMEDOUT' ||
         (error.response && error.response.status >= 500);
};

// Example usage
async function makeApiCall() {
  return await retryPattern.execute(
    () => fetch('/api/external-service'),
    isRetryableError
  );
}

module.exports = RetryPattern;
```

### 4. Graceful Degradation Service
```javascript
// error-handling/patterns/GracefulDegradation.js
class GracefulDegradationService {
  constructor() {
    this.serviceStatus = new Map();
    this.degradationRules = new Map();
    this.currentDegradationLevel = 'FULL_SERVICE';
  }
  
  registerService(serviceName, healthCheck, degradationRule) {
    this.serviceStatus.set(serviceName, {
      healthy: true,
      lastCheck: Date.now(),
      healthCheck
    });
    
    this.degradationRules.set(serviceName, degradationRule);
  }
  
  async checkServiceHealth(serviceName) {
    const service = this.serviceStatus.get(serviceName);
    if (!service) return false;
    
    try {
      const isHealthy = await service.healthCheck();
      service.healthy = isHealthy;
      service.lastCheck = Date.now();
      return isHealthy;
    } catch (error) {
      service.healthy = false;
      service.lastCheck = Date.now();
      return false;
    }
  }
  
  async evaluateDegradationLevel() {
    const unhealthyServices = [];
    
    for (const [serviceName, service] of this.serviceStatus) {
      if (!await this.checkServiceHealth(serviceName)) {
        unhealthyServices.push(serviceName);
      }
    }
    
    // Determine degradation level based on unhealthy services
    if (unhealthyServices.length === 0) {
      this.currentDegradationLevel = 'FULL_SERVICE';
    } else if (unhealthyServices.includes('database') || unhealthyServices.includes('auth')) {
      this.currentDegradationLevel = 'EMERGENCY_MODE';
    } else if (unhealthyServices.length >= 2) {
      this.currentDegradationLevel = 'MINIMAL_SERVICE';
    } else {
      this.currentDegradationLevel = 'DEGRADED_SERVICE';
    }
    
    return this.currentDegradationLevel;
  }
  
  isFeatureAvailable(featureName) {
    const degradationRule = this.degradationRules.get(featureName);
    if (!degradationRule) return true;
    
    return degradationRule.availableInModes.includes(this.currentDegradationLevel);
  }
  
  getAlternativeResponse(featureName) {
    const degradationRule = this.degradationRules.get(featureName);
    return degradationRule?.fallbackResponse || null;
  }
}

// Example usage
const degradationService = new GracefulDegradationService();

// Register services and their degradation rules
degradationService.registerService('database', 
  () => checkDatabaseConnection(),
  {
    availableInModes: ['FULL_SERVICE', 'DEGRADED_SERVICE'],
    fallbackResponse: { message: 'Data temporarily unavailable' }
  }
);

degradationService.registerService('external_api',
  () => checkExternalApiHealth(),
  {
    availableInModes: ['FULL_SERVICE'],
    fallbackResponse: { message: 'Using cached data' }
  }
);

module.exports = GracefulDegradationService;
```

### 5. Global Error Boundaries (React)
```javascript
// error-handling/components/ErrorBoundary.jsx
import React from 'react';
import { logger } from '../utils/logger';

class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { 
      hasError: false, 
      error: null,
      errorInfo: null 
    };
  }
  
  static getDerivedStateFromError(error) {
    return { hasError: true };
  }
  
  componentDidCatch(error, errorInfo) {
    this.setState({
      error,
      errorInfo
    });
    
    // Log error to monitoring service
    logger.error('React Error Boundary Caught Error', {
      error: {
        message: error.message,
        stack: error.stack
      },
      errorInfo: {
        componentStack: errorInfo.componentStack
      },
      url: window.location.href,
      userAgent: navigator.userAgent,
      timestamp: new Date().toISOString()
    });
    
    // Track error in analytics
    if (window.analytics) {
      window.analytics.track('Frontend Error', {
        error_message: error.message,
        component_stack: errorInfo.componentStack
      });
    }
  }
  
  render() {
    if (this.state.hasError) {
      return (
        <div className="error-boundary">
          <h2>Something went wrong</h2>
          <p>We're sorry, but something unexpected happened.</p>
          <button 
            onClick={() => window.location.reload()}
            className="retry-button"
          >
            Reload Page
          </button>
          
          {process.env.NODE_ENV === 'development' && (
            <details style={{ whiteSpace: 'pre-wrap', marginTop: '20px' }}>
              <summary>Error Details (Development Only)</summary>
              {this.state.error && this.state.error.toString()}
              <br />
              {this.state.errorInfo.componentStack}
            </details>
          )}
        </div>
      );
    }
    
    return this.props.children;
  }
}

export default ErrorBoundary;
```

## Business Model Adaptations

### SaaS Platform
```yaml
saas_error_handling:
  tenant_isolation: "error_isolation_per_tenant"
  subscription_errors: "billing_failure_graceful_handling"
  feature_gating: "graceful_feature_unavailability"
  data_consistency: "tenant_data_integrity_protection"
  
  specific_patterns:
    - subscription_expired_handling
    - feature_limit_exceeded_handling
    - tenant_data_isolation_errors
    - billing_webhook_failures
```

### Marketplace
```yaml
marketplace_error_handling:
  transaction_integrity: "payment_failure_rollback"
  user_type_errors: "buyer_seller_specific_handling"
  matching_failures: "search_algorithm_fallbacks"
  communication_errors: "messaging_system_resilience"
  
  specific_patterns:
    - payment_processing_failures
    - seller_verification_errors
    - product_listing_failures
    - review_system_errors
```

### E-commerce
```yaml
ecommerce_error_handling:
  inventory_errors: "stock_level_inconsistency_handling"
  payment_failures: "checkout_process_resilience"
  shipping_errors: "fulfillment_error_recovery"
  cart_persistence: "shopping_cart_recovery"
  
  specific_patterns:
    - out_of_stock_handling
    - payment_gateway_failures
    - shipping_calculation_errors
    - tax_calculation_failures
```

## Generated Files Structure

### 05-templates/error-handling/
```
error-handling/
├── middleware/
│   ├── errorHandler.js
│   ├── requestValidation.js
│   └── rateLimiting.js
├── patterns/
│   ├── CircuitBreaker.js
│   ├── RetryPattern.js
│   ├── GracefulDegradation.js
│   └── BulkheadPattern.js
├── components/
│   ├── ErrorBoundary.jsx
│   ├── ErrorPage.jsx
│   └── LoadingFallback.jsx
├── utils/
│   ├── errorClassification.js
│   ├── errorLogger.js
│   └── errorMetrics.js
├── configurations/
│   ├── error-codes.json
│   ├── retry-policies.yaml
│   └── circuit-breaker-config.yaml
└── tests/
    ├── errorHandler.test.js
    ├── circuitBreaker.test.js
    └── retryPattern.test.js
```

### 02-architecture/
```
architecture/
├── error-handling-architecture.yaml
├── resilience-patterns.yaml
├── failure-modes-analysis.yaml
└── recovery-strategies.yaml
```

## Quality Assurance

### Validation Checkpoints
1. **Error Coverage**: Ensure all error scenarios are handled
2. **User Experience**: Validate user-friendly error messages
3. **System Recovery**: Test automatic recovery mechanisms
4. **Performance Impact**: Ensure error handling doesn't degrade performance
5. **Monitoring Integration**: Verify error tracking and alerting

### Testing Requirements
- Chaos engineering tests
- Error injection testing
- Circuit breaker functionality tests
- Recovery procedure validation
- User experience testing under error conditions

## Integration Points

### With Other Modules
- **monitoring-generator.md**: Integrates error tracking and alerting
- **devops-generator.md**: Implements error handling in deployment pipeline
- **feature-generator.md**: Adds error handling to feature specifications
- **business-logic-generator.md**: Handles business rule validation errors

### With External Systems
- Error tracking services (Sentry, Rollbar, Bugsnag)
- Logging platforms (ELK Stack, Splunk)
- Monitoring tools (DataDog, New Relic)
- Alerting systems (PagerDuty, Slack)

## Success Metrics

### Reliability Metrics
- **Error Rate**: <1% of all requests result in errors
- **Recovery Time**: <30 seconds for automatic recovery
- **User Impact**: <5% of users affected by any single error
- **False Positive Rate**: <10% of alerts are false positives

### User Experience Metrics
- **Error Resolution**: >90% of user errors resolved without support
- **Error Message Clarity**: >80% user satisfaction with error messages
- **Recovery Success**: >95% of users can complete tasks after errors
- **Support Ticket Reduction**: <50% reduction in error-related support tickets

This module ensures startups have robust, resilient applications that handle errors gracefully, maintain user experience during failures, and recover automatically when possible.