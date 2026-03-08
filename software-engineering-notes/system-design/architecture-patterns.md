# Architecture Patterns

Common patterns for organizing software systems at scale.

## Monolithic Architecture

Single deployable unit containing all functionality.

**Pros**: Simple development, easy debugging, straightforward deployment  
**Cons**: Scaling limitations, tight coupling, longer build times

```
┌─────────────────────────────┐
│         Monolith            │
│  ┌─────┐ ┌─────┐ ┌─────┐   │
│  │Users│ │Orders│ │Payment│ │
│  └─────┘ └─────┘ └─────┘   │
│         Database            │
└─────────────────────────────┘
```

## Microservices Architecture

Application split into small, independent services.

**Pros**: Independent scaling, technology flexibility, fault isolation  
**Cons**: Operational complexity, network latency, data consistency

```
┌─────────┐  ┌─────────┐  ┌─────────┐
│ Users   │  │ Orders  │  │ Payment │
│ Service │  │ Service │  │ Service │
│   DB    │  │   DB    │  │   DB    │
└─────────┘  └─────────┘  └─────────┘
```

## Event-Driven Architecture

Components communicate through events asynchronously.

```
Producer → Message Queue → Consumer
                ↓
            Event Store
```

**Use Cases**: Real-time systems, decoupled services, audit logging

## API Gateway Pattern

Single entry point for all client requests.

**Responsibilities**:

- Request routing
- Authentication
- Rate limiting
- Response caching

## Other Common Patterns

| Pattern         | Purpose                    |
| --------------- | -------------------------- |
| CQRS            | Separate read/write models |
| Saga            | Distributed transactions   |
| Circuit Breaker | Fault tolerance            |
| Sidecar         | Cross-cutting concerns     |

## Choosing an Architecture

- **Start with monolith** for new projects
- Migrate to microservices when scaling is needed
- Consider team size and operational maturity
- Evaluate trade-offs based on requirements
- Don't over-engineer early
