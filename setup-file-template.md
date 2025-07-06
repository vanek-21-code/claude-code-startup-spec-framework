# Setup File Template for Universal Startup Specification Framework

This template generates the complete setup file that Claude Code will use to build any startup repository. The framework populates all `{PLACEHOLDER}` values with startup-specific content.

---

# Setup Instructions for {STARTUP_NAME}

## 🎯 Project Overview
**Startup Name:** {STARTUP_NAME}  
**Business Model:** {BUSINESS_MODEL_TYPE}  
**Industry:** {INDUSTRY_VERTICAL}  
**Tech Stack:** {PRIMARY_TECH_STACK}  
**Brand Personality:** {BRAND_ARCHETYPE}  
**Target Users:** {PRIMARY_USER_TYPES}  
**Launch Timeline:** {MVP_TARGET_DATE}

---

## 🏗️ Repository Generation Instructions

### **Processing Order (Critical for Claude Code)**
```yaml
processing_sequence:
  1: "00-meta"          # Universal instructions & dependencies
  2: "01-foundation"    # Business context & strategy  
  3: "02-architecture"  # Technical requirements & decisions
  4: "04-schemas"       # Validation frameworks (before features)
  5: "05-templates"     # Code generation templates
  6: "03-features"      # Feature specifications (validated against schemas)
  7: "07-business-rules" # Business logic encoding
  8: "08-brand"         # Brand personality implementation
  9: "06-workflows"     # Claude Code execution plans
  10: "09-testing"      # Quality assurance frameworks
  11: "10-deployment"   # Launch & operations planning
```

### **Validation Requirements**
- Every YAML file must validate against corresponding schema
- All cross-references must resolve correctly
- Brand personality must be consistent across all files
- Business model logic must be coherent throughout

---

## 📁 Complete Repository Structure to Generate

```
{STARTUP_NAME}-setup/
├── 00-meta/
│   ├── README.md                                    # Project overview & Claude Code instructions
│   ├── claude-instructions.md                       # AI execution workflow & validation rules
│   ├── folder-processing-order.yaml                 # Processing sequence & dependencies
│   └── cross-reference-map.yaml                     # Inter-file dependency mapping
│
├── 01-foundation/
│   ├── product-vision.yaml                          # {PRODUCT_MISSION}, {VALUE_PROPOSITION}, {CORE_PURPOSE}
│   ├── business-model.yaml                          # {REVENUE_STREAMS}, {PRICING_STRATEGY}, {MARKET_STRATEGY}
│   ├── user-personas.yaml                           # {PRIMARY_USERS}, {SECONDARY_USERS}, {USER_JOURNEYS}
│   ├── success-metrics.yaml                         # {PRIMARY_KPIS}, {SECONDARY_METRICS}, {MEASUREMENT_FRAMEWORK}
│   ├── competitive-analysis.yaml                    # {COMPETITORS}, {DIFFERENTIATION}, {COMPETITIVE_ADVANTAGE}
│   └── market-positioning.yaml                      # {TARGET_MARKET}, {POSITIONING_STRATEGY}, {BRAND_PROMISE}
│
├── 02-architecture/
│   ├── tech-stack.yaml                              # {FRONTEND_TECH}, {BACKEND_TECH}, {DATABASE_TECH}, {AI_TECH}
│   ├── {PLATFORM_INTEGRATION_TYPE}-patterns.yaml   # {PLATFORM_SPECIFIC_PATTERNS} (e.g., wix-integration-patterns.yaml)
│   ├── ai-model-specifications.yaml                 # {AI_MODELS}, {AI_WORKFLOWS}, {AI_PERFORMANCE_REQUIREMENTS}
│   ├── performance-requirements.yaml                # {SPEED_TARGETS}, {RELIABILITY_TARGETS}, {SCALABILITY_TARGETS}
│   ├── security-compliance.yaml                     # {SECURITY_REQUIREMENTS}, {COMPLIANCE_NEEDS}, {DATA_PROTECTION}
│   ├── scalability-architecture.yaml                # {SCALING_STRATEGY}, {INFRASTRUCTURE_GROWTH}, {CAPACITY_PLANNING}
│   ├── data-flow-architecture.yaml                  # {DATA_SOURCES}, {DATA_PROCESSING}, {DATA_STORAGE}
│   └── infrastructure-requirements.yaml             # {HOSTING_NEEDS}, {DEPLOYMENT_REQUIREMENTS}, {MONITORING_NEEDS}
│
├── 03-features/
│   ├── F001-{PRIMARY_FEATURE_NAME}.yaml             # {CORE_BUSINESS_FUNCTIONALITY}
│   ├── F002-{USER_MANAGEMENT_TYPE}.yaml             # {AUTHENTICATION}, {USER_PROFILES}, {USER_ONBOARDING}
│   ├── F003-{CORE_INTERACTION_NAME}.yaml            # {MAIN_USER_INTERACTION_FEATURE}
│   ├── F004-{DATA_MANAGEMENT_TYPE}.yaml             # {DATA_HANDLING}, {CONTENT_MANAGEMENT}
│   ├── F005-{DISCOVERY_FEATURE_NAME}.yaml           # {SEARCH}, {RECOMMENDATIONS}, {CONTENT_DISCOVERY}
│   ├── F006-{COMMUNICATION_TYPE}.yaml               # {MESSAGING}, {NOTIFICATIONS}, {USER_COMMUNICATION}
│   ├── F007-{MONETIZATION_TYPE}.yaml                # {PAYMENTS}, {BILLING}, {REVENUE_FEATURES}
│   ├── F008-{ANALYTICS_TYPE}.yaml                   # {USER_ANALYTICS}, {BUSINESS_ANALYTICS}, {REPORTING}
│   ├── F009-{MODERATION_TYPE}.yaml                  # {CONTENT_SAFETY}, {QUALITY_CONTROL}, {COMMUNITY_MANAGEMENT}
│   ├── F010-{NOTIFICATION_TYPE}.yaml                # {ALERTS}, {UPDATES}, {ENGAGEMENT_FEATURES}
│   ├── F011-{RESPONSIVE_TYPE}.yaml                  # {MOBILE_OPTIMIZATION}, {CROSS_PLATFORM_SUPPORT}
│   ├── F012-{ADMIN_TYPE}.yaml                       # {ADMIN_DASHBOARD}, {SYSTEM_MANAGEMENT}
│   ├── F013-{INTEGRATION_TYPE}.yaml                 # {THIRD_PARTY_APIS}, {EXTERNAL_INTEGRATIONS}
│   └── F014-{ADVANCED_FEATURES_TYPE}.yaml           # {PREMIUM_FEATURES}, {FUTURE_ROADMAP_FEATURES}
│
├── 04-schemas/
│   ├── feature-specification.schema.json            # Universal feature validation schema
│   ├── user-story.schema.json                       # Actor-action-constraint validation schema
│   ├── behavioral-spec.schema.json                  # When-then-unless behavior validation schema
│   ├── business-rule.schema.json                    # Business logic validation schema
│   ├── api-contract.schema.json                     # API endpoint validation schema
│   ├── ui-component.schema.json                     # UI component validation schema
│   ├── test-specification.schema.json               # Testing requirement validation schema
│   ├── performance-benchmark.schema.json            # Performance criteria validation schema
│   └── validation-rules.schema.json                 # Overall validation framework schema
│
├── 05-templates/
│   ├── {FRONTEND_FRAMEWORK}-components/
│   │   ├── base-component.template.{FILE_EXTENSION} # {COMPONENT_TEMPLATE} for {FRONTEND_TECH}
│   │   ├── styling-framework.template.{CSS_EXT}     # {STYLING_APPROACH} template
│   │   ├── state-management.template.{FILE_EXTENSION} # {STATE_MANAGEMENT_PATTERN} template
│   │   └── {PLATFORM_TYPE}-integration.template.{FILE_EXTENSION} # Platform-specific integration template
│   ├── backend-api/
│   │   ├── rest-endpoint.template.{BACKEND_EXT}     # {BACKEND_FRAMEWORK} API template
│   │   ├── data-validation.template.{BACKEND_EXT}   # {VALIDATION_FRAMEWORK} template
│   │   ├── authentication.template.{BACKEND_EXT}    # {AUTH_STRATEGY} template
│   │   └── error-handling.template.{BACKEND_EXT}    # {ERROR_HANDLING_PATTERN} template
│   ├── database-models/
│   │   ├── data-model.template.{DB_EXT}             # {DATABASE_TYPE} schema template
│   │   ├── data-relationships.template.{DB_EXT}     # {RELATIONSHIP_MAPPING} template
│   │   └── migration-scripts.template.{DB_EXT}      # {MIGRATION_STRATEGY} template
│   ├── test-suites/
│   │   ├── unit-test.template.{TEST_EXT}            # {TESTING_FRAMEWORK} unit test template
│   │   ├── integration-test.template.{TEST_EXT}     # {INTEGRATION_TEST_APPROACH} template
│   │   ├── e2e-test.template.{TEST_EXT}             # {E2E_TESTING_FRAMEWORK} template
│   │   └── performance-test.template.{TEST_EXT}     # {PERFORMANCE_TEST_TOOLS} template
│   ├── documentation/
│   │   ├── api-docs.template.md                     # {API_DOCUMENTATION_STYLE} template
│   │   ├── user-guide.template.md                   # {USER_DOCUMENTATION_APPROACH} template
│   │   └── developer-docs.template.md               # {DEVELOPER_DOCUMENTATION_STYLE} template
│   └── deployment/
│       ├── ci-cd-pipeline.template.{DEPLOYMENT_EXT} # {CI_CD_STRATEGY} template
│       ├── environment-config.template.{CONFIG_EXT} # {ENVIRONMENT_MANAGEMENT} template
│       └── monitoring-setup.template.{MONITOR_EXT}  # {MONITORING_STRATEGY} template
│
├── 06-workflows/
│   ├── repository-generation.yaml                   # Claude Code repo creation workflow
│   ├── feature-implementation.yaml                  # {DEVELOPMENT_METHODOLOGY} workflow
│   ├── testing-automation.yaml                      # {TESTING_STRATEGY} automation workflow
│   ├── deployment-pipeline.yaml                     # {DEPLOYMENT_STRATEGY} workflow
│   ├── quality-assurance.yaml                       # {QA_APPROACH} validation workflow
│   ├── dependency-management.yaml                   # {DEPENDENCY_STRATEGY} workflow
│   ├── version-control.yaml                         # {VERSION_CONTROL_STRATEGY} workflow
│   └── maintenance-procedures.yaml                  # {MAINTENANCE_APPROACH} workflow
│
├── 07-business-rules/
│   ├── pricing-algorithms.yaml                      # {PRICING_LOGIC}, {REVENUE_CALCULATIONS}
│   ├── user-permission-matrix.yaml                  # {ACCESS_CONTROL}, {ROLE_PERMISSIONS}
│   ├── content-moderation-rules.yaml                # {SAFETY_RULES}, {QUALITY_STANDARDS}
│   ├── workflow-automation.yaml                     # {BUSINESS_PROCESS_AUTOMATION}
│   ├── analytics-tracking.yaml                      # {DATA_COLLECTION_RULES}, {TRACKING_REQUIREMENTS}
│   ├── subscription-management.yaml                 # {BILLING_LOGIC}, {SUBSCRIPTION_RULES}
│   ├── compliance-requirements.yaml                 # {LEGAL_REQUIREMENTS}, {REGULATORY_COMPLIANCE}
│   └── business-process-optimization.yaml           # {EFFICIENCY_RULES}, {OPTIMIZATION_ALGORITHMS}
│
├── 08-brand/
│   ├── personality-encoding.yaml                    # {BRAND_PERSONALITY_RULES}, {ARCHETYPE_IMPLEMENTATION}
│   ├── language-patterns.yaml                       # {TONE_GUIDELINES}, {VOICE_PATTERNS}
│   ├── ui-personality-rules.yaml                    # {VISUAL_PERSONALITY}, {UI_BEHAVIOR_RULES}
│   ├── copy-guidelines.yaml                         # {CONTENT_WRITING_RULES}, {MESSAGING_GUIDELINES}
│   ├── marketing-frameworks.yaml                    # {MARKETING_MESSAGE_PATTERNS}, {CAMPAIGN_FRAMEWORKS}
│   ├── voice-tone-matrix.yaml                       # {CONTEXTUAL_TONE_RULES}, {SITUATION_BASED_VOICE}
│   └── brand-compliance-validation.yaml             # {BRAND_CONSISTENCY_RULES}, {VALIDATION_CRITERIA}
│
├── 09-testing/
│   ├── acceptance-criteria-framework.yaml           # {SUCCESS_VALIDATION_RULES}, {ACCEPTANCE_STANDARDS}
│   ├── performance-benchmarks.yaml                  # {SPEED_TARGETS}, {RELIABILITY_STANDARDS}
│   ├── security-validation-suite.yaml               # {SECURITY_TESTING_REQUIREMENTS}, {VULNERABILITY_CHECKS}
│   ├── accessibility-testing.yaml                   # {A11Y_COMPLIANCE_TESTING}, {ACCESSIBILITY_STANDARDS}
│   ├── brand-compliance-testing.yaml                # {BRAND_CONSISTENCY_VALIDATION}, {PERSONALITY_TESTING}
│   ├── load-testing-specifications.yaml             # {SCALABILITY_TESTING}, {PERFORMANCE_UNDER_LOAD}
│   ├── user-acceptance-testing.yaml                 # {UAT_FRAMEWORK}, {USER_VALIDATION_CRITERIA}
│   └── automated-qa-workflows.yaml                  # {CONTINUOUS_QUALITY_WORKFLOWS}, {AUTOMATED_VALIDATION}
│
└── 10-deployment/
    ├── mvp-implementation-roadmap.yaml              # {MVP_DEVELOPMENT_PLAN}, {FEATURE_PRIORITIES}
    ├── launch-strategy.yaml                         # {GO_TO_MARKET_PLAN}, {LAUNCH_SEQUENCE}
    ├── scaling-architecture.yaml                    # {GROWTH_SCALING_PLAN}, {INFRASTRUCTURE_SCALING}
    ├── monitoring-alerting.yaml                     # {SYSTEM_MONITORING}, {ALERTING_STRATEGY}
    ├── backup-disaster-recovery.yaml                # {DATA_PROTECTION}, {DISASTER_RECOVERY_PLAN}
    ├── post-launch-iteration-plan.yaml              # {CONTINUOUS_IMPROVEMENT}, {ITERATION_STRATEGY}
    ├── growth-strategy.yaml                         # {USER_GROWTH_PLAN}, {REVENUE_GROWTH_STRATEGY}
    └── maintenance-operations.yaml                  # {ONGOING_OPERATIONS}, {MAINTENANCE_PROCEDURES}
```

---

## 🎯 Startup-Specific Content Population

### **Business Model Context: {BUSINESS_MODEL_TYPE}**
```yaml
# Generated content adapts based on business model:
saas:
  revenue_focus: "subscription_recurring_revenue"
  key_features: ["subscription_management", "usage_analytics", "customer_success"]
  primary_metrics: ["MRR", "churn_rate", "customer_lifetime_value"]

marketplace:
  revenue_focus: "commission_transaction_fees"
  key_features: ["seller_onboarding", "buyer_matching", "transaction_processing"]
  primary_metrics: ["GMV", "take_rate", "marketplace_liquidity"]

creator_platform:
  revenue_focus: "creator_monetization_sharing"
  key_features: ["creator_tools", "audience_engagement", "monetization_features"]
  primary_metrics: ["creator_earnings", "audience_growth", "engagement_rate"]

# Additional business models supported:
# e_commerce, social_platform, ai_service, blockchain_app, mobile_app, etc.
```

### **Industry Vertical Adaptations: {INDUSTRY_VERTICAL}**
```yaml
# Industry-specific requirements automatically added:
fintech:
  compliance_requirements: ["PCI_DSS", "SOX", "financial_regulations"]
  security_enhancements: ["enhanced_authentication", "transaction_monitoring"]
  additional_features: ["KYC_verification", "fraud_detection"]

healthcare:
  compliance_requirements: ["HIPAA", "GDPR_health_data", "FDA_if_applicable"]
  security_enhancements: ["patient_data_encryption", "access_audit_trails"]
  additional_features: ["patient_privacy_controls", "consent_management"]

education:
  compliance_requirements: ["COPPA", "FERPA", "accessibility_standards"]
  security_enhancements: ["student_data_protection", "parental_controls"]
  additional_features: ["learning_analytics", "progress_tracking"]

# Additional industries: real_estate, legal, entertainment, etc.
```

### **Tech Stack Integration: {PRIMARY_TECH_STACK}**
```yaml
# Platform-specific adaptations:
wix_platform:
  integration_patterns: "wix-integration-patterns.yaml"
  component_templates: "wix-custom-elements"
  file_extensions: ".js"
  special_requirements: ["shadow_dom_patterns", "wix_data_integration"]

react_web:
  integration_patterns: "web-app-patterns.yaml"
  component_templates: "react-components"
  file_extensions: ".jsx"
  special_requirements: ["state_management", "routing", "responsive_design"]

react_native:
  integration_patterns: "mobile-app-patterns.yaml"
  component_templates: "react-native-components"
  file_extensions: ".tsx"
  special_requirements: ["platform_specific_code", "app_store_compliance"]
```

### **Brand Personality Implementation: {BRAND_ARCHETYPE}**
```yaml
# Brand personality encoded into all files:
motivational_friend: # Like "You got this" personality
  tone_rules: ["encouraging", "supportive", "confidence_building"]
  language_patterns: ["action_oriented", "capability_focused", "empowering"]
  ui_personality: ["bold_colors", "confident_typography", "momentum_focused"]

professional_expert:
  tone_rules: ["authoritative", "knowledgeable", "trustworthy"]
  language_patterns: ["precise", "technical", "credible"]
  ui_personality: ["clean_design", "professional_colors", "structured_layout"]

innovative_disruptor:
  tone_rules: ["bold", "challenging", "forward_thinking"]
  language_patterns: ["breakthrough", "revolutionary", "cutting_edge"]
  ui_personality: ["edgy_design", "vibrant_colors", "dynamic_interactions"]
```

---

## 🚀 Claude Code Execution Instructions

### **Phase 1: Repository Setup**
1. Create folder structure exactly as specified above
2. Generate all files with startup-specific content populated
3. Validate all YAML files against schemas in 04-schemas/
4. Verify all cross-references resolve correctly

### **Phase 2: Content Population**
1. Replace all `{PLACEHOLDER}` values with startup-specific content
2. Adapt business logic based on {BUSINESS_MODEL_TYPE}
3. Include industry-specific requirements based on {INDUSTRY_VERTICAL}
4. Implement brand personality consistently across all files

### **Phase 3: Validation & Quality Assurance**
1. Schema validation for all structured files
2. Cross-reference integrity checking
3. Brand consistency validation
4. Business model coherence verification
5. Technical feasibility assessment

### **Phase 4: Code Generation Ready**
1. All templates populated and ready for code generation
2. All workflows defined for implementation
3. All testing frameworks prepared
4. All deployment strategies configured

---

## ✅ Success Criteria

**Repository Generation Complete When:**
- [ ] All 10 folders created with correct structure
- [ ] All files populated with {STARTUP_NAME}-specific content
- [ ] All YAML files validate against schemas
- [ ] All cross-references resolve correctly
- [ ] Brand personality consistently implemented
- [ ] Business model logic coherent throughout
- [ ] Technical specifications are implementable
- [ ] All placeholders replaced with actual content

**Ready for Claude Code Development When:**
- [ ] All templates are code-generation ready
- [ ] All workflows are execution ready
- [ ] All tests are validation ready
- [ ] All deployment configs are launch ready

---

This setup file template generates a complete, startup-specific repository that Claude Code can autonomously process to build the entire application.