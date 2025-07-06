# Claude Code Instructions for Universal Startup Specification Framework

## Framework Overview
This framework transforms startup ideas into complete, AI-executable specification repositories. Each module processes specific aspects of startup generation in a coordinated sequence.

## Processing Instructions

### Phase 1: Business Intelligence
1. **business-model-generator.md** - Analyze startup concept and generate revenue model
2. **persona-generator.md** - Create detailed user personas using business model output

### Phase 2: Technical Architecture  
3. **tech-architecture-generator.md** - Select optimal tech stack based on business model and personas

### Phase 3: Feature Specification
4. **feature-generator.md** - Generate complete feature set using all previous outputs

### Phase 4: Brand & Business Logic
5. **brand-generator.md** - Encode brand personality using personas and business model
6. **business-logic-generator.md** - Create executable business rules using business model and features

### Phase 5: Infrastructure & Operations
7. **database-generator.md** - Design database schema and migration strategies using feature data requirements
8. **devops-generator.md** - Create CI/CD pipelines and infrastructure configs using tech architecture
9. **monitoring-generator.md** - Generate monitoring, logging, and alerting configs using application architecture
10. **error-handling-generator.md** - Create error handling and resilience patterns using feature specifications

### Phase 6: Quality & Implementation
11. **testing-generator.md** - Generate testing frameworks using all specifications and infrastructure configs
12. **roadmap-generator.md** - Create implementation timeline using business objectives and complete tech stack

### Phase 7: Final Assembly
13. **claude-instructions-generator.md** - Generate AI execution instructions using complete specification set

## Key Execution Rules

### Input Processing
- Always validate startup input against `schemas/startup-input.schema.json`
- Use adaptive generation rules based on business model type
- Maintain cross-module data flow and dependencies

### Output Generation
- Generate repository structure using `templates/repository-structure-template.md`
- Validate all outputs against corresponding schemas in `schemas/`
- Ensure all files populate with real, actionable content

### Quality Assurance
- Validate business model feasibility and market fit
- Ensure technical architecture scalability and implementation feasibility
- Verify feature completeness and behavioral specification accuracy
- Check cross-reference integrity and dependency mapping
- Confirm brand consistency across all specifications

### File Management
- Create numbered folder structure (00-10) for organized processing
- Use consistent naming conventions for all generated files
- Maintain template format across all output files

## Example Execution Flow

```
Input: startup_input.yaml
↓
business-model-generator.md → 01-foundation/business-model.yaml
↓
persona-generator.md → 01-foundation/user-personas.yaml
↓
tech-architecture-generator.md → 02-architecture/tech-stack.yaml
↓
feature-generator.md → 03-features/F001-F014+.yaml
↓
brand-generator.md → 08-brand/personality-encoding.yaml
↓
business-logic-generator.md → 07-business-rules/*.yaml
↓
database-generator.md → 02-architecture/database-*.yaml + 05-templates/database-models/
↓
devops-generator.md → 05-templates/deployment/ + 10-deployment/ci-cd-*.yaml
↓
monitoring-generator.md → 05-templates/monitoring/ + 10-deployment/monitoring-*.yaml
↓
error-handling-generator.md → 05-templates/error-handling/ + 02-architecture/resilience-*.yaml
↓
testing-generator.md → 09-testing/acceptance-criteria-framework.yaml
↓
roadmap-generator.md → 10-deployment/mvp-implementation-roadmap.yaml
↓
claude-instructions-generator.md → 00-meta/claude-instructions.md
↓
Output: Complete {STARTUP_NAME}-setup/ repository
```

## Validation Commands

Before completion, verify:
- All required folders (00-10) exist and are populated
- All generated files validate against their schemas
- Cross-references between modules are consistent
- Business logic aligns with business model
- Technical decisions support feature requirements

## Success Criteria

A successful generation includes:
- 150+ populated files in standardized structure
- Valid business model with clear revenue strategy
- Complete feature specifications with user stories
- Optimal tech stack selection with architecture decisions
- Production-ready database schema and migration strategies
- Complete CI/CD pipelines and infrastructure configurations
- Comprehensive monitoring, logging, and alerting setup
- Robust error handling and resilience patterns
- Brand personality consistently encoded throughout
- Comprehensive testing and deployment frameworks
- Clear implementation roadmap and timeline

## Error Handling

If any module fails:
1. Validate input format and completeness
2. Check for missing dependencies from previous modules
3. Verify schema compliance
4. Ensure all required templates are available
5. Validate business logic consistency

## Performance Optimization

- Process modules in parallel where dependencies allow
- Cache intermediate results for reuse
- Validate inputs early to prevent downstream failures
- Use efficient template processing for large file generation

This framework is designed for autonomous Claude Code execution with minimal human intervention while ensuring high-quality, comprehensive startup specifications.