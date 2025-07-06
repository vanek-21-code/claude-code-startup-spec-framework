# Business Model Generator Module

This module generates comprehensive business model specifications for any startup, outputting structured YAML files that integrate with the universal repository structure (00-10 folders).

## 🎯 Output Files Generated

```yaml
# Primary Output Location: 01-foundation/
business-model.yaml                    # Core business model specification

# Secondary Output Locations:
07-business-rules/pricing-algorithms.yaml       # Revenue calculation logic
07-business-rules/subscription-management.yaml  # Billing & subscription rules
```

---

## 📋 Generation Framework

### **Input Analysis Pipeline**
```yaml
startup_input_analysis:
  business_idea_parsing:
    - extract_core_value_proposition
    - identify_target_market_segments
    - analyze_problem_solution_fit
    - determine_market_opportunity_size
  
  revenue_model_detection:
    - identify_primary_revenue_streams
    - analyze_pricing_strategy_signals
    - detect_monetization_patterns
    - assess_market_willingness_to_pay
  
  competitive_landscape_analysis:
    - identify_direct_competitors
    - analyze_indirect_competitors
    - assess_market_positioning_opportunities
    - determine_differentiation_strategies
```

### **Business Model Pattern Matching**
```yaml
business_model_patterns:
  saas_subscription:
    revenue_streams: ["monthly_subscription", "annual_subscription", "usage_based"]
    pricing_models: ["freemium", "tiered_pricing", "usage_based", "per_seat"]
    customer_acquisition: ["content_marketing", "free_trial", "product_led_growth"]
    key_metrics: ["mrr", "arr", "churn_rate", "ltv_cac_ratio", "expansion_revenue"]
    
  marketplace_commission:
    revenue_streams: ["transaction_commission", "listing_fees", "premium_features"]
    pricing_models: ["percentage_commission", "flat_fee", "subscription_plus_commission"]
    customer_acquisition: ["supply_side_first", "demand_side_first", "simultaneous"]
    key_metrics: ["gmv", "take_rate", "active_buyers", "active_sellers", "repeat_rate"]
    
  creator_economy_platform:
    revenue_streams: ["creator_revenue_share", "fan_subscriptions", "tool_monetization"]
    pricing_models: ["revenue_sharing", "platform_fee", "premium_tools"]
    customer_acquisition: ["creator_first", "audience_first", "viral_growth"]
    key_metrics: ["creator_earnings", "fan_engagement", "content_creation_rate"]
    
  e_commerce_direct:
    revenue_streams: ["product_sales", "shipping_fees", "premium_services"]
    pricing_models: ["cost_plus_margin", "competitive_pricing", "value_based"]
    customer_acquisition: ["paid_advertising", "seo", "social_commerce"]
    key_metrics: ["revenue", "gross_margin", "customer_acquisition_cost", "repeat_purchase_rate"]
    
  ai_powered_service:
    revenue_streams: ["api_usage", "subscription_tiers", "enterprise_licenses"]
    pricing_models: ["token_based", "request_based", "monthly_limits"]
    customer_acquisition: ["developer_evangelism", "api_marketplace", "integration_partnerships"]
    key_metrics: ["api_calls", "token_usage", "developer_adoption", "enterprise_conversion"]
```

### **Revenue Model Generation Algorithm**
```yaml
revenue_optimization_engine:
  primary_revenue_stream_selection:
    criteria:
      - market_size_potential
      - competition_intensity
      - customer_willingness_to_pay
      - implementation_complexity
      - time_to_revenue
    
  pricing_strategy_optimization:
    freemium_analysis:
      - calculate_free_to_paid_conversion_rates
      - optimize_feature_gating_strategy
      - determine_usage_limit_thresholds
    
    subscription_tier_optimization:
      - analyze_feature_value_perception
      - calculate_optimal_price_points
      - design_upgrade_path_strategy
    
    usage_based_pricing:
      - determine_usage_unit_metrics
      - calculate_marginal_cost_structure
      - optimize_pricing_per_unit
  
  monetization_timeline_planning:
    mvp_phase:
      - focus_on_user_validation
      - minimal_viable_monetization
      - data_collection_for_optimization
    
    growth_phase:
      - optimize_conversion_funnels
      - expand_revenue_streams
      - implement_advanced_pricing
    
    scale_phase:
      - enterprise_tier_introduction
      - platform_monetization_expansion
      - strategic_partnership_revenue
```

---

## 🏗️ 01-foundation/business-model.yaml Structure

```yaml
# Generated Business Model Specification
business_model:
  metadata:
    generated_date: "{CURRENT_DATE}"
    startup_name: "{STARTUP_NAME}"
    business_type: "{DETECTED_BUSINESS_TYPE}"
    market_category: "{PRIMARY_MARKET_CATEGORY}"
    
  core_value_proposition:
    primary_value: "{AI_GENERATED_VALUE_PROP}"
    target_problem: "{IDENTIFIED_PROBLEM}"
    solution_approach: "{SOLUTION_METHODOLOGY}"
    unique_differentiation: ["{DIFF_1}", "{DIFF_2}", "{DIFF_3}"]
    
  target_market:
    primary_segment:
      description: "{PRIMARY_CUSTOMER_SEGMENT}"
      size_estimate: "{MARKET_SIZE_ESTIMATE}"
      demographics: ["{DEMO_1}", "{DEMO_2}"]
      psychographics: ["{PSYCHO_1}", "{PSYCHO_2}"]
      pain_points: ["{PAIN_1}", "{PAIN_2}", "{PAIN_3}"]
      
    secondary_segments:
      - description: "{SECONDARY_SEGMENT_1}"
        opportunity_size: "{OPPORTUNITY_SIZE}"
        entry_strategy: "{ENTRY_APPROACH}"
    
  revenue_model:
    primary_streams:
      - stream_name: "{PRIMARY_REVENUE_STREAM}"
        description: "{STREAM_DESCRIPTION}"
        pricing_model: "{PRICING_MODEL}"
        revenue_percentage: "{PERCENTAGE_OF_TOTAL}"
        implementation_priority: "P0"
        
    secondary_streams:
      - stream_name: "{SECONDARY_REVENUE_STREAM}"
        description: "{STREAM_DESCRIPTION}"
        pricing_model: "{PRICING_MODEL}"
        revenue_percentage: "{PERCENTAGE_OF_TOTAL}"
        implementation_priority: "P1"
        
  pricing_strategy:
    model_type: "{PRICING_MODEL_TYPE}"
    price_points:
      tier_1:
        name: "{TIER_1_NAME}"
        price: "{TIER_1_PRICE}"
        features: ["{FEATURE_1}", "{FEATURE_2}"]
        target_segment: "{TARGET_SEGMENT}"
        
      tier_2:
        name: "{TIER_2_NAME}"
        price: "{TIER_2_PRICE}"
        features: ["{FEATURE_1}", "{FEATURE_2}", "{FEATURE_3}"]
        target_segment: "{TARGET_SEGMENT}"
        
    pricing_optimization:
      testing_strategy: "{A_B_TESTING_APPROACH}"
      price_elasticity_monitoring: "{MONITORING_APPROACH}"
      competitive_pricing_tracking: "{TRACKING_METHOD}"
      
  customer_acquisition:
    primary_channels:
      - channel: "{PRIMARY_CHANNEL}"
        cost_estimate: "{CAC_ESTIMATE}"
        conversion_rate: "{CONVERSION_ESTIMATE}"
        scalability: "{SCALABILITY_RATING}"
        
    growth_strategy:
      viral_coefficient_target: "{VIRAL_K_FACTOR}"
      retention_rate_target: "{RETENTION_TARGET}"
      expansion_revenue_strategy: "{EXPANSION_APPROACH}"
      
  unit_economics:
    customer_metrics:
      customer_acquisition_cost: "{CAC_ESTIMATE}"
      customer_lifetime_value: "{LTV_ESTIMATE}"
      ltv_cac_ratio: "{RATIO_CALCULATION}"
      payback_period: "{PAYBACK_MONTHS}"
      
    revenue_metrics:
      average_revenue_per_user: "{ARPU_ESTIMATE}"
      gross_margin_percentage: "{GROSS_MARGIN}"
      contribution_margin: "{CONTRIBUTION_MARGIN}"
      
  financial_projections:
    year_1:
      revenue_target: "{Y1_REVENUE}"
      user_acquisition_target: "{Y1_USERS}"
      burn_rate_estimate: "{Y1_BURN_RATE}"
      
    year_2:
      revenue_target: "{Y2_REVENUE}"
      user_acquisition_target: "{Y2_USERS}"
      profitability_timeline: "{PROFITABILITY_MONTH}"
      
    year_3:
      revenue_target: "{Y3_REVENUE}"
      market_share_target: "{MARKET_SHARE_PERCENTAGE}"
      expansion_opportunities: ["{EXPANSION_1}", "{EXPANSION_2}"]
      
  competitive_positioning:
    direct_competitors:
      - name: "{COMPETITOR_1}"
        strength: "{COMPETITOR_STRENGTH}"
        weakness: "{COMPETITOR_WEAKNESS}"
        differentiation_strategy: "{OUR_ADVANTAGE}"
        
    indirect_competitors:
      - category: "{INDIRECT_CATEGORY}"
        threat_level: "{THREAT_ASSESSMENT}"
        mitigation_strategy: "{MITIGATION_APPROACH}"
        
  risk_assessment:
    market_risks:
      - risk: "{MARKET_RISK_1}"
        probability: "{RISK_PROBABILITY}"
        impact: "{RISK_IMPACT}"
        mitigation: "{MITIGATION_STRATEGY}"
        
    business_model_risks:
      - risk: "{BM_RISK_1}"
        probability: "{RISK_PROBABILITY}"
        impact: "{RISK_IMPACT}"
        mitigation: "{MITIGATION_STRATEGY}"
        
  success_metrics:
    primary_kpis:
      - metric: "{PRIMARY_KPI_1}"
        target: "{TARGET_VALUE}"
        measurement_frequency: "{MEASUREMENT_CADENCE}"
        
    secondary_kpis:
      - metric: "{SECONDARY_KPI_1}"
        target: "{TARGET_VALUE}"
        measurement_frequency: "{MEASUREMENT_CADENCE}"
        
  validation_framework:
    mvp_validation_metrics:
      - hypothesis: "{HYPOTHESIS_1}"
        success_criteria: "{SUCCESS_CRITERIA}"
        measurement_method: "{MEASUREMENT_APPROACH}"
        
    market_validation_approach:
      customer_discovery_plan: "{DISCOVERY_METHODOLOGY}"
      prototype_testing_strategy: "{TESTING_APPROACH}"
      market_feedback_collection: "{FEEDBACK_MECHANISM}"
```

---

## 🔧 07-business-rules/pricing-algorithms.yaml Structure

```yaml
# Generated Pricing Logic Implementation
pricing_algorithms:
  metadata:
    business_model_reference: "01-foundation/business-model.yaml"
    last_updated: "{CURRENT_DATE}"
    algorithm_version: "1.0"
    
  subscription_pricing:
    tier_calculation:
      free_tier:
        features_included: ["{FREE_FEATURE_1}", "{FREE_FEATURE_2}"]
        usage_limits: 
          monthly_requests: "{FREE_LIMIT}"
          storage_limit: "{STORAGE_LIMIT}"
        upgrade_triggers: ["{TRIGGER_1}", "{TRIGGER_2}"]
        
      paid_tiers:
        basic:
          monthly_price: "{BASIC_PRICE}"
          features_included: ["{BASIC_FEATURE_1}", "{BASIC_FEATURE_2}"]
          usage_limits:
            monthly_requests: "{BASIC_LIMIT}"
            storage_limit: "{BASIC_STORAGE}"
          value_proposition: "{BASIC_VALUE_PROP}"
          
        premium:
          monthly_price: "{PREMIUM_PRICE}"
          features_included: ["{PREMIUM_FEATURE_1}", "{PREMIUM_FEATURE_2}"]
          usage_limits:
            monthly_requests: "{PREMIUM_LIMIT}"
            storage_limit: "{PREMIUM_STORAGE}"
          value_proposition: "{PREMIUM_VALUE_PROP}"
          
        enterprise:
          pricing_model: "custom_negotiated"
          base_price: "{ENTERPRISE_BASE}"
          custom_features: ["{ENTERPRISE_FEATURE_1}", "{ENTERPRISE_FEATURE_2}"]
          volume_discounts:
            tier_1: "10_percent_off_100_plus_users"
            tier_2: "20_percent_off_500_plus_users"
            tier_3: "custom_negotiation_1000_plus_users"
            
  usage_based_pricing:
    unit_calculation:
      primary_unit: "{USAGE_UNIT_TYPE}"
      cost_per_unit: "{COST_PER_UNIT}"
      volume_discounts:
        tier_1:
          threshold: "{VOLUME_THRESHOLD_1}"
          discount_percentage: "{DISCOUNT_1}"
        tier_2:
          threshold: "{VOLUME_THRESHOLD_2}"
          discount_percentage: "{DISCOUNT_2}"
          
    billing_logic:
      measurement_period: "monthly"
      overage_charges: "automatic"
      credit_rollover: "{ROLLOVER_POLICY}"
      
  dynamic_pricing:
    market_demand_adjustments:
      peak_demand_multiplier: "{PEAK_MULTIPLIER}"
      off_peak_discount: "{OFF_PEAK_DISCOUNT}"
      seasonal_adjustments: ["{SEASONAL_1}", "{SEASONAL_2}"]
      
    competitive_pricing_responses:
      price_matching_triggers: ["{TRIGGER_1}", "{TRIGGER_2}"]
      maximum_discount_allowed: "{MAX_DISCOUNT}"
      minimum_margin_protection: "{MIN_MARGIN}"
      
  revenue_optimization:
    upselling_logic:
      usage_threshold_alerts: ["{THRESHOLD_1}", "{THRESHOLD_2}"]
      feature_upgrade_suggestions: ["{SUGGESTION_1}", "{SUGGESTION_2}"]
      timing_optimization: "{OPTIMAL_TIMING}"
      
    churn_prevention_pricing:
      retention_discounts: ["{DISCOUNT_1}", "{DISCOUNT_2}"]
      win_back_offers: ["{OFFER_1}", "{OFFER_2}"]
      loyalty_program_integration: "{LOYALTY_STRUCTURE}"
      
  compliance_and_taxation:
    regional_pricing_adjustments:
      currency_conversion_logic: "{CONVERSION_APPROACH}"
      local_tax_calculation: "{TAX_CALCULATION_METHOD}"
      regulatory_compliance: ["{REGULATION_1}", "{REGULATION_2}"]
      
    pricing_transparency:
      display_rules: ["{DISPLAY_RULE_1}", "{DISPLAY_RULE_2}"]
      change_notification_requirements: "{NOTIFICATION_POLICY}"
      refund_policy_integration: "{REFUND_POLICY}"
```

---

## 🎯 Generation Logic for Different Business Models

### **SaaS/Subscription Focused**
```yaml
generation_rules:
  emphasis_areas:
    - subscription_tier_optimization
    - churn_prevention_strategies
    - expansion_revenue_planning
    - customer_success_integration
    
  pricing_model_priority:
    - freemium_with_premium_tiers
    - usage_based_hybrid
    - enterprise_custom_pricing
    
  key_metrics_focus:
    - monthly_recurring_revenue
    - customer_acquisition_cost
    - customer_lifetime_value
    - net_revenue_retention
```

### **Marketplace/Platform Focused**
```yaml
generation_rules:
  emphasis_areas:
    - two_sided_market_dynamics
    - commission_optimization
    - network_effects_monetization
    - platform_fee_structures
    
  pricing_model_priority:
    - commission_based_revenue
    - listing_fee_strategies
    - premium_service_monetization
    
  key_metrics_focus:
    - gross_merchandise_value
    - take_rate_optimization
    - active_buyer_seller_ratio
    - marketplace_liquidity
```

### **Creator Economy Focused**
```yaml
generation_rules:
  emphasis_areas:
    - creator_revenue_sharing
    - audience_monetization
    - platform_value_creation
    - creator_retention_strategies
    
  pricing_model_priority:
    - revenue_sharing_models
    - fan_subscription_systems
    - tool_monetization_strategies
    
  key_metrics_focus:
    - creator_earnings_growth
    - fan_engagement_rates
    - content_creation_velocity
    - platform_stickiness
```

### **AI/Technology Service Focused**
```yaml
generation_rules:
  emphasis_areas:
    - api_usage_monetization
    - computational_cost_optimization
    - enterprise_licensing_strategies
    - developer_ecosystem_building
    
  pricing_model_priority:
    - token_based_pricing
    - request_volume_pricing
    - enterprise_seat_licensing
    
  key_metrics_focus:
    - api_call_volume
    - developer_adoption_rate
    - enterprise_conversion_rate
    - computational_efficiency
```

---

## 🔄 Cross-Reference Integration

### **Dependencies from Other Modules**
```yaml
required_inputs:
  from_persona_generator: "01-foundation/user-personas.yaml"
  from_tech_architecture: "02-architecture/tech-stack.yaml" 
  from_feature_generator: "03-features/F*.yaml"
  
integration_points:
  user_personas: "Pricing aligned with persona willingness-to-pay"
  tech_stack: "Pricing model supports technical architecture"
  features: "Feature value drives pricing tier differentiation"
```

### **Outputs Referenced By**
```yaml
referenced_by:
  feature_specifications: "Feature pricing and monetization logic"
  testing_frameworks: "Revenue and pricing validation tests"
  deployment_strategy: "Billing system implementation requirements"
  brand_personality: "Pricing communication and positioning"
```

---

## 📋 Claude Code Processing Instructions

### **Processing Sequence**
1. **Analyze startup input** for business model signals
2. **Generate business-model.yaml** in 01-foundation/
3. **Generate pricing-algorithms.yaml** in 07-business-rules/
4. **Validate against schemas** in 04-schemas/
5. **Cross-reference integration** with other generated files

### **Quality Validation**
- **Schema compliance**: Validate against business-model.schema.json
- **Internal consistency**: Pricing aligns with revenue model
- **Market feasibility**: Pricing competitive in target market
- **Financial viability**: Unit economics support business sustainability

### **Output Optimization**
- **Claude Code readable**: YAML structure optimized for AI processing
- **Human reviewable**: Clear section organization and naming
- **Implementation ready**: Detailed enough for development team execution
- **Iteration friendly**: Easy to update and refine based on market feedback

This business model generator creates comprehensive, implementation-ready business specifications that integrate seamlessly with the universal repository structure while adapting to any startup type or industry.