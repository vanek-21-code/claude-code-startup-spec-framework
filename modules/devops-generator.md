# DevOps & Deployment Generator

## Purpose
Generate comprehensive DevOps, CI/CD, and deployment specifications for startup infrastructure. This module creates production-ready deployment configurations, infrastructure-as-code templates, and automated deployment pipelines.

## Input Dependencies
- `02-architecture/tech-stack.yaml` - Technology stack decisions
- `03-features/` - Feature specifications for deployment requirements
- `09-testing/` - Testing frameworks for CI/CD integration
- `10-deployment/mvp-implementation-roadmap.yaml` - Deployment timeline and requirements

## Core Processing Logic

### 1. Infrastructure Architecture Selection
```yaml
infrastructure_patterns:
  simple_monolith:
    deployment_target: "single_server"
    containers: "docker_compose"
    database: "managed_service"
    scaling: "vertical_scaling"
    
  microservices:
    deployment_target: "kubernetes"
    containers: "docker_containers"
    database: "distributed_databases"
    scaling: "horizontal_scaling"
    
  serverless:
    deployment_target: "cloud_functions"
    containers: "serverless_containers"
    database: "managed_nosql"
    scaling: "auto_scaling"
```

### 2. CI/CD Pipeline Generation
```yaml
pipeline_stages:
  development:
    - code_quality_checks
    - unit_tests
    - integration_tests
    - security_scanning
    - build_artifacts
    
  staging:
    - deploy_to_staging
    - end_to_end_tests
    - performance_tests
    - security_penetration_tests
    - approval_gates
    
  production:
    - blue_green_deployment
    - health_checks
    - rollback_procedures
    - monitoring_alerts
    - post_deployment_validation
```

### 3. Environment Configuration
```yaml
environment_setup:
  development:
    resources: "minimal"
    debugging: "enabled"
    logging: "verbose"
    database: "local_docker"
    
  staging:
    resources: "production_like"
    debugging: "limited"
    logging: "standard"
    database: "managed_instance"
    
  production:
    resources: "auto_scaling"
    debugging: "disabled"
    logging: "optimized"
    database: "high_availability"
```

## Output Generation

### 1. CI/CD Configuration Files
```yaml
# .github/workflows/ci-cd.yml
name: CI/CD Pipeline
on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Setup Environment
        run: |
          # Environment setup based on tech stack
      - name: Run Tests
        run: |
          # Test commands from testing framework
      - name: Security Scan
        run: |
          # Security scanning based on tech stack
          
  deploy:
    needs: test
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'
    steps:
      - name: Deploy to Production
        run: |
          # Deployment commands based on infrastructure
```

### 2. Docker Configuration
```dockerfile
# Dockerfile
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production

FROM node:18-alpine AS runtime
WORKDIR /app
COPY --from=builder /app/node_modules ./node_modules
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

### 3. Infrastructure as Code
```yaml
# terraform/main.tf (example for cloud deployment)
provider "aws" {
  region = var.aws_region
}

module "vpc" {
  source = "./modules/vpc"
  # VPC configuration based on architecture
}

module "database" {
  source = "./modules/database"
  # Database configuration based on data requirements
}

module "application" {
  source = "./modules/application"
  # Application deployment configuration
}
```

### 4. Kubernetes Manifests
```yaml
# k8s/deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: startup-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: startup-app
  template:
    metadata:
      labels:
        app: startup-app
    spec:
      containers:
      - name: app
        image: startup-app:latest
        ports:
        - containerPort: 3000
        env:
        - name: DATABASE_URL
          valueFrom:
            secretKeyRef:
              name: app-secrets
              key: database-url
```

## Business Model Adaptations

### SaaS Platform
```yaml
saas_devops:
  multi_tenancy: "database_per_tenant"
  scaling: "auto_scaling_based_on_usage"
  backup_strategy: "daily_automated_backups"
  security: "encryption_at_rest_and_transit"
  compliance: "soc2_gdpr_ready"
```

### Marketplace
```yaml
marketplace_devops:
  traffic_patterns: "high_peak_traffic_handling"
  payment_processing: "pci_compliant_infrastructure"
  user_data: "gdpr_compliant_storage"
  search_performance: "elasticsearch_cluster"
  image_processing: "cdn_with_image_optimization"
```

### E-commerce
```yaml
ecommerce_devops:
  high_availability: "99.9_uptime_requirement"
  payment_security: "pci_dss_compliance"
  inventory_sync: "real_time_inventory_updates"
  cdn_setup: "global_cdn_for_product_images"
  peak_traffic: "black_friday_scaling_patterns"
```

## Generated Files Structure

### 05-templates/deployment/
```
deployment/
├── docker/
│   ├── Dockerfile
│   ├── docker-compose.yml
│   └── docker-compose.prod.yml
├── ci-cd/
│   ├── github-actions.yml
│   ├── gitlab-ci.yml
│   └── jenkins-pipeline.groovy
├── infrastructure/
│   ├── terraform/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   └── outputs.tf
│   ├── kubernetes/
│   │   ├── deployment.yaml
│   │   ├── service.yaml
│   │   └── ingress.yaml
│   └── aws-cloudformation/
│       ├── infrastructure.yaml
│       └── application.yaml
├── scripts/
│   ├── deploy.sh
│   ├── rollback.sh
│   └── health-check.sh
└── environments/
    ├── development.env
    ├── staging.env
    └── production.env
```

### 10-deployment/
```
deployment/
├── ci-cd-pipeline.yaml
├── infrastructure-requirements.yaml
├── deployment-strategy.yaml
├── environment-configuration.yaml
├── security-requirements.yaml
└── scaling-strategy.yaml
```

## Quality Assurance

### Validation Checkpoints
1. **Infrastructure Compatibility**: Ensure infrastructure matches tech stack requirements
2. **Security Standards**: Validate security configurations meet industry standards
3. **Scalability Planning**: Verify scaling strategies align with business projections
4. **Cost Optimization**: Ensure infrastructure costs align with budget constraints
5. **Compliance Requirements**: Validate compliance with relevant regulations

### Testing Requirements
- Infrastructure provisioning tests
- Deployment pipeline validation
- Rollback procedure testing
- Security configuration verification
- Performance benchmarking

## Integration Points

### With Other Modules
- **tech-architecture-generator.md**: Uses tech stack decisions for infrastructure selection
- **testing-generator.md**: Integrates testing frameworks into CI/CD pipeline
- **monitoring-generator.md**: Configures monitoring and alerting in deployment pipeline
- **business-logic-generator.md**: Implements business rules in deployment configurations

### With External Systems
- Cloud providers (AWS, GCP, Azure)
- Container orchestration (Kubernetes, Docker Swarm)
- CI/CD platforms (GitHub Actions, GitLab CI, Jenkins)
- Infrastructure as Code tools (Terraform, CloudFormation)

## Success Metrics

### Infrastructure Metrics
- **Deployment Success Rate**: >95% successful deployments
- **Deployment Time**: <15 minutes for standard deployments
- **Rollback Time**: <5 minutes for emergency rollbacks
- **Infrastructure Uptime**: >99.9% availability
- **Security Compliance**: 100% compliance with security standards

### Developer Experience Metrics
- **Developer Onboarding**: <30 minutes to set up local environment
- **Feature Deployment**: <1 hour from code merge to production
- **Infrastructure Changes**: <2 hours to implement infrastructure updates
- **Troubleshooting**: <15 minutes to access logs and metrics

This module ensures startups have production-ready, scalable, and secure deployment infrastructure from day one, reducing time-to-market and operational risks.