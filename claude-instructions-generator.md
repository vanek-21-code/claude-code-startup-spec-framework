# Claude Instructions Generator
## AI-Executable Repository Generation Instructions

This module generates the complete instruction set that Claude Code follows to autonomously create and populate startup specification repositories using the universal 00-10 folder structure.

---

## 🎯 Core Generation Principles

### **Sequential Processing Architecture**
Claude Code processes folders in strict numerical order (00→01→02...→10) with validation checkpoints between each phase.

### **Schema-Driven Validation**
Every generated file validates against corresponding schemas before proceeding to the next folder.

### **Cross-Reference Integrity**
All dependencies are mapped and validated to ensure no broken references.

---

## 📋 Universal Claude Code Instructions Template

```yaml
# claude-instructions.md (Generated for each startup)

startup_context:
  name: "{STARTUP_NAME}"
  business_model: "{BUSINESS_MODEL_TYPE}"
  tech_stack: "{TECHNOLOGY_STACK}"
  target_users: ["{USER_PERSONAS}"]
  brand_personality: "{BRAND_ARCHETYPE}"
  complexity_level: "{MVP|GROWTH|ENTERPRISE}"

processing_sequence:
  
  # PHASE 0: Meta Setup & Validation
  phase_0_meta:
    folder: "00-meta/"
    priority: "CRITICAL"
    dependencies: []
    instructions:
      - generate_readme_with_project_overview
      - create_processing_order_validation_rules
      - build_cross_reference_dependency_map
      - establish_claude_code_execution_checkpoints
    validation_checkpoints:
      - "All meta files validate against universal schemas"
      - "Processing order rules are logically consistent"
      - "Cross-reference map covers all planned dependencies"
    error_handling:
      - "FATAL: Cannot proceed without valid meta setup"
      - "Regenerate entire meta folder on validation failure"

  # PHASE 1: Business Foundation
  phase_1_foundation:
    folder: "01-foundation/"
    priority: "CRITICAL"
    dependencies: ["00-meta/"]
    instructions:
      - populate_product_vision_from_business_context
      - generate_business_model_with_revenue_calculations
      - create_user_personas_based_on_target_market
      - define_success_metrics_aligned_with_business_model
      - analyze_competitive_landscape_for_positioning
      - establish_market_positioning_strategy
    validation_checkpoints:
      - "Business model aligns with startup context"
      - "User personas match business model requirements"
      - "Success metrics are measurable and realistic"
      - "All foundation files validate against schemas"
    cross_references:
      - "business-model.yaml metrics → success-metrics.yaml KPIs"
      - "user-personas.yaml needs → competitive-analysis.yaml gaps"
    error_handling:
      - "WARNING: Misaligned business model requires regeneration"
      - "RETRY: Invalid personas need context refinement"

  # PHASE 2: Technical Architecture
  phase_2_architecture:
    folder: "02-architecture/"
    priority: "CRITICAL"
    dependencies: ["01-foundation/"]
    instructions:
      - select_optimal_tech_stack_for_business_requirements
      - generate_platform_integration_patterns_for_chosen_stack
      - configure_ai_model_specifications_if_ai_powered
      - define_performance_requirements_based_on_user_expectations
      - establish_security_compliance_for_target_market
      - design_scalability_architecture_for_growth_projections
      - map_data_flow_architecture_for_feature_requirements
      - specify_infrastructure_requirements_for_deployment
    validation_checkpoints:
      - "Tech stack supports all planned features"
      - "Performance requirements are technically achievable"
      - "Security compliance meets industry standards"
      - "Scalability plan supports business growth projections"
    cross_references:
      - "tech-stack.yaml capabilities → 03-features/ requirements"
      - "performance-requirements.yaml → 09-testing/performance-benchmarks.yaml"
      - "security-compliance.yaml → 07-business-rules/compliance-requirements.yaml"
    error_handling:
      - "ERROR: Tech stack insufficient for feature requirements"
      - "ESCALATE: Security requirements exceed tech stack capabilities"

  # PHASE 3: Schema Foundation (Before Features)
  phase_3_schemas:
    folder: "04-schemas/"
    priority: "CRITICAL"
    dependencies: ["02-architecture/"]
    instructions:
      - generate_feature_specification_validation_schema
      - create_user_story_format_validation_schema
      - build_behavioral_specification_validation_schema
      - design_business_rule_validation_schema
      - establish_api_contract_validation_schema
      - create_ui_component_validation_schema
      - build_test_specification_validation_schema
      - generate_performance_benchmark_validation_schema
      - create_universal_validation_rules_schema
    validation_checkpoints:
      - "All schemas are valid JSON Schema format"
      - "Schemas cover all required validation scenarios"
      - "Schema relationships are properly defined"
    cross_references:
      - "All subsequent phases validate against these schemas"
    error_handling:
      - "FATAL: Invalid schemas break all subsequent validation"
      - "REGENERATE: Schema inconsistencies require full schema rebuild"

  # PHASE 4: Code Templates
  phase_4_templates:
    folder: "05-templates/"
    priority: "HIGH"
    dependencies: ["02-architecture/", "04-schemas/"]
    instructions:
      - generate_frontend_component_templates_for_tech_stack
      - create_backend_api_templates_matching_architecture
      - build_database_model_templates_for_data_requirements
      - generate_test_suite_templates_for_quality_framework
      - create_documentation_templates_for_maintenance
      - build_deployment_templates_for_infrastructure_plan
    validation_checkpoints:
      - "Templates match selected tech stack"
      - "Template patterns are consistent across categories"
      - "All templates include proper error handling"
    cross_references:
      - "frontend-components/ → 02-architecture/tech-stack.yaml"
      - "backend-api/ → 02-architecture/data-flow-architecture.yaml"
      - "test-suites/ → 09-testing/ specifications"
    error_handling:
      - "WARNING: Template mismatch with tech stack requires regeneration"

  # PHASE 5: Feature Specifications  
  phase_5_features:
    folder: "03-features/"
    priority: "CRITICAL"
    dependencies: ["01-foundation/", "02-architecture/", "04-schemas/", "05-templates/"]
    instructions:
      - generate_primary_business_feature_specification
      - create_user_management_and_authentication_features
      - build_core_user_interaction_features
      - design_data_management_and_storage_features
      - establish_discovery_and_search_capabilities
      - create_communication_and_engagement_features
      - implement_monetization_and_payment_features
      - build_analytics_and_reporting_capabilities
      - design_content_moderation_and_safety_features
      - create_notification_and_alert_systems
      - ensure_mobile_responsive_design_features
      - build_administrative_interface_features
      - design_third_party_integration_capabilities
      - plan_advanced_and_premium_features
    validation_checkpoints:
      - "Each feature validates against feature-specification.schema.json"
      - "All user stories follow user-story.schema.json format"
      - "Behavioral specs follow behavioral-spec.schema.json"
      - "Feature dependencies are properly mapped"
      - "All features align with business model requirements"
    cross_references:
      - "F001-{primary} → 01-foundation/business-model.yaml core_value"
      - "F007-{payments} → 07-business-rules/pricing-algorithms.yaml"
      - "All features → 05-templates/ for implementation patterns"
    error_handling:
      - "ERROR: Feature validation failure requires schema compliance"
      - "WARNING: Missing feature dependencies require generation"

  # PHASE 6: Business Rules Encoding
  phase_6_business_rules:
    folder: "07-business-rules/"
    priority: "HIGH"
    dependencies: ["03-features/", "01-foundation/"]
    instructions:
      - encode_pricing_algorithms_from_business_model
      - create_user_permission_matrix_for_feature_access
      - establish_content_moderation_rules_for_safety
      - design_workflow_automation_for_efficiency
      - implement_analytics_tracking_for_insights
      - create_subscription_management_for_billing
      - ensure_compliance_requirements_for_regulations
      - optimize_business_processes_for_performance
    validation_checkpoints:
      - "Business rules validate against business-rule.schema.json"
      - "Pricing algorithms match business model revenue streams"
      - "Permission matrix covers all feature access scenarios"
      - "Compliance rules meet industry standards"
    cross_references:
      - "pricing-algorithms.yaml → 01-foundation/business-model.yaml"
      - "user-permission-matrix.yaml → 03-features/ access_requirements"
      - "compliance-requirements.yaml → 02-architecture/security-compliance.yaml"
    error_handling:
      - "ERROR: Business rule conflicts require resolution"
      - "WARNING: Missing compliance rules require generation"

  # PHASE 7: Brand Implementation
  phase_7_brand:
    folder: "08-brand/"
    priority: "MEDIUM"
    dependencies: ["01-foundation/", "03-features/"]
    instructions:
      - encode_brand_personality_into_executable_rules
      - create_language_patterns_for_consistent_voice
      - establish_ui_personality_rules_for_visual_consistency
      - generate_copy_guidelines_for_content_creation
      - build_marketing_frameworks_for_growth
      - create_voice_tone_matrix_for_context_awareness
      - implement_brand_compliance_validation_system
    validation_checkpoints:
      - "Brand encoding matches specified personality archetype"
      - "Language patterns are consistent across all contexts"
      - "UI personality rules integrate with feature specifications"
    cross_references:
      - "personality-encoding.yaml → 03-features/ user_experience"
      - "ui-personality-rules.yaml → 05-templates/frontend-components/"
    error_handling:
      - "WARNING: Brand inconsistency requires alignment"

  # PHASE 8: Workflow Orchestration
  phase_8_workflows:
    folder: "06-workflows/"
    priority: "HIGH"
    dependencies: ["03-features/", "05-templates/", "04-schemas/"]
    instructions:
      - create_repository_generation_workflow
      - design_feature_implementation_workflow_using_templates
      - build_testing_automation_workflow_for_quality
      - establish_deployment_pipeline_for_releases
      - create_quality_assurance_workflow_for_validation
      - implement_dependency_management_for_coordination
      - design_version_control_workflow_for_maintenance
      - create_maintenance_procedures_for_operations
    validation_checkpoints:
      - "Workflows reference valid templates and schemas"
      - "Implementation workflows cover all feature types"
      - "Quality workflows ensure comprehensive validation"
    cross_references:
      - "feature-implementation.yaml → 05-templates/ + 03-features/"
      - "testing-automation.yaml → 09-testing/ specifications"
      - "deployment-pipeline.yaml → 10-deployment/ requirements"
    error_handling:
      - "ERROR: Workflow template references must be valid"

  # PHASE 9: Testing Framework
  phase_9_testing:
    folder: "09-testing/"
    priority: "HIGH"
    dependencies: ["03-features/", "02-architecture/", "08-brand/"]
    instructions:
      - create_acceptance_criteria_framework_for_features
      - establish_performance_benchmarks_from_architecture
      - build_security_validation_suite_for_protection
      - create_accessibility_testing_for_inclusion
      - implement_brand_compliance_testing_for_consistency
      - design_load_testing_specifications_for_scalability
      - establish_user_acceptance_testing_framework
      - create_automated_qa_workflows_for_efficiency
    validation_checkpoints:
      - "Testing specs validate against test-specification.schema.json"
      - "Performance benchmarks align with architecture requirements"
      - "Security tests cover all compliance requirements"
      - "Brand tests validate personality implementation"
    cross_references:
      - "performance-benchmarks.yaml → 02-architecture/performance-requirements.yaml"
      - "security-validation-suite.yaml → 07-business-rules/compliance-requirements.yaml"
      - "brand-compliance-testing.yaml → 08-brand/ validation rules"
    error_handling:
      - "WARNING: Missing test coverage requires additional specs"

  # PHASE 10: Deployment Strategy
  phase_10_deployment:
    folder: "10-deployment/"
    priority: "MEDIUM"
    dependencies: ["ALL_PREVIOUS_PHASES"]
    instructions:
      - create_mvp_implementation_roadmap_from_features
      - design_launch_strategy_for_market_entry
      - build_scaling_architecture_for_growth
      - establish_monitoring_alerting_for_operations
      - create_backup_disaster_recovery_for_protection
      - plan_post_launch_iteration_for_improvement
      - design_growth_strategy_for_expansion
      - establish_maintenance_operations_for_sustainability
    validation_checkpoints:
      - "Roadmap covers all MVP features in logical sequence"
      - "Launch strategy aligns with business model"
      - "Scaling plan supports projected growth"
      - "All deployment specs are technically feasible"
    cross_references:
      - "mvp-implementation-roadmap.yaml → 03-features/ priority matrix"
      - "scaling-architecture.yaml → 02-architecture/scalability-architecture.yaml"
      - "growth-strategy.yaml → 01-foundation/success-metrics.yaml"
    error_handling:
      - "WARNING: Unrealistic roadmap requires adjustment"

# OVERALL VALIDATION & QUALITY ASSURANCE
final_validation:
  cross_reference_integrity:
    - "Validate all cross-references resolve correctly"
    - "Ensure no circular dependencies exist"
    - "Verify all schema validations pass"
  
  business_model_alignment:
    - "All features support business model objectives"
    - "Pricing algorithms align with revenue strategy"
    - "User personas match feature specifications"
  
  technical_feasibility:
    - "Tech stack supports all feature requirements"
    - "Performance requirements are achievable"
    - "Security compliance is comprehensive"
  
  brand_consistency:
    - "All components reflect brand personality"
    - "Language patterns are consistent throughout"
    - "UI personality is properly encoded"

error_escalation:
  critical_errors:
    - "Stop processing and request human intervention"
    - "Log all validation failures with specific details"
    - "Provide recommendations for resolution"
  
  warning_resolution:
    - "Continue processing with noted warnings"
    - "Attempt automatic resolution where possible"
    - "Document all warnings for review"

completion_criteria:
  - "All 11 folders generated and populated"
  - "All files validate against schemas"
  - "All cross-references resolve correctly"
  - "Business model alignment verified"
  - "Technical feasibility confirmed"
  - "Brand consistency validated"
  - "Final repository passes all quality checks"
```

---

## 🎯 Quality Assurance Framework

### **Schema Validation Requirements**
```yaml
validation_rules:
  schema_compliance:
    - "Every YAML file MUST validate against corresponding schema"
    - "All JSON Schema files MUST be valid JSON Schema format"
    - "Cross-references MUST resolve to existing files"
  
  business_logic_validation:
    - "Pricing algorithms MUST match business model"
    - "User permissions MUST cover all feature access scenarios"
    - "Success metrics MUST be measurable and realistic"
  
  technical_validation:
    - "Tech stack MUST support all feature requirements"
    - "Performance requirements MUST be technically achievable"
    - "Security compliance MUST meet industry standards"
```

### **Error Handling Protocol**
```yaml
error_types:
  FATAL:
    description: "Cannot proceed without resolution"
    examples: ["Invalid schemas", "Missing critical dependencies"]
    action: "Stop processing, request human intervention"
  
  ERROR:
    description: "Significant issue requiring correction"
    examples: ["Feature validation failure", "Business rule conflicts"]
    action: "Attempt automatic resolution, escalate if failed"
  
  WARNING:
    description: "Minor issue that doesn't block processing"
    examples: ["Missing optional features", "Brand inconsistencies"]
    action: "Continue with notation, flag for review"
```

### **Success Criteria Checklist**
```yaml
completion_checklist:
  structure_generation:
    - "All 11 folders created with correct naming"
    - "All required files generated in correct locations"
    - "File naming follows established conventions"
  
  content_population:
    - "All YAML files contain valid structured data"
    - "All business context properly encoded"
    - "All technical specifications complete"
  
  validation_compliance:
    - "100% schema validation pass rate"
    - "All cross-references resolve correctly"
    - "No critical or error-level issues remaining"
  
  quality_assurance:
    - "Business model alignment verified"
    - "Technical feasibility confirmed"
    - "Brand consistency validated"
```

---

## 🚀 Adaptive Instruction Generation

### **Business Model Adaptations**
```yaml
saas_specific_instructions:
  - "Emphasize subscription management in business rules"
  - "Include SaaS-specific metrics in success criteria"
  - "Generate subscription billing templates"

marketplace_specific_instructions:
  - "Create two-sided user persona specifications"
  - "Include commission-based pricing algorithms"
  - "Generate seller/buyer workflow templates"

ai_powered_specific_instructions:
  - "Include detailed AI model specifications"
  - "Generate AI integration templates"
  - "Add AI-specific performance benchmarks"
```

### **Tech Stack Adaptations**
```yaml
wix_specific_instructions:
  - "Generate Shadow DOM custom element templates"
  - "Include Wix collection data flow patterns"
  - "Add Wix-specific deployment workflows"

react_native_specific_instructions:
  - "Generate React Native component templates"
  - "Include mobile-specific performance requirements"
  - "Add app store deployment workflows"
```

### **Complexity Level Adaptations**
```yaml
mvp_instructions:
  - "Focus on core features only"
  - "Simplify deployment and testing requirements"
  - "Prioritize speed to market over comprehensive features"

enterprise_instructions:
  - "Include comprehensive security and compliance"
  - "Generate enterprise-grade monitoring and alerting"
  - "Add complex scaling and disaster recovery plans"
```

---

This updated claude-instructions-generator.md provides complete, AI-executable instructions that align perfectly with the universal 00-10 repository structure and ensure consistent, high-quality startup specification generation.