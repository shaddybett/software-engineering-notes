# Scalability Basics

Scalability is a system's ability to handle increased load by adding resources.

## Types of Scaling

### Vertical Scaling (Scale Up)

- Add more power to existing machine (CPU, RAM)
- Simpler but has hardware limits
- Single point of failure

### Horizontal Scaling (Scale Out)

- Add more machines to the system
- Better fault tolerance
- Requires distributed system design

## Key Strategies

### 1. Load Balancing

Distributes traffic across multiple servers:

- Round-robin, least connections, IP hash
- Tools: Nginx, HAProxy, AWS ALB

### 2. Caching

Reduces database load and latency:

```
Client → Cache (Redis) → Database
```

- Cache frequently accessed data
- Implement cache invalidation strategies

### 3. Database Scaling

- **Read Replicas**: Distribute read queries
- **Sharding**: Partition data across databases
- **Connection Pooling**: Reuse database connections

### 4. Asynchronous Processing

- Use message queues (RabbitMQ, SQS) for background tasks
- Decouple components for independent scaling

## Performance Metrics

- **Latency**: Response time (p50, p95, p99)
- **Throughput**: Requests per second (RPS)
- **Availability**: Uptime percentage (99.9% = 8.76h downtime/year)

## Best Practices

- Design stateless services for easy horizontal scaling
- Cache at multiple levels (CDN, application, database)
- Use async processing for non-critical operations
- Monitor and set up alerts for key metrics
- Plan capacity before traffic spikes
- Start simple, scale as needed
