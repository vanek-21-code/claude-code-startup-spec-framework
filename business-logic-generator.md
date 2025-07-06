# Business Logic Generator

Generates executable business rules and logic for any startup, outputting to the `07-business-rules/` folder in machine-readable YAML format.

## 🎯 Purpose

Transform startup business model and requirements into executable business logic that Claude Code can implement as working systems.

---

## 📁 Output Structure

```
07-business-rules/
├── pricing-algorithms.yaml                      # Revenue & pricing logic
├── user-permission-matrix.yaml                  # Access control rules
├── content-moderation-rules.yaml                # Safety & quality rules
├── workflow-automation.yaml                     # Business process automation
├── analytics-tracking.yaml                      # Data collection rules
├── subscription-management.yaml                 # Billing & subscription logic
├── compliance-requirements.yaml                 # Legal & regulatory rules
└── business-process-optimization.yaml           # Efficiency & optimization rules
```

---

## 🧠 Business Logic Generation Framework

### **Input Analysis**
```yaml
# Startup Context Analysis
business_model_type: [saas, marketplace, e_commerce, platform, service]
revenue_streams: [subscription, commission, transaction, advertising, freemium]
user_types: [creator, consumer, admin, enterprise, free_user]
industry_context: [fintech, healthcare, education, general]
complexity_level: [mvp, growth, enterprise]
compliance_requirements: [gdpr, hipaa, pci_dss, coppa, general]
```

### **Logic Generation Rules**
```yaml
# Rule Generation Matrix
when: "business_model == 'marketplace'"
then: "generate commission-based pricing rules"
and: "create two-sided user permission matrix"
unless: "revenue_model == 'subscription_only'"

when: "industry == 'fintech'"
then: "add enhanced security rules"
and: "include financial compliance requirements"
and: "implement fraud detection workflows"

when: "complexity_level == 'enterprise'"
then: "add advanced analytics tracking"
and: "implement role-based permissions"
and: "include audit trail requirements"
```

---

## 💰 Pricing Algorithms Generator

### **Revenue Model Patterns**
```yaml
# Subscription-Based Pricing
subscription_pricing:
  algorithm_type: "tiered_subscription"
  pricing_tiers:
    free:
      price: 0
      limits: { features: "basic", usage: "limited" }
    starter:
      price: "$9/month"
      limits: { features: "standard", usage: "moderate" }
    pro:
      price: "$29/month"  
      limits: { features: "advanced", usage: "high" }
    enterprise:
      price: "custom"
      limits: { features: "unlimited", usage: "unlimited" }
  
  upgrade_rules:
    when: "usage_exceeds_tier_limit"
    then: "suggest_upgrade_to_next_tier"
    and: "track_conversion_metrics"
    
  discount_rules:
    annual_discount: "20%"
    student_discount: "50%"
    enterprise_negotiable: true

# Usage-Based Pricing
usage_pricing:
  algorithm_type: "pay_per_use"
  base_rate: "$0.01_per_unit"
  volume_discounts:
    - tier: "1-1000 units"
      rate: "$0.01"
    - tier: "1001-10000 units"
      rate: "$0.008"
    - tier: "10001+ units"
      rate: "$0.005"
      
  billing_rules:
    when: "monthly_usage_calculated"
    then: "apply_volume_discount_tier"
    and: "generate_invoice"
    unless: "account_suspended"

# Commission-Based Pricing (Marketplaces)
commission_pricing:
  algorithm_type: "percentage_commission"
  commission_rates:
    standard_transaction: "5%"
    premium_seller: "3%"
    enterprise_seller: "2%"
    
  commission_rules:
    when: "transaction_completed"
    then: "calculate_commission"
    and: "split_payment_to_seller"
    and: "retain_platform_fee"
    unless: "transaction_disputed"
    
  payout_rules:
    frequency: "weekly"
    minimum_payout: "$25"
    hold_period: "7_days"
```

### **Dynamic Pricing Logic**
```yaml
dynamic_pricing:
  demand_based:
    when: "demand_high"
    then: "increase_price_by_percent(10)"
    unless: "user_tier == 'enterprise'"
    
  seasonal_adjustments:
    when: "holiday_season"
    then: "apply_seasonal_discount(15)"
    and: "extend_trial_period(7_days)"
    
  competitive_pricing:
    when: "competitor_price_change_detected"
    then: "evaluate_price_adjustment"
    and: "notify_pricing_team"
    if: "price_difference > 20%"
```

---

## 🔐 User Permission Matrix Generator

### **Role-Based Access Control**
```yaml
# Permission Hierarchy
user_roles:
  super_admin:
    permissions: ["*"]  # All permissions
    restrictions: []
    
  admin:
    permissions:
      - "user_management"
      - "content_moderation" 
      - "analytics_view"
      - "feature_configuration"
    restrictions:
      - "cannot_delete_super_admin"
      - "cannot_modify_billing"
      
  creator:
    permissions:
      - "create_content"
      - "manage_own_content"
      - "view_own_analytics"
      - "respond_to_comments"
    restrictions:
      - "cannot_access_other_creator_data"
      - "cannot_modify_platform_settings"
      
  premium_user:
    permissions:
      - "access_premium_features"
      - "advanced_analytics"
      - "priority_support"
    restrictions:
      - "usage_limits_increased_not_unlimited"
      
  free_user:
    permissions:
      - "basic_features_only"
      - "limited_usage"
    restrictions:
      - "feature_limitations_apply"
      - "usage_quotas_enforced"

# Dynamic Permission Rules
permission_rules:
  when: "user_subscription_expires"
  then: "downgrade_to_free_tier_permissions"
  and: "preserve_data_but_limit_access"
  
  when: "user_violates_terms"
  then: "suspend_content_creation_permissions"
  and: "maintain_read_only_access"
  unless: "violation_severity == 'severe'"
  
  when: "enterprise_customer"
  then: "allow_custom_permission_configuration"
  and: "enable_single_sign_on"
  and: "provide_audit_trail_access"
```

### **Feature-Based Permissions**
```yaml
feature_permissions:
  content_creation:
    free_tier: 
      - "basic_templates_only"
      - "watermarked_output"
      - "limited_exports_per_month(5)"
    premium_tier:
      - "all_templates_available"
      - "no_watermarks"
      - "unlimited_exports"
      - "advanced_customization"
      
  analytics_access:
    creator:
      - "own_content_analytics"
      - "basic_engagement_metrics"
    premium_creator:
      - "detailed_analytics_dashboard"
      - "competitor_benchmarking"
      - "export_analytics_data"
    admin:
      - "platform_wide_analytics"
      - "user_behavior_insights"
      - "revenue_analytics"
```

---

## 🛡️ Content Moderation Rules Generator

### **Automated Moderation**
```yaml
content_moderation:
  ai_screening:
    text_content:
      when: "content_submitted"
      then: "run_toxicity_detection"
      and: "check_spam_patterns"
      and: "verify_language_appropriateness"
      
      auto_approve_if:
        - "toxicity_score < 0.3"
        - "spam_probability < 0.1"
        - "creator_reputation > 8.0"
        
      auto_reject_if:
        - "toxicity_score > 0.8"
        - "spam_probability > 0.7"
        - "contains_banned_keywords"
        
      human_review_if:
        - "toxicity_score between 0.3-0.8"
        - "flagged_by_users >= 3"
        - "new_creator_first_submissions"
        
    image_content:
      when: "image_uploaded"
      then: "run_visual_moderation"
      and: "check_copyright_infringement"
      and: "verify_appropriate_content"
      
      moderation_criteria:
        - "nudity_detection"
        - "violence_detection"
        - "trademark_violation"
        - "brand_safety_compliance"

# User Reporting System
user_reporting:
  report_types:
    - "inappropriate_content"
    - "copyright_violation"
    - "spam_or_scam"
    - "harassment"
    - "misinformation"
    
  report_processing:
    when: "report_submitted"
    then: "categorize_report_type"
    and: "assign_priority_level"
    and: "route_to_appropriate_reviewer"
    
    priority_rules:
      when: "report_type == 'harassment'"
      then: "set_priority_high"
      and: "notify_safety_team_immediately"
      
      when: "multiple_reports_same_content"
      then: "escalate_priority"
      and: "temporary_content_suspension"
      
  resolution_actions:
    content_warning: "add_warning_label"
    content_removal: "remove_and_notify_creator"
    user_suspension: "temporary_account_restriction"
    user_ban: "permanent_account_termination"
```

### **Creator Reputation System**
```yaml
reputation_management:
  reputation_scoring:
    starting_score: 5.0
    max_score: 10.0
    min_score: 0.0
    
    positive_actions:
      - action: "content_approved_quickly"
        score_change: "+0.1"
      - action: "high_user_engagement"
        score_change: "+0.2"
      - action: "positive_user_feedback"
        score_change: "+0.1"
        
    negative_actions:
      - action: "content_rejected"
        score_change: "-0.3"
      - action: "user_reports_validated"
        score_change: "-0.5"
      - action: "policy_violation"
        score_change: "-1.0"
        
  reputation_consequences:
    when: "reputation_score > 8.0"
    then: "enable_auto_approve_content"
    and: "reduce_moderation_delays"
    
    when: "reputation_score < 3.0"
    then: "require_manual_review_all_content"
    and: "limit_posting_frequency"
    
    when: "reputation_score < 1.0"
    then: "suspend_content_creation"
    and: "require_appeal_process"
```

---

## ⚙️ Workflow Automation Generator

### **Business Process Automation**
```yaml
automated_workflows:
  user_onboarding:
    trigger: "new_user_registration"
    steps:
      - action: "send_welcome_email"
        delay: "immediate"
      - action: "assign_onboarding_tasks"
        delay: "immediate"
      - action: "schedule_follow_up_email"
        delay: "3_days"
      - action: "prompt_profile_completion"
        delay: "7_days"
        condition: "profile_incomplete"
        
  subscription_management:
    payment_failed:
      trigger: "payment_failure_detected"
      steps:
        - action: "retry_payment"
          delay: "24_hours"
          max_attempts: 3
        - action: "send_payment_reminder"
          delay: "immediate"
        - action: "downgrade_to_free_tier"
          delay: "7_days"
          condition: "payment_still_failed"
          
    subscription_renewal:
      trigger: "subscription_expiring_soon"
      steps:
        - action: "send_renewal_reminder"
          delay: "7_days_before_expiry"
        - action: "offer_renewal_discount"
          delay: "3_days_before_expiry"
          condition: "user_hasn't_renewed"
        - action: "process_auto_renewal"
          delay: "expiry_date"
          condition: "auto_renewal_enabled"
          
  content_lifecycle:
    content_published:
      trigger: "content_goes_live"
      steps:
        - action: "notify_followers"
          delay: "immediate"
        - action: "submit_to_discovery_algorithm"
          delay: "immediate"
        - action: "track_initial_engagement"
          delay: "1_hour"
        - action: "analyze_performance"
          delay: "24_hours"
          
# Customer Support Automation
support_automation:
  ticket_routing:
    when: "support_ticket_created"
    then: "categorize_ticket_type"
    and: "assign_priority_level"
    and: "route_to_appropriate_team"
    
    routing_rules:
      billing_issues: "billing_team"
      technical_problems: "tech_support_team"
      content_disputes: "moderation_team"
      feature_requests: "product_team"
      
  auto_responses:
    when: "common_question_detected"
    then: "send_auto_response"
    and: "provide_relevant_help_articles"
    unless: "user_specifically_requests_human"
    
    escalation_rules:
      when: "auto_response_ineffective"
      then: "escalate_to_human_agent"
      and: "prioritize_ticket"
```

---

## 📊 Analytics Tracking Generator

### **Event Tracking Framework**
```yaml
analytics_tracking:
  user_events:
    registration:
      event: "user_registered"
      properties:
        - "registration_source"
        - "user_type"
        - "signup_method"
        - "referral_code"
        
    engagement:
      event: "content_interaction"
      properties:
        - "interaction_type" # [view, like, share, comment]
        - "content_id"
        - "creator_id"
        - "session_duration"
        - "device_type"
        
    conversion:
      event: "subscription_conversion"
      properties:
        - "tier_selected"
        - "conversion_source"
        - "trial_duration"
        - "discount_applied"
        
  business_metrics:
    revenue_tracking:
      when: "payment_processed"
      then: "track_revenue_event"
      properties:
        - "amount"
        - "currency"
        - "payment_method"
        - "subscription_tier"
        - "user_lifetime_value"
        
    retention_analysis:
      daily_active_users:
        metric: "count_unique_daily_users"
        calculation: "distinct_users_with_activity_today"
        
      monthly_retention:
        metric: "monthly_retention_rate"
        calculation: "users_active_month_N / users_registered_month_0"
        
    content_performance:
      when: "content_viewed"
      then: "increment_view_count"
      and: "track_engagement_duration"
      and: "record_user_journey"
      
# Privacy-Compliant Tracking
privacy_compliance:
  data_collection_rules:
    when: "user_from_eu"
    then: "require_gdpr_consent"
    and: "provide_data_deletion_option"
    and: "limit_data_retention_period"
    
    when: "user_under_13"
    then: "apply_coppa_restrictions"
    and: "require_parental_consent"
    and: "minimal_data_collection_only"
    
  data_anonymization:
    when: "analytics_data_older_than_2_years"
    then: "anonymize_personal_identifiers"
    and: "retain_aggregated_metrics_only"
```

---

## 💳 Subscription Management Generator

### **Subscription Lifecycle Management**
```yaml
subscription_management:
  trial_periods:
    free_trial:
      duration: "14_days"
      features: "full_access"
      conversion_reminders:
        - day: 7
          message: "trial_halfway_reminder"
        - day: 12
          message: "trial_ending_soon"
        - day: 14
          message: "trial_expired_conversion_offer"
          
  billing_cycles:
    monthly:
      billing_day: "subscription_start_date"
      grace_period: "3_days"
      retry_attempts: 3
      retry_schedule: [1, 3, 7] # days
      
    annual:
      discount: "20%"
      billing_day: "subscription_anniversary"
      advance_notice: "30_days"
      
  upgrade_downgrade_rules:
    immediate_upgrade:
      when: "user_upgrades_plan"
      then: "apply_new_features_immediately"
      and: "prorate_billing_difference"
      and: "adjust_next_billing_date"
      
    downgrade_at_period_end:
      when: "user_downgrades_plan"
      then: "schedule_downgrade_for_next_billing_cycle"
      and: "maintain_current_features_until_then"
      and: "send_downgrade_confirmation"
      
  cancellation_management:
    cancellation_flow:
      when: "user_initiates_cancellation"
      then: "offer_retention_discount"
      and: "provide_pause_option"
      and: "collect_cancellation_feedback"
      
    win_back_campaigns:
      when: "subscription_cancelled_30_days_ago"
      then: "send_win_back_offer"
      and: "highlight_new_features"
      unless: "user_opted_out_marketing"
```

---

## ⚖️ Compliance Requirements Generator

### **Legal & Regulatory Compliance**
```yaml
compliance_frameworks:
  gdpr_compliance:
    data_processing:
      legal_basis: "consent_or_legitimate_interest"
      data_minimization: "collect_only_necessary_data"
      purpose_limitation: "use_data_only_for_stated_purpose"
      
    user_rights:
      right_to_access:
        when: "user_requests_data_export"
        then: "provide_data_within_30_days"
        format: "machine_readable"
        
      right_to_deletion:
        when: "user_requests_account_deletion"
        then: "delete_personal_data_within_30_days"
        and: "retain_only_legally_required_data"
        exceptions: ["financial_records", "legal_obligations"]
        
      right_to_portability:
        when: "user_requests_data_portability"
        then: "provide_data_in_structured_format"
        and: "enable_direct_transfer_if_possible"
        
  hipaa_compliance: # Healthcare industry
    data_encryption:
      at_rest: "aes_256_encryption"
      in_transit: "tls_1.3_minimum"
      key_management: "hardware_security_modules"
      
    access_controls:
      minimum_necessary: "limit_access_to_job_requirements"
      audit_logging: "log_all_data_access_attempts"
      session_management: "automatic_logout_after_inactivity"
      
  pci_dss_compliance: # Payment processing
    payment_security:
      when: "processing_credit_card_data"
      then: "use_certified_payment_processor"
      and: "never_store_card_numbers"
      and: "implement_fraud_detection"
      
    network_security:
      firewall_rules: "restrict_payment_network_access"
      vulnerability_scanning: "monthly_security_scans"
      penetration_testing: "annual_security_assessment"
```

---

## 🚀 Business Process Optimization Generator

### **Performance Optimization Rules**
```yaml
process_optimization:
  cost_optimization:
    infrastructure_scaling:
      when: "server_utilization < 30%"
      then: "scale_down_infrastructure"
      and: "reduce_hosting_costs"
      unless: "traffic_spike_predicted"
      
    feature_usage_analysis:
      when: "feature_usage < 5%_of_users"
      then: "evaluate_feature_deprecation"
      and: "survey_users_about_necessity"
      and: "calculate_maintenance_cost_benefit"
      
  revenue_optimization:
    pricing_experiments:
      when: "new_pricing_strategy_proposed"
      then: "run_ab_test_with_percentage_of_users"
      and: "measure_conversion_rate_impact"
      and: "analyze_customer_lifetime_value_change"
      
    upselling_opportunities:
      when: "user_approaching_usage_limit"
      then: "suggest_upgrade_at_optimal_moment"
      and: "highlight_relevant_premium_features"
      unless: "user_recently_upgraded"
      
  operational_efficiency:
    customer_support:
      when: "support_ticket_volume_high"
      then: "analyze_common_issues"
      and: "create_self_service_solutions"
      and: "update_documentation"
      
    content_moderation:
      when: "moderation_queue_backlog > 2_hours"
      then: "temporarily_increase_auto_approval_threshold"
      and: "alert_moderation_team"
      and: "consider_additional_staffing"
```

---

## 🔧 Generation Rules by Business Model

### **SaaS Applications**
```yaml
saas_specific_rules:
  pricing: "subscription_tiered_model"
  permissions: "role_based_access_control"
  moderation: "content_quality_focused"
  workflows: "trial_conversion_optimization"
  analytics: "engagement_and_retention_focused"
  compliance: "data_protection_emphasis"
```

### **Marketplace Platforms**
```yaml
marketplace_specific_rules:
  pricing: "commission_based_model"
  permissions: "buyer_seller_creator_roles"
  moderation: "trust_and_safety_focused"
  workflows: "two_sided_onboarding"
  analytics: "transaction_volume_focused"
  compliance: "payment_processing_emphasis"
```

### **Creator Economy Platforms**
```yaml
creator_economy_rules:
  pricing: "revenue_sharing_model"
  permissions: "creator_consumer_hierarchy"
  moderation: "content_creator_reputation_system"
  workflows: "creator_monetization_optimization"
  analytics: "creator_success_metrics"
  compliance: "intellectual_property_protection"
```

---

## 📋 Output Validation

### **Business Logic Validation Framework**
```yaml
validation_rules:
  consistency_checks:
    - "pricing_rules_align_with_business_model"
    - "permission_matrix_covers_all_user_types"
    - "compliance_requirements_match_industry"
    - "workflows_support_business_objectives"
    
  completeness_checks:
    - "all_user_journeys_have_automation_rules"
    - "all_business_processes_have_defined_logic"
    - "all_compliance_requirements_addressed"
    - "all_revenue_streams_have_tracking_rules"
    
  feasibility_checks:
    - "business_rules_are_technically_implementable"
    - "compliance_requirements_are_achievable"
    - "automation_workflows_are_logical"
    - "analytics_tracking_is_privacy_compliant"
```

This business logic generator creates comprehensive, executable business rules that Claude Code can implement as working systems, ensuring the startup operates efficiently and compliantly from day one.