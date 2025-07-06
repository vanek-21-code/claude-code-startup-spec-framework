# Monitoring & Observability Generator

## Purpose
Generate comprehensive monitoring, alerting, and observability frameworks for startup applications. This module creates production-ready monitoring configurations, dashboard specifications, and alerting strategies to ensure system reliability and performance.

## Input Dependencies
- `02-architecture/tech-stack.yaml` - Technology stack for monitoring tool selection
- `03-features/` - Feature specifications for monitoring requirements
- `07-business-rules/` - Business logic requiring monitoring
- `10-deployment/` - Deployment architecture for monitoring setup

## Core Processing Logic

### 1. Monitoring Architecture Selection
```yaml
monitoring_patterns:
  basic_startup:
    metrics: "application_metrics"
    logging: "centralized_logging"
    alerting: "basic_alerts"
    dashboards: "operational_dashboards"
    
  scaling_startup:
    metrics: "business_and_technical_metrics"
    logging: "structured_logging"
    alerting: "intelligent_alerts"
    dashboards: "business_intelligence_dashboards"
    
  enterprise_ready:
    metrics: "comprehensive_observability"
    logging: "distributed_tracing"
    alerting: "predictive_alerts"
    dashboards: "executive_dashboards"
```

### 2. Metrics Collection Strategy
```yaml
metrics_categories:
  infrastructure:
    - cpu_usage
    - memory_utilization
    - disk_io
    - network_throughput
    - container_health
    
  application:
    - response_times
    - error_rates
    - throughput
    - dependency_health
    - custom_business_metrics
    
  business:
    - user_registrations
    - revenue_metrics
    - feature_adoption
    - customer_satisfaction
    - conversion_rates
```

### 3. Alerting Framework
```yaml
alert_levels:
  critical:
    response_time: "immediate"
    escalation: "automatic_escalation"
    channels: ["pagerduty", "phone", "slack"]
    
  warning:
    response_time: "within_30_minutes"
    escalation: "manual_escalation"
    channels: ["slack", "email"]
    
  info:
    response_time: "next_business_day"
    escalation: "no_escalation"
    channels: ["email", "dashboard"]
```

## Output Generation

### 1. Application Instrumentation
```javascript
// monitoring/instrumentation.js
const { createPrometheusMetrics } = require('prom-client');
const { createLogger } = require('winston');
const { trace } = require('@opentelemetry/api');

class MonitoringService {
  constructor() {
    this.metrics = this.initializeMetrics();
    this.logger = this.initializeLogger();
    this.tracer = trace.getTracer('startup-app');
  }
  
  initializeMetrics() {
    return {
      httpRequestDuration: new Histogram({
        name: 'http_request_duration_seconds',
        help: 'Duration of HTTP requests in seconds',
        labelNames: ['method', 'route', 'status_code']
      }),
      
      activeUsers: new Gauge({
        name: 'active_users_total',
        help: 'Number of currently active users'
      }),
      
      businessMetrics: new Counter({
        name: 'business_events_total',
        help: 'Total business events',
        labelNames: ['event_type', 'user_type']
      })
    };
  }
  
  trackRequest(req, res, next) {
    const start = Date.now();
    const span = this.tracer.startSpan(`${req.method} ${req.route?.path || req.path}`);
    
    res.on('finish', () => {
      const duration = (Date.now() - start) / 1000;
      this.metrics.httpRequestDuration
        .labels(req.method, req.route?.path || req.path, res.statusCode)
        .observe(duration);
      
      span.setAttributes({
        'http.method': req.method,
        'http.status_code': res.statusCode,
        'http.duration': duration
      });
      span.end();
    });
    
    next();
  }
  
  trackBusinessEvent(eventType, userType, metadata = {}) {
    this.metrics.businessMetrics.labels(eventType, userType).inc();
    
    this.logger.info('Business Event', {
      event_type: eventType,
      user_type: userType,
      metadata,
      timestamp: new Date().toISOString()
    });
  }
}

module.exports = MonitoringService;
```

### 2. Prometheus Configuration
```yaml
# monitoring/prometheus.yml
global:
  scrape_interval: 15s
  evaluation_interval: 15s

rule_files:
  - "alert_rules.yml"

scrape_configs:
  - job_name: 'startup-app'
    static_configs:
      - targets: ['app:3000']
    metrics_path: '/metrics'
    scrape_interval: 10s
    
  - job_name: 'database'
    static_configs:
      - targets: ['postgres-exporter:9187']
    
  - job_name: 'redis'
    static_configs:
      - targets: ['redis-exporter:9121']

alerting:
  alertmanagers:
    - static_configs:
        - targets:
          - alertmanager:9093
```

### 3. Alert Rules
```yaml
# monitoring/alert_rules.yml
groups:
  - name: application.rules
    rules:
      - alert: HighErrorRate
        expr: rate(http_requests_total{status=~"5.."}[5m]) > 0.1
        for: 5m
        labels:
          severity: critical
        annotations:
          summary: "High error rate detected"
          description: "Error rate is {{ $value }} requests per second"
          
      - alert: HighResponseTime
        expr: histogram_quantile(0.95, rate(http_request_duration_seconds_bucket[5m])) > 1
        for: 2m
        labels:
          severity: warning
        annotations:
          summary: "High response time"
          description: "95th percentile response time is {{ $value }} seconds"
          
      - alert: DatabaseConnectionFailure
        expr: up{job="database"} == 0
        for: 1m
        labels:
          severity: critical
        annotations:
          summary: "Database connection failure"
          description: "Database is unreachable"

  - name: business.rules
    rules:
      - alert: LowUserRegistrations
        expr: increase(business_events_total{event_type="user_registration"}[1h]) < 5
        for: 30m
        labels:
          severity: warning
        annotations:
          summary: "Low user registrations"
          description: "Only {{ $value }} registrations in the last hour"
```

### 4. Grafana Dashboards
```json
{
  "dashboard": {
    "title": "Startup Application Overview",
    "panels": [
      {
        "title": "Request Rate",
        "type": "graph",
        "targets": [
          {
            "expr": "rate(http_requests_total[5m])",
            "legendFormat": "Requests/sec"
          }
        ]
      },
      {
        "title": "Error Rate",
        "type": "singlestat",
        "targets": [
          {
            "expr": "rate(http_requests_total{status=~\"5..\"}[5m]) / rate(http_requests_total[5m]) * 100",
            "legendFormat": "Error %"
          }
        ]
      },
      {
        "title": "Active Users",
        "type": "graph",
        "targets": [
          {
            "expr": "active_users_total",
            "legendFormat": "Active Users"
          }
        ]
      },
      {
        "title": "Business Metrics",
        "type": "table",
        "targets": [
          {
            "expr": "increase(business_events_total[24h])",
            "legendFormat": "{{event_type}}"
          }
        ]
      }
    ]
  }
}
```

### 5. Logging Configuration
```javascript
// monitoring/logger.js
const winston = require('winston');
const { ElasticsearchTransport } = require('winston-elasticsearch');

const logger = winston.createLogger({
  level: process.env.LOG_LEVEL || 'info',
  format: winston.format.combine(
    winston.format.timestamp(),
    winston.format.errors({ stack: true }),
    winston.format.json()
  ),
  defaultMeta: {
    service: 'startup-app',
    version: process.env.APP_VERSION || '1.0.0',
    environment: process.env.NODE_ENV || 'development'
  },
  transports: [
    new winston.transports.File({ 
      filename: 'logs/error.log', 
      level: 'error' 
    }),
    new winston.transports.File({ 
      filename: 'logs/combined.log' 
    })
  ]
});

if (process.env.NODE_ENV === 'production') {
  logger.add(new ElasticsearchTransport({
    level: 'info',
    clientOpts: {
      node: process.env.ELASTICSEARCH_URL
    },
    index: 'startup-app-logs'
  }));
} else {
  logger.add(new winston.transports.Console({
    format: winston.format.simple()
  }));
}

module.exports = logger;
```

## Business Model Adaptations

### SaaS Platform
```yaml
saas_monitoring:
  tenant_metrics: "per_tenant_usage_tracking"
  billing_metrics: "subscription_revenue_tracking"
  churn_detection: "user_engagement_monitoring"
  feature_adoption: "per_feature_usage_metrics"
  
  key_metrics:
    - monthly_recurring_revenue
    - customer_acquisition_cost
    - customer_lifetime_value
    - feature_adoption_rates
    - support_ticket_volume
```

### Marketplace
```yaml
marketplace_monitoring:
  transaction_metrics: "gmv_tracking"
  user_behavior: "buyer_seller_analytics"
  matching_efficiency: "conversion_rate_monitoring"
  payment_processing: "payment_success_rates"
  
  key_metrics:
    - gross_merchandise_value
    - take_rate_percentage
    - user_acquisition_funnel
    - search_to_purchase_conversion
    - seller_success_metrics
```

### E-commerce
```yaml
ecommerce_monitoring:
  sales_metrics: "real_time_sales_tracking"
  inventory_monitoring: "stock_level_alerts"
  checkout_funnel: "conversion_optimization_metrics"
  performance_monitoring: "page_load_times"
  
  key_metrics:
    - conversion_rate
    - average_order_value
    - cart_abandonment_rate
    - inventory_turnover
    - customer_satisfaction_score
```

## Generated Files Structure

### 05-templates/monitoring/
```
monitoring/
├── prometheus/
│   ├── prometheus.yml
│   ├── alert_rules.yml
│   └── docker-compose.yml
├── grafana/
│   ├── dashboards/
│   │   ├── application_overview.json
│   │   ├── business_metrics.json
│   │   └── infrastructure.json
│   ├── provisioning/
│   │   ├── datasources.yml
│   │   └── dashboards.yml
│   └── grafana.ini
├── logging/
│   ├── elasticsearch/
│   │   ├── elasticsearch.yml
│   │   └── index_templates.json
│   ├── logstash/
│   │   ├── logstash.conf
│   │   └── pipelines.yml
│   └── filebeat/
│       └── filebeat.yml
├── alerting/
│   ├── alertmanager/
│   │   ├── alertmanager.yml
│   │   └── notification_templates.tmpl
│   ├── pagerduty/
│   │   └── integration_config.yml
│   └── slack/
│       └── webhook_config.yml
└── instrumentation/
    ├── node.js/
    │   ├── metrics.js
    │   ├── tracing.js
    │   └── logging.js
    ├── python/
    │   ├── metrics.py
    │   ├── tracing.py
    │   └── logging.py
    └── go/
        ├── metrics.go
        ├── tracing.go
        └── logging.go
```

### 10-deployment/
```
deployment/
├── monitoring-architecture.yaml
├── alerting-strategy.yaml
├── dashboard-specifications.yaml
├── sla-requirements.yaml
└── incident-response.yaml
```

## Advanced Monitoring Features

### 1. Distributed Tracing
```yaml
tracing_setup:
  technology: "opentelemetry"
  backend: "jaeger"
  sampling_rate: "0.1"
  trace_correlation: "request_id_based"
  
  instrumentation_points:
    - http_requests
    - database_queries
    - external_api_calls
    - background_jobs
    - cache_operations
```

### 2. Synthetic Monitoring
```yaml
synthetic_monitoring:
  uptime_checks:
    - endpoint: "/health"
      frequency: "1_minute"
      timeout: "5_seconds"
      
  user_journey_tests:
    - name: "user_registration_flow"
      steps: ["visit_homepage", "click_signup", "fill_form", "verify_email"]
      frequency: "5_minutes"
      
  api_tests:
    - endpoint: "/api/v1/users"
      method: "GET"
      expected_status: 200
      frequency: "2_minutes"
```

## Quality Assurance

### Validation Checkpoints
1. **Metrics Coverage**: Ensure all critical paths are instrumented
2. **Alert Effectiveness**: Validate alerts trigger appropriate responses
3. **Dashboard Usability**: Verify dashboards provide actionable insights
4. **Performance Impact**: Ensure monitoring doesn't impact application performance
5. **Data Retention**: Validate data retention policies meet requirements

### Testing Requirements
- Load testing with monitoring enabled
- Alert testing and validation
- Dashboard functionality testing
- Log ingestion and search testing
- Synthetic monitoring validation

## Integration Points

### With Other Modules
- **devops-generator.md**: Integrates monitoring into deployment pipeline
- **tech-architecture-generator.md**: Uses tech stack for monitoring tool selection
- **business-logic-generator.md**: Monitors business rule execution
- **feature-generator.md**: Instruments feature usage and performance

### With External Systems
- APM tools (DataDog, New Relic, AppDynamics)
- Log aggregation (ELK Stack, Splunk, Fluentd)
- Alerting platforms (PagerDuty, Opsgenie, Slack)
- Time-series databases (InfluxDB, TimescaleDB)

## Success Metrics

### Operational Metrics
- **Mean Time to Detection (MTTD)**: <5 minutes for critical issues
- **Mean Time to Resolution (MTTR)**: <30 minutes for critical issues
- **Alert Noise Ratio**: <10% false positive alerts
- **Dashboard Load Time**: <3 seconds for all dashboards

### Business Impact Metrics
- **System Availability**: >99.9% uptime
- **Performance SLA**: 95th percentile response time <500ms
- **Data Accuracy**: 100% accurate business metrics
- **Cost Efficiency**: Monitoring costs <2% of infrastructure costs

This module ensures startups have comprehensive observability into their systems, enabling proactive issue detection, performance optimization, and data-driven decision making.