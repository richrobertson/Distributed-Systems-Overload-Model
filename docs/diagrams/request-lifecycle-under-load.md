# Request Lifecycle Under Load

**Summary:** Diagram and interpretation for request lifecycle under load.

```mermaid
sequenceDiagram
    participant Client
    participant Gateway
    participant API
    participant Queue
    participant Worker
    participant Dependency
    Client->>Gateway: Request burst
    Gateway->>Gateway: Admission + rate checks
    Gateway->>API: Accepted requests
    API->>Queue: Enqueue bounded work
    Queue-->>API: Queue near limit signal
    API-->>Gateway: Backpressure signal
    Worker->>Dependency: Call with timeout
    Dependency-->>Worker: Slow/failing responses
    Worker->>Worker: Breaker opens
    Gateway-->>Client: Shed low-priority traffic
```

## Interpretation
This diagram highlights overload decision points and containment boundaries.

## Related concepts
- [Overload Control Model](../overview/overload-control-model.md)
