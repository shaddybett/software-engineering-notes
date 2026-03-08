# Database Design

Database design involves structuring data for efficient storage, retrieval, and integrity.

## SQL vs NoSQL

| SQL (Relational)      | NoSQL (Non-Relational)       |
| --------------------- | ---------------------------- |
| Structured schema     | Flexible schema              |
| ACID transactions     | Eventually consistent        |
| Tables with relations | Documents, key-value, graphs |
| PostgreSQL, MySQL     | MongoDB, Redis, DynamoDB     |

## Normalization

Organizing data to reduce redundancy:

- **1NF**: Atomic values, no repeating groups
- **2NF**: 1NF + no partial dependencies
- **3NF**: 2NF + no transitive dependencies

```sql
-- Normalized design
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    email VARCHAR(255) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT NOW()
);

CREATE TABLE orders (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id),
    total DECIMAL(10, 2),
    status VARCHAR(50)
);
```

## Indexing

Indexes speed up queries but slow down writes:

```sql
-- Create index on frequently queried columns
CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_orders_user_id ON orders(user_id);

-- Composite index for multi-column queries
CREATE INDEX idx_orders_status_date ON orders(status, created_at);
```

## Key Relationships

- **One-to-One**: User ↔ Profile
- **One-to-Many**: User → Orders
- **Many-to-Many**: Students ↔ Courses (via junction table)

## Best Practices

- Always define primary keys
- Use foreign keys for referential integrity
- Index columns used in WHERE, JOIN, ORDER BY
- Avoid over-indexing (impacts write performance)
- Use appropriate data types (VARCHAR vs TEXT)
- Consider denormalization for read-heavy workloads
- Plan for data growth and query patterns
