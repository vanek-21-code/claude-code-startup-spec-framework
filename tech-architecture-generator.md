# Tech Architecture Generator v2.0

**Purpose**: Generates comprehensive technical architecture specifications for any startup, outputting to the standardized `02-architecture/` folder structure.

---

## 🎯 **Output Structure Specification**

### **Target Directory**: `02-architecture/`
```yaml
02-architecture/
├── tech-stack.yaml                              # Core technology decisions
├── platform-integration-patterns.yaml           # Platform-specific integration patterns  
├── ai-model-specifications.yaml                 # AI/ML integration specifications
├── performance-requirements.yaml                # Speed, reliability & scalability targets
├── security-compliance.yaml                     # Security frameworks & compliance rules
├── scalability-architecture.yaml                # Growth & scaling technical strategy
├── data-flow-architecture.yaml                  # Data management & flow specifications
└── infrastructure-requirements.yaml             # Hosting, deployment & operations needs
```

---

## 🏗️ **Generation Framework**

### **Input Analysis Decision Tree**
```yaml
startup_analysis:
  business_model_type: [saas, marketplace, e_commerce, platform, service]
  technical_complexity: [simple, moderate, complex, enterprise]
  scale_requirements: [mvp, growth, enterprise]
  industry_vertical: [fintech, healthcare, education, e_commerce, general]
  platform_preference: [web, mobile, desktop, cross_platform]
  ai_integration: [none, basic, advanced, ai_native]
  compliance_needs: [minimal, standard, strict, regulated_industry]
```

### **Architecture Pattern Selection Matrix**
```yaml
pattern_selection:
  web_app:
    simple: "static_site_with_api"
    moderate: "spa_with_backend_api" 
    complex: "microservices_architecture"
    enterprise: "distributed_microservices_with_orchestration"
  
  mobile_app:
    simple: "react_native_with_firebase"
    moderate: "react_native_with_custom_backend"
    complex: "native_apps_with_shared_backend"
    enterprise: "native_apps_with_enterprise_backend"
  
  ai_powered:
    basic: "api_integration_with_openai"
    advanced: "custom_ml_pipeline_with_vector_db"
    ai_native: "multi_model_orchestration_with_fine_tuning"
  
  marketplace:
    simple: "template_based_with_payment_integration"
    moderate: "custom_platform_with_matching_algorithm"
    complex: "multi_sided_platform_with_ai_recommendations"
    enterprise: "distributed_marketplace_with_blockchain_settlements"
```

---

## 📋 **File Generation Specifications**

### **1. tech-stack.yaml**
```yaml
# Template Structure
tech_stack:
  meta:
    startup_name: "{STARTUP_NAME}"
    business_model: "{BUSINESS_MODEL}"
    complexity_level: "{COMPLEXITY_LEVEL}"
    last_updated: "{DATE}"
  
  frontend:
    framework: "{FRONTEND_FRAMEWORK}"
    styling: "{STYLING_APPROACH}"
    state_management: "{STATE_SOLUTION}"
    ui_library: "{UI_COMPONENT_LIBRARY}"
    build_tools: ["{BUILD_TOOL_1}", "{BUILD_TOOL_2}"]
    testing: ["{TESTING_FRAMEWORK_1}", "{TESTING_FRAMEWORK_2}"]
    
  backend:
    language: "{BACKEND_LANGUAGE}"
    framework: "{BACKEND_FRAMEWORK}"
    database_primary: "{PRIMARY_DATABASE}"
    database_cache: "{CACHE_SOLUTION}"
    api_design: "{API_PATTERN}"
    authentication: "{AUTH_SOLUTION}"
    file_storage: "{STORAGE_SOLUTION}"
    
  ai_ml:
    primary_models: ["{AI_MODEL_1}", "{AI_MODEL_2}"]
    vector_database: "{VECTOR_DB_SOLUTION}"
    ml_ops: "{MLOPS_PLATFORM}"
    model_serving: "{MODEL_SERVING_SOLUTION}"
    
  infrastructure:
    hosting: "{HOSTING_PLATFORM}"
    cdn: "{CDN_SOLUTION}"
    monitoring: "{MONITORING_SOLUTION}"
    analytics: "{ANALYTICS_PLATFORM}"
    ci_cd: "{DEPLOYMENT_PIPELINE}"
    
  third_party_integrations:
    payments: "{PAYMENT_PROCESSOR}"
    email: "{EMAIL_SERVICE}"
    sms: "{SMS_SERVICE}"
    analytics: "{ANALYTICS_SERVICE}"
    customer_support: "{SUPPORT_PLATFORM}"

# Dynamic Population Rules
population_rules:
  saas_simple:
    frontend_framework: "React"
    backend_language: "Node.js"
    database_primary: "PostgreSQL"
    hosting: "Vercel + Railway"
    
  marketplace_complex:
    frontend_framework: "React/Next.js"
    backend_language: "Python/Django"
    database_primary: "PostgreSQL"
    database_cache: "Redis"
    hosting: "AWS"
    
  ai_native:
    frontend_framework: "React/Next.js"
    backend_language: "Python/FastAPI"
    database_primary: "PostgreSQL"
    vector_database: "Pinecone"
    ai_models: ["OpenAI GPT-4", "Anthropic Claude"]
    hosting: "AWS/Google Cloud"
```

### **2. platform-integration-patterns.yaml**
```yaml
# Dynamic based on selected platform
platform_integration:
  meta:
    platform_type: "{PLATFORM_TYPE}"
    integration_complexity: "{INTEGRATION_LEVEL}"
    
  # WIX-specific patterns
  wix_patterns:
    custom_elements:
      shadow_dom_required: true
      event_communication: "custom_events_with_bubbling"
      state_management: "internal_state_with_dispatched_events"
      styling_approach: "shadow_dom_css_with_host_styles"
      
    data_integration:
      collections: "wix_data_collections"
      api_calls: "backend_web_modules"
      real_time: "wix_realtime_for_live_updates"
      
    user_management:
      authentication: "wix_members_api"
      permissions: "wix_permissions_api"
      profiles: "member_profile_collections"
      
  # React Native patterns  
  react_native_patterns:
    navigation: "react_navigation_v6"
    state_management: "redux_toolkit_with_rtk_query"
    storage: "async_storage_with_mmkv"
    networking: "axios_with_retry_logic"
    
  # Web app patterns
  web_patterns:
    routing: "react_router_or_next_router"
    state_management: "zustand_or_redux_toolkit"
    data_fetching: "react_query_or_swr"
    authentication: "next_auth_or_custom_jwt"
```

### **3. ai-model-specifications.yaml**
```yaml
ai_integration:
  meta:
    ai_complexity: "{AI_COMPLEXITY_LEVEL}"
    primary_use_cases: ["{USE_CASE_1}", "{USE_CASE_2}"]
    
  model_selection:
    text_generation:
      primary: "{PRIMARY_TEXT_MODEL}"
      fallback: "{FALLBACK_TEXT_MODEL}"
      cost_optimization: "{COST_STRATEGY}"
      
    embeddings:
      model: "{EMBEDDING_MODEL}"
      dimensions: "{VECTOR_DIMENSIONS}"
      use_cases: ["semantic_search", "content_similarity"]
      
    image_processing:
      generation: "{IMAGE_GEN_MODEL}"
      analysis: "{IMAGE_ANALYSIS_MODEL}"
      
  orchestration_patterns:
    simple_integration:
      pattern: "direct_api_calls"
      error_handling: "retry_with_exponential_backoff"
      rate_limiting: "token_bucket_algorithm"
      
    advanced_orchestration:
      pattern: "agent_based_routing"
      context_management: "conversation_memory_with_summarization"
      multi_model_coordination: "confidence_based_model_selection"
      
  performance_optimization:
    caching_strategy: "{CACHING_APPROACH}"
    streaming: "{STREAMING_IMPLEMENTATION}"
    batching: "{BATCH_PROCESSING_STRATEGY}"
    
  monitoring_observability:
    cost_tracking: "{COST_MONITORING_SOLUTION}"
    performance_monitoring: "{PERFORMANCE_TRACKING}"
    quality_metrics: "{QUALITY_ASSESSMENT_FRAMEWORK}"

# Population rules based on startup type
ai_population_rules:
  ai_native_startup:
    primary_text_model: "Claude Sonnet 4"
    fallback_text_model: "GPT-4"
    orchestration: "advanced_agent_based"
    monitoring: "comprehensive_cost_and_quality"
    
  ai_enhanced_startup:
    primary_text_model: "GPT-4o-mini"
    orchestration: "simple_api_integration"
    monitoring: "basic_cost_tracking"
    
  minimal_ai_startup:
    primary_text_model: "GPT-4o-mini"
    orchestration: "direct_api_calls"
    monitoring: "usage_logging_only"
```

### **4. performance-requirements.yaml**
```yaml
performance_targets:
  meta:
    performance_tier: "{PERFORMANCE_TIER}"
    user_scale: "{EXPECTED_USER_SCALE}"
    
  response_times:
    api_endpoints:
      authentication: "< 200ms"
      data_retrieval: "< 500ms"
      ai_processing: "< 3000ms"
      file_uploads: "< 2000ms"
      
    frontend_performance:
      initial_page_load: "< 2000ms"
      subsequent_navigation: "< 500ms"
      search_results: "< 800ms"
      real_time_updates: "< 100ms"
      
  scalability_targets:
    concurrent_users: "{CONCURRENT_USER_TARGET}"
    requests_per_second: "{RPS_TARGET}"
    database_transactions: "{TPS_TARGET}"
    ai_api_calls: "{AI_CALLS_PER_MINUTE}"
    
  availability_requirements:
    uptime_target: "{UPTIME_SLA}"
    max_downtime_per_month: "{DOWNTIME_ALLOWANCE}"
    disaster_recovery_time: "{RECOVERY_TIME_OBJECTIVE}"
    
  monitoring_thresholds:
    cpu_utilization: "< 70%"
    memory_usage: "< 80%"
    database_connection_pool: "< 80%"
    error_rate: "< 1%"

# Performance tier mapping
performance_tiers:
  mvp:
    concurrent_users: 100
    rps_target: 50
    uptime_target: "99%"
    
  growth:
    concurrent_users: 1000
    rps_target: 500
    uptime_target: "99.5%"
    
  enterprise:
    concurrent_users: 10000
    rps_target: 5000
    uptime_target: "99.9%"
```

### **5. security-compliance.yaml**
```yaml
security_framework:
  meta:
    compliance_level: "{COMPLIANCE_LEVEL}"
    industry_requirements: ["{REQUIREMENT_1}", "{REQUIREMENT_2}"]
    
  authentication_security:
    password_policy:
      minimum_length: 8
      complexity_requirements: ["uppercase", "lowercase", "numbers", "symbols"]
      password_history: 5
      max_age_days: 90
      
    multi_factor_authentication:
      required_for: ["admin_users", "high_privilege_operations"]
      methods: ["totp", "sms", "email"]
      backup_codes: true
      
    session_management:
      session_timeout: "30_minutes_inactivity"
      token_rotation: true
      secure_cookie_flags: ["httpOnly", "secure", "sameSite"]
      
  data_protection:
    encryption:
      data_at_rest: "AES-256"
      data_in_transit: "TLS_1.3"
      key_management: "{KEY_MANAGEMENT_SERVICE}"
      
    data_classification:
      public: "no_encryption_required"
      internal: "standard_encryption"
      confidential: "enhanced_encryption_with_access_logging"
      restricted: "highest_encryption_with_approval_workflow"
      
  api_security:
    authentication: "JWT_with_refresh_tokens"
    authorization: "RBAC_with_fine_grained_permissions"
    rate_limiting: "sliding_window_with_user_based_limits"
    input_validation: "strict_schema_validation_with_sanitization"
    
  compliance_frameworks:
    gdpr:
      data_mapping: true
      consent_management: true
      right_to_deletion: true
      data_portability: true
      
    ccpa:
      privacy_notice: true
      opt_out_mechanisms: true
      data_deletion_rights: true
      
    hipaa:
      business_associate_agreements: true
      audit_logging: true
      access_controls: true
      encryption_requirements: true

# Industry-specific security rules
industry_security_mapping:
  fintech:
    compliance_frameworks: ["PCI_DSS", "SOC2", "GDPR"]
    encryption_level: "enhanced"
    audit_requirements: "comprehensive"
    
  healthcare:
    compliance_frameworks: ["HIPAA", "GDPR", "SOC2"]
    encryption_level: "maximum"
    audit_requirements: "comprehensive_with_real_time_monitoring"
    
  general:
    compliance_frameworks: ["GDPR", "CCPA"]
    encryption_level: "standard"
    audit_requirements: "standard"
```

### **6. scalability-architecture.yaml**
```yaml
scalability_strategy:
  meta:
    growth_projection: "{GROWTH_PROJECTION}"
    scaling_timeline: "{SCALING_TIMELINE}"
    
  horizontal_scaling:
    application_tier:
      load_balancing: "{LOAD_BALANCER_TYPE}"
      auto_scaling: "{AUTO_SCALING_STRATEGY}"
      container_orchestration: "{ORCHESTRATION_PLATFORM}"
      
    database_tier:
      read_replicas: "{READ_REPLICA_STRATEGY}"
      sharding_strategy: "{SHARDING_APPROACH}"
      connection_pooling: "{CONNECTION_POOL_SOLUTION}"
      
  vertical_scaling:
    compute_optimization:
      cpu_scaling: "automatic_based_on_utilization"
      memory_scaling: "automatic_based_on_usage_patterns"
      storage_scaling: "automatic_with_performance_monitoring"
      
  caching_strategy:
    application_cache:
      in_memory: "{IN_MEMORY_CACHE}"
      distributed: "{DISTRIBUTED_CACHE}"
      cache_invalidation: "{INVALIDATION_STRATEGY}"
      
    content_delivery:
      cdn: "{CDN_PROVIDER}"
      edge_caching: "{EDGE_STRATEGY}"
      cache_policies: "{CACHE_POLICY_FRAMEWORK}"
      
  microservices_decomposition:
    service_boundaries:
      user_management: "dedicated_user_service"
      core_business_logic: "domain_specific_services"
      ai_processing: "separate_ai_service_cluster"
      notifications: "dedicated_notification_service"
      
    inter_service_communication:
      synchronous: "REST_APIs_with_circuit_breakers"
      asynchronous: "event_driven_with_message_queues"
      data_consistency: "eventual_consistency_with_saga_pattern"

# Scaling timeline mapping
scaling_timelines:
  immediate_mvp:
    architecture: "monolithic_with_scalable_infrastructure"
    database: "single_instance_with_backup"
    caching: "application_level_only"
    
  6_month_growth:
    architecture: "modular_monolith_with_service_extraction"
    database: "primary_with_read_replicas"
    caching: "distributed_cache_layer"
    
  12_month_scale:
    architecture: "microservices_with_api_gateway"
    database: "sharded_with_multiple_read_replicas"
    caching: "multi_tier_caching_with_cdn"
```

### **7. data-flow-architecture.yaml**
```yaml
data_architecture:
  meta:
    data_complexity: "{DATA_COMPLEXITY_LEVEL}"
    real_time_requirements: "{REAL_TIME_NEEDS}"
    
  data_sources:
    user_generated_content:
      ingestion_pattern: "{INGESTION_PATTERN}"
      validation_rules: "{VALIDATION_FRAMEWORK}"
      processing_pipeline: "{PROCESSING_STRATEGY}"
      
    external_apis:
      integration_pattern: "{API_INTEGRATION_PATTERN}"
      data_synchronization: "{SYNC_STRATEGY}"
      error_handling: "{ERROR_RECOVERY_STRATEGY}"
      
    iot_sensors:
      data_collection: "{IOT_COLLECTION_METHOD}"
      edge_processing: "{EDGE_COMPUTING_STRATEGY}"
      telemetry_aggregation: "{TELEMETRY_PROCESSING}"
      
  data_processing:
    real_time_processing:
      stream_processing: "{STREAM_PROCESSING_FRAMEWORK}"
      event_sourcing: "{EVENT_SOURCING_PATTERN}"
      cqrs_implementation: "{CQRS_STRATEGY}"
      
    batch_processing:
      etl_pipeline: "{ETL_FRAMEWORK}"
      data_warehouse: "{WAREHOUSE_SOLUTION}"
      analytics_processing: "{ANALYTICS_PIPELINE}"
      
  data_storage:
    operational_data:
      primary_database: "{OPERATIONAL_DB}"
      backup_strategy: "{BACKUP_APPROACH}"
      retention_policy: "{DATA_RETENTION_RULES}"
      
    analytical_data:
      data_lake: "{DATA_LAKE_SOLUTION}"
      data_warehouse: "{WAREHOUSE_PLATFORM}"
      data_marts: "{DATA_MART_STRATEGY}"
      
  data_access:
    api_layer:
      graphql_implementation: "{GRAPHQL_STRATEGY}"
      rest_api_design: "{REST_API_PATTERNS}"
      real_time_subscriptions: "{REAL_TIME_SOLUTION}"
      
    analytics_access:
      business_intelligence: "{BI_PLATFORM}"
      self_service_analytics: "{SELF_SERVICE_TOOLS}"
      data_visualization: "{VISUALIZATION_PLATFORM}"

# Data complexity level mapping
data_complexity_mapping:
  simple:
    primary_database: "PostgreSQL"
    processing: "application_level_processing"
    analytics: "basic_sql_queries"
    
  moderate:
    primary_database: "PostgreSQL_with_Redis"
    processing: "background_job_processing"
    analytics: "dedicated_analytics_database"
    
  complex:
    primary_database: "microservice_specific_databases"
    processing: "stream_processing_with_event_sourcing"
    analytics: "data_lake_with_real_time_processing"
```

### **8. infrastructure-requirements.yaml**
```yaml
infrastructure_strategy:
  meta:
    deployment_model: "{DEPLOYMENT_MODEL}"
    environment_strategy: "{ENVIRONMENT_STRATEGY}"
    
  hosting_platform:
    production:
      provider: "{CLOUD_PROVIDER}"
      region_strategy: "{REGION_DEPLOYMENT}"
      availability_zones: "{AZ_STRATEGY}"
      
    development:
      provider: "{DEV_HOSTING_PROVIDER}"
      resource_allocation: "{DEV_RESOURCE_STRATEGY}"
      
  compute_resources:
    application_servers:
      instance_types: ["{INSTANCE_TYPE_1}", "{INSTANCE_TYPE_2}"]
      auto_scaling_policy: "{AUTO_SCALING_CONFIG}"
      load_balancer: "{LOAD_BALANCER_CONFIG}"
      
    database_servers:
      instance_type: "{DB_INSTANCE_TYPE}"
      storage_type: "{STORAGE_TYPE}"
      backup_strategy: "{BACKUP_CONFIGURATION}"
      
  networking:
    vpc_configuration:
      subnets: "{SUBNET_STRATEGY}"
      security_groups: "{SECURITY_GROUP_RULES}"
      nat_gateway: "{NAT_CONFIGURATION}"
      
    cdn_configuration:
      provider: "{CDN_PROVIDER}"
      cache_policies: "{CDN_CACHE_STRATEGY}"
      geographic_distribution: "{CDN_REGION_STRATEGY}"
      
  monitoring_logging:
    application_monitoring:
      apm_tool: "{APM_SOLUTION}"
      metrics_collection: "{METRICS_STRATEGY}"
      alerting_rules: "{ALERTING_CONFIGURATION}"
      
    infrastructure_monitoring:
      server_monitoring: "{SERVER_MONITORING_TOOL}"
      network_monitoring: "{NETWORK_MONITORING_SOLUTION}"
      cost_monitoring: "{COST_TRACKING_TOOL}"
      
  security_infrastructure:
    network_security:
      firewall_rules: "{FIREWALL_CONFIGURATION}"
      ddos_protection: "{DDOS_MITIGATION}"
      intrusion_detection: "{IDS_SOLUTION}"
      
    access_management:
      iam_policies: "{IAM_STRATEGY}"
      secret_management: "{SECRET_MANAGEMENT_TOOL}"
      certificate_management: "{SSL_CERTIFICATE_STRATEGY}"

# Deployment model mapping
deployment_models:
  cloud_native:
    provider: "AWS/Google_Cloud/Azure"
    containerization: "Docker_with_Kubernetes"
    infrastructure_as_code: "Terraform_or_CDK"
    
  serverless:
    provider: "AWS_Lambda/Vercel/Netlify"
    database: "managed_database_services"
    monitoring: "cloud_native_monitoring"
    
  hybrid:
    core_services: "cloud_hosted"
    sensitive_data: "on_premise_or_private_cloud"
    integration: "secure_api_gateway"
```

---

## 🔧 **Generation Logic Implementation**

### **Input Processing Algorithm**
```yaml
generation_process:
  step_1_analysis:
    - analyze_business_model
    - determine_technical_complexity
    - identify_compliance_requirements
    - assess_scalability_needs
    
  step_2_pattern_matching:
    - select_architecture_patterns
    - choose_technology_stack
    - determine_integration_patterns
    - define_security_requirements
    
  step_3_customization:
    - apply_industry_specific_rules
    - adjust_for_scale_requirements
    - incorporate_ai_specifications
    - add_compliance_frameworks
    
  step_4_validation:
    - validate_technology_compatibility
    - ensure_performance_feasibility
    - verify_security_completeness
    - check_scalability_coherence
    
  step_5_output_generation:
    - populate_all_yaml_files
    - apply_dynamic_values
    - validate_against_schemas
    - ensure_cross_reference_integrity
```

### **Quality Validation Rules**
```yaml
validation_framework:
  technical_consistency:
    - frontend_backend_compatibility
    - database_application_alignment
    - ai_model_infrastructure_support
    - security_architecture_coherence
    
  performance_feasibility:
    - scalability_architecture_alignment
    - performance_target_achievability
    - resource_requirement_realism
    - cost_optimization_balance
    
  compliance_completeness:
    - industry_requirement_coverage
    - security_framework_adequacy
    - data_protection_completeness
    - audit_trail_sufficiency
```

---

## 🎯 **Output Specifications**

### **File Format Standards**
- **Format**: YAML for all architecture files
- **Schema Validation**: All outputs validate against `04-schemas/` definitions
- **Cross-References**: Automatic dependency mapping to other folders
- **Documentation**: Inline comments explaining technical decisions

### **Dynamic Value Population**
- **Placeholder Replacement**: All `{VARIABLE}` placeholders replaced with startup-specific values
- **Conditional Logic**: IF/THEN rules based on business model and complexity
- **Template Inheritance**: Base patterns extended for specific requirements
- **Validation Hooks**: Automatic validation against business rules and constraints

### **Integration Points**
- **01-foundation/**: Business model drives technical decisions
- **03-features/**: Feature requirements influence architecture choices  
- **07-business-rules/**: Performance SLAs and compliance rules
- **09-testing/**: Performance benchmarks and security testing requirements
- **10-deployment/**: Infrastructure and scaling specifications

This updated tech architecture generator ensures complete alignment with the universal repository structure while providing comprehensive, AI-executable technical specifications for any startup.