# Database Design & Migration Generator

## Purpose
Generate comprehensive database architecture, schema design patterns, and migration strategies for startup data requirements. This module creates production-ready database configurations, migration scripts, and data management frameworks.

## Input Dependencies
- `02-architecture/tech-stack.yaml` - Database technology decisions
- `03-features/` - Feature specifications requiring data storage
- `07-business-rules/` - Business logic affecting data constraints
- `01-foundation/user-personas.yaml` - User data requirements

## Core Processing Logic

### 1. Database Architecture Selection
```yaml
database_patterns:
  simple_relational:
    type: "postgresql"
    structure: "single_database"
    scaling: "read_replicas"
    backup: "daily_automated"
    
  microservices_data:
    type: "polyglot_persistence"
    structure: "database_per_service"
    scaling: "service_specific"
    backup: "service_level_backups"
    
  high_scale:
    type: "distributed_database"
    structure: "sharded_clusters"
    scaling: "horizontal_sharding"
    backup: "distributed_backups"
```

### 2. Schema Design Patterns
```yaml
schema_patterns:
  user_management:
    tables: ["users", "profiles", "sessions", "permissions"]
    relationships: "normalized"
    indexes: "performance_optimized"
    constraints: "referential_integrity"
    
  content_management:
    tables: ["content", "metadata", "tags", "relationships"]
    relationships: "flexible_schema"
    indexes: "search_optimized"
    constraints: "soft_deletes"
    
  transaction_processing:
    tables: ["transactions", "orders", "payments", "audit_logs"]
    relationships: "strictly_normalized"
    indexes: "transaction_optimized"
    constraints: "acid_compliance"
```

### 3. Migration Strategy
```yaml
migration_patterns:
  version_controlled:
    strategy: "sequential_migrations"
    rollback: "automatic_rollback"
    testing: "migration_testing"
    monitoring: "migration_monitoring"
    
  zero_downtime:
    strategy: "blue_green_migrations"
    rollback: "instant_rollback"
    testing: "production_like_testing"
    monitoring: "real_time_monitoring"
```

## Output Generation

### 1. Database Schema Definitions
```sql
-- users table with comprehensive structure
CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    email_verified BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
    updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
    deleted_at TIMESTAMP WITH TIME ZONE NULL
);

-- indexes for performance
CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_created_at ON users(created_at);
CREATE INDEX idx_users_active ON users(id) WHERE deleted_at IS NULL;

-- triggers for updated_at
CREATE OR REPLACE FUNCTION update_updated_at_column()
RETURNS TRIGGER AS $$
BEGIN
    NEW.updated_at = NOW();
    RETURN NEW;
END;
$$ language 'plpgsql';

CREATE TRIGGER update_users_updated_at 
    BEFORE UPDATE ON users 
    FOR EACH ROW 
    EXECUTE FUNCTION update_updated_at_column();
```

### 2. Migration Scripts
```sql
-- migrations/001_create_users_table.up.sql
BEGIN;

CREATE EXTENSION IF NOT EXISTS "uuid-ossp";

CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    email_verified BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
    updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

CREATE INDEX idx_users_email ON users(email);

COMMIT;

-- migrations/001_create_users_table.down.sql
BEGIN;

DROP TABLE IF EXISTS users;

COMMIT;
```

### 3. Database Configuration
```yaml
# database/config.yml
development:
  adapter: postgresql
  database: startup_development
  username: postgres
  password: development_password
  host: localhost
  port: 5432
  pool: 5
  timeout: 5000
  
production:
  adapter: postgresql
  url: ${DATABASE_URL}
  pool: ${DB_POOL_SIZE:-20}
  timeout: ${DB_TIMEOUT:-5000}
  ssl_mode: require
  connection_retry_attempts: 3
  connection_retry_delay: 1000
```

### 4. Data Access Layer Templates
```javascript
// models/User.js - Example ORM model
const { Model, DataTypes } = require('sequelize');

class User extends Model {
  static init(sequelize) {
    return super.init({
      id: {
        type: DataTypes.UUID,
        defaultValue: DataTypes.UUIDV4,
        primaryKey: true
      },
      email: {
        type: DataTypes.STRING,
        allowNull: false,
        unique: true,
        validate: {
          isEmail: true
        }
      },
      passwordHash: {
        type: DataTypes.STRING,
        allowNull: false,
        field: 'password_hash'
      },
      emailVerified: {
        type: DataTypes.BOOLEAN,
        defaultValue: false,
        field: 'email_verified'
      }
    }, {
      sequelize,
      modelName: 'User',
      tableName: 'users',
      paranoid: true, // soft deletes
      timestamps: true,
      underscored: true
    });
  }
  
  static associate(models) {
    // Define associations here
  }
}

module.exports = User;
```

## Business Model Adaptations

### SaaS Platform
```yaml
saas_database:
  multi_tenancy: "tenant_per_schema"
  data_isolation: "complete_tenant_isolation"
  scaling: "tenant_based_sharding"
  backup: "tenant_specific_backups"
  compliance: "per_tenant_encryption"
  
  tenant_schema:
    - tenant_id (partition key)
    - data_residency_region
    - compliance_requirements
    - feature_flags
```

### Marketplace
```yaml
marketplace_database:
  user_types: "buyers_sellers_admins"
  transaction_integrity: "acid_transactions"
  search_optimization: "elasticsearch_integration"
  audit_trail: "complete_transaction_history"
  
  core_entities:
    - users (buyers/sellers)
    - products/services
    - transactions
    - reviews_ratings
    - messaging
```

### E-commerce
```yaml
ecommerce_database:
  inventory_management: "real_time_inventory"
  order_processing: "order_state_machine"
  payment_integration: "payment_method_abstraction"
  product_catalog: "hierarchical_categories"
  
  performance_requirements:
    - product_search_response: "<100ms"
    - checkout_process: "<500ms"
    - inventory_updates: "real_time"
```

## Generated Files Structure

### 05-templates/database-models/
```
database-models/
├── schemas/
│   ├── postgresql/
│   │   ├── initial_schema.sql
│   │   ├── indexes.sql
│   │   └── triggers.sql
│   ├── mongodb/
│   │   ├── collections.js
│   │   └── indexes.js
│   └── mysql/
│       ├── schema.sql
│       └── procedures.sql
├── migrations/
│   ├── postgresql/
│   │   ├── 001_create_users.sql
│   │   ├── 002_create_products.sql
│   │   └── migration_template.sql
│   └── migration_config.yml
├── models/
│   ├── sequelize/
│   │   ├── User.js
│   │   ├── Product.js
│   │   └── index.js
│   ├── mongoose/
│   │   ├── User.js
│   │   └── Product.js
│   └── prisma/
│       └── schema.prisma
├── seeds/
│   ├── development.sql
│   ├── test.sql
│   └── seed_config.yml
└── backup/
    ├── backup_strategy.yml
    ├── backup_scripts.sh
    └── restore_procedures.md
```

### 02-architecture/
```
architecture/
├── database-architecture.yaml
├── data-flow-diagrams.yaml
├── backup-strategy.yaml
├── scaling-strategy.yaml
└── compliance-requirements.yaml
```

## Migration Management

### 1. Migration Framework
```yaml
migration_strategy:
  versioning: "sequential_numbering"
  rollback_support: "automatic_rollback"
  testing: "migration_testing_framework"
  monitoring: "migration_progress_tracking"
  
  safety_checks:
    - dry_run_validation
    - backup_before_migration
    - rollback_plan_verification
    - performance_impact_analysis
```

### 2. Zero-Downtime Migrations
```yaml
zero_downtime_patterns:
  additive_changes:
    - add_columns
    - add_indexes
    - add_tables
    
  breaking_changes:
    - column_rename_strategy
    - table_split_strategy
    - data_type_change_strategy
    
  deployment_coordination:
    - application_deployment_sync
    - feature_flag_coordination
    - rollback_coordination
```

## Quality Assurance

### Validation Checkpoints
1. **Schema Integrity**: Validate referential integrity and constraints
2. **Performance Optimization**: Ensure indexes and queries are optimized
3. **Migration Safety**: Verify migration rollback procedures
4. **Data Security**: Validate encryption and access controls
5. **Compliance Requirements**: Ensure data handling meets regulations

### Testing Requirements
- Unit tests for database models
- Integration tests for data access layer
- Migration testing on production-like data
- Performance testing under load
- Backup and restore testing

## Integration Points

### With Other Modules
- **tech-architecture-generator.md**: Uses database technology decisions
- **feature-generator.md**: Implements feature data requirements
- **business-logic-generator.md**: Enforces business rules at database level
- **devops-generator.md**: Integrates with deployment and backup strategies

### With External Systems
- ORM frameworks (Sequelize, Prisma, Mongoose)
- Migration tools (Flyway, Liquibase)
- Backup solutions (pg_dump, MongoDB Atlas)
- Monitoring tools (DataDog, New Relic)

## Success Metrics

### Performance Metrics
- **Query Response Time**: <100ms for simple queries, <500ms for complex
- **Migration Success Rate**: >99% successful migrations
- **Backup Success Rate**: 100% successful automated backups
- **Data Consistency**: 100% referential integrity maintenance

### Operational Metrics
- **Database Uptime**: >99.9% availability
- **Backup Recovery Time**: <1 hour for full database restore
- **Migration Downtime**: <5 minutes for breaking changes
- **Data Loss Prevention**: Zero data loss tolerance

This module ensures startups have robust, scalable, and maintainable database architectures that can evolve with business growth while maintaining data integrity and performance.