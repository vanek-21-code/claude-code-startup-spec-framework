# Persona Generator Module

Universal user persona generation system that creates detailed, behavioral user profiles for any startup idea. Outputs structured YAML files for Claude Code processing.

## 🎯 Purpose

Generates comprehensive user personas that drive feature development, business logic, and user experience decisions across all startup types.

## 📁 Output Specifications

**Output Location**: `01-foundation/user-personas.yaml`
**Schema Validation**: `04-schemas/user-story.schema.json`
**File Format**: Structured YAML with behavioral specifications
**Processing Order**: Generated after business-model.yaml, before features

## 🧠 Persona Generation Framework

### **Universal Persona Structure**
```yaml
# Standard persona format for any startup type
personas:
  primary_persona:
    id: "P001"
    name: "{persona_name}"
    type: "{primary|secondary|tertiary}"
    role: "{user_role_in_business_model}"
    
  demographic_profile:
    age_range: "{age_range}"
    income_level: "{income_bracket}"
    education: "{education_level}"
    location: "{geographic_target}"
    tech_savviness: "{low|medium|high}"
    
  psychographic_profile:
    personality_traits: ["{trait1}", "{trait2}", "{trait3}"]
    values: ["{value1}", "{value2}", "{value3}"]
    lifestyle: "{lifestyle_description}"
    pain_points: ["{pain1}", "{pain2}", "{pain3}"]
    motivations: ["{motivation1}", "{motivation2}", "{motivation3}"]
    
  behavioral_patterns:
    digital_behavior:
      preferred_devices: ["{device1}", "{device2}"]
      app_usage_patterns: "{usage_description}"
      communication_preferences: ["{channel1}", "{channel2}"]
      
    decision_making:
      research_depth: "{low|medium|high}"
      price_sensitivity: "{low|medium|high}"
      brand_loyalty: "{low|medium|high}"
      influence_factors: ["{factor1}", "{factor2}", "{factor3}"]
      
    engagement_patterns:
      frequency_of_use: "{daily|weekly|monthly|occasional}"
      session_duration: "{short|medium|long}"
      preferred_interaction_style: "{self_service|guided|collaborative}"
      
  business_context:
    relationship_to_product: "{how_they_use_product}"
    value_they_seek: "{primary_value_proposition}"
    willingness_to_pay: "{price_range_or_model}"
    referral_likelihood: "{low|medium|high}"
    
  behavioral_specifications:
    user_stories:
      - actor: "{persona_name}"
        action: "{primary_action}"
        goal: "{desired_outcome}"
        constraints: 
          time_limit: "{time_constraint}"
          skill_requirement: "{skill_level}"
          resource_requirement: "{resource_needs}"
        success_criteria:
          - "{success_measure_1}"
          - "{success_measure_2}"
          
    usage_scenarios:
      primary_scenario:
        when: "{trigger_condition}"
        context: "{usage_context}"
        expected_behavior: "{behavior_description}"
        success_outcome: "{desired_result}"
        
    interaction_preferences:
      ui_complexity: "{simple|moderate|complex}"
      information_density: "{minimal|balanced|rich}"
      guidance_level: "{self_directed|some_help|hand_holding}"
```

## 🔄 Business Model Adaptation Rules

### **SaaS Products**
```yaml
persona_adaptations:
  saas:
    roles: ["end_user", "decision_maker", "administrator"]
    focus_areas: ["productivity", "efficiency", "cost_savings"]
    behavioral_patterns:
      trial_behavior: "evaluation_focused"
      adoption_pattern: "gradual_rollout"
      retention_drivers: ["roi_demonstration", "ease_of_use"]
```

### **Marketplace Platforms**
```yaml
persona_adaptations:
  marketplace:
    roles: ["supplier", "buyer", "facilitator"]
    focus_areas: ["transaction_efficiency", "trust_building", "discovery"]
    behavioral_patterns:
      supplier_behavior: "revenue_optimization"
      buyer_behavior: "value_seeking"
      platform_interaction: "minimal_friction"
```

### **E-commerce**
```yaml
persona_adaptations:
  ecommerce:
    roles: ["shopper", "gift_buyer", "repeat_customer"]
    focus_areas: ["product_discovery", "purchase_confidence", "convenience"]
    behavioral_patterns:
      shopping_behavior: "research_then_buy"
      loyalty_drivers: ["quality", "service", "price"]
      mobile_usage: "high_mobile_preference"
```

### **Creator Economy Platforms**
```yaml
persona_adaptations:
  creator_platform:
    roles: ["creator", "audience", "collaborator"]
    focus_areas: ["monetization", "audience_growth", "content_creation"]
    behavioral_patterns:
      creator_behavior: "growth_and_revenue_focused"
      audience_behavior: "value_and_entertainment_seeking"
      engagement_pattern: "community_driven"
```

### **AI-Powered Tools**
```yaml
persona_adaptations:
  ai_tools:
    roles: ["power_user", "casual_user", "integrator"]
    focus_areas: ["automation", "enhancement", "learning"]
    behavioral_patterns:
      ai_comfort: "varies_by_persona"
      learning_curve: "expects_immediate_value"
      trust_building: "requires_transparency"
```

## 🎯 Industry-Specific Adaptations

### **Fintech**
```yaml
industry_adaptations:
  fintech:
    additional_attributes:
      financial_sophistication: "{novice|intermediate|expert}"
      risk_tolerance: "{conservative|moderate|aggressive}"
      regulatory_awareness: "{low|medium|high}"
    behavioral_considerations:
      security_concerns: "extremely_high"
      compliance_expectations: "strict_adherence"
      trust_requirements: "institutional_level"
```

### **Healthcare**
```yaml
industry_adaptations:
  healthcare:
    additional_attributes:
      health_literacy: "{low|medium|high}"
      technology_adoption: "{early|mainstream|late}"
      privacy_sensitivity: "{standard|high|extreme}"
    behavioral_considerations:
      data_sharing: "highly_cautious"
      professional_validation: "required"
      accessibility_needs: "critical_consideration"
```

### **Education**
```yaml
industry_adaptations:
  education:
    additional_attributes:
      learning_style: "{visual|auditory|kinesthetic|reading}"
      motivation_type: "{intrinsic|extrinsic|mixed}"
      technology_integration: "{digital_native|digital_immigrant}"
    behavioral_considerations:
      engagement_patterns: "varied_attention_spans"
      progress_tracking: "motivation_driver"
      social_learning: "important_component"
```

## 📊 Persona Prioritization Framework

### **Primary Persona Selection**
```yaml
prioritization_criteria:
  business_impact:
    revenue_potential: "weight: 40%"
    market_size: "weight: 30%"
    acquisition_cost: "weight: 30%"
    
  product_fit:
    problem_intensity: "weight: 50%"
    solution_alignment: "weight: 30%"
    differentiation_opportunity: "weight: 20%"
    
  execution_feasibility:
    accessibility: "weight: 40%"
    development_complexity: "weight: 30%"
    go_to_market_efficiency: "weight: 30%"
```

### **Multi-Persona Relationships**
```yaml
persona_interactions:
  influencer_relationships:
    - persona: "P001"
      influences: ["P002", "P003"]
      influence_type: "decision_making"
      
  workflow_dependencies:
    - primary_user: "P001"
      dependent_users: ["P002"]
      dependency_type: "output_consumption"
      
  conflict_resolution:
    - conflicting_personas: ["P001", "P002"]
      conflict_area: "feature_priority"
      resolution_strategy: "segmented_experience"
```

## 🎨 Brand Personality Integration

### **Persona-Brand Alignment**
```yaml
brand_integration:
  personality_mapping:
    confident_brand:
      persona_adaptation: "emphasize_capability_and_achievement"
      language_patterns: "empowering_and_action_oriented"
      interaction_design: "streamlined_and_decisive"
      
    friendly_brand:
      persona_adaptation: "emphasize_community_and_support"
      language_patterns: "warm_and_approachable"
      interaction_design: "guided_and_encouraging"
      
    innovative_brand:
      persona_adaptation: "emphasize_creativity_and_growth"
      language_patterns: "forward_thinking_and_inspiring"
      interaction_design: "cutting_edge_and_experimental"
```

## 🔧 Technical Implementation Specifications

### **Data Structure Requirements**
```yaml
technical_specs:
  persona_data_model:
    primary_key: "persona_id"
    required_fields: ["name", "type", "role", "behavioral_patterns"]
    optional_fields: ["demographic_profile", "psychographic_profile"]
    validation_rules: "schema_compliant"
    
  integration_points:
    features: "persona_id referenced in user stories"
    business_rules: "persona_behavior drives rule logic"
    testing: "persona_scenarios drive test cases"
    brand: "persona_alignment validates brand consistency"
```

### **Validation Framework**
```yaml
validation_rules:
  completeness_check:
    - "all_primary_personas_have_behavioral_specifications"
    - "user_stories_cover_all_primary_use_cases"
    - "personas_align_with_business_model"
    
  consistency_validation:
    - "demographic_data_matches_target_market"
    - "behavioral_patterns_support_business_goals"
    - "pain_points_align_with_value_proposition"
    
  business_alignment:
    - "personas_support_revenue_model"
    - "user_journey_enables_monetization"
    - "persona_priorities_match_feature_roadmap"
```

## 🚀 Claude Code Processing Instructions

### **Generation Workflow**
```yaml
processing_steps:
  1_data_collection:
    input_source: "01-foundation/business-model.yaml"
    required_data: ["target_market", "value_proposition", "user_roles"]
    
  2_persona_generation:
    framework_application: "business_model_adaptation_rules"
    output_generation: "structured_persona_profiles"
    
  3_behavioral_specification:
    user_story_creation: "actor_action_constraint_format"
    scenario_development: "usage_context_mapping"
    
  4_validation:
    schema_compliance: "04-schemas/user-story.schema.json"
    business_alignment: "cross_reference_business_model"
    
  5_integration_preparation:
    feature_mapping: "persona_to_feature_requirements"
    testing_scenario_creation: "persona_driven_test_cases"
```

### **Quality Assurance Checkpoints**
```yaml
qa_framework:
  persona_quality:
    - "personas_are_specific_and_actionable"
    - "behavioral_patterns_are_realistic"
    - "pain_points_are_addressable_by_solution"
    
  business_relevance:
    - "personas_support_business_model"
    - "user_journey_enables_monetization"
    - "market_size_justifies_development_effort"
    
  technical_feasibility:
    - "behavioral_requirements_are_implementable"
    - "persona_data_structure_supports_features"
    - "integration_points_are_clearly_defined"
```

## 📈 Success Metrics & Validation

### **Persona Effectiveness Measurement**
```yaml
success_metrics:
  development_guidance:
    feature_prioritization: "personas_drive_clear_priorities"
    user_experience: "personas_inform_ux_decisions"
    business_logic: "personas_validate_rule_design"
    
  market_validation:
    user_research_alignment: "real_users_match_persona_profiles"
    product_market_fit: "persona_needs_met_by_product"
    acquisition_efficiency: "persona_targeting_improves_conversion"
```

This updated persona generator aligns with the 00-10 repository structure and generates YAML output that Claude Code can process autonomously while maintaining universal applicability across all startup types.