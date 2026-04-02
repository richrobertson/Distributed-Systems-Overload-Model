# Overload Control Model

**Summary:** Overload control is a coordinated system of bounded decisions that determines what work enters, propagates, and survives when demand exceeds safe capacity.

## What this model is
The overload-control model is an end-to-end control architecture for distributed systems. It treats stability as an explicit design objective and separates three concerns:
1. **Admission:** should this request enter the system now?
2. **Execution:** how much in-flight work can each stage safely handle?
3. **Protection:** what should be rejected, downgraded, or isolated when limits are hit?

A system is stable when these decisions remain bounded and enforceable under stress.

## Why systems fail under load
Most major incidents are not single hard crashes. They are progressive failures:
- latency rises, then timeouts increase
- retries amplify demand
- queues absorb excess work until memory, CPU, or dependency budgets collapse
- shared control-plane resources starve critical workflows

Unbounded acceptance is usually the root cause; downstream failures are often secondary effects.

## Core control loop
1. **Detect pressure:** queue depth, concurrency saturation, timeout rate, resource pressure.
2. **Signal pressure:** propagate backpressure upstream quickly.
3. **Constrain work:** admission gates, rate limits, bounded queues, concurrency caps.
4. **Contain failures:** isolate dependencies, open breakers, shed low-priority work.
5. **Preserve service:** degrade non-critical paths and protect core operations.
6. **Recover deliberately:** gradual ramp-up with hysteresis to avoid oscillation.

## Overload-control stack
### 1) Front-door controls
- Admission control
- Tenant-aware rate limiting
- Concurrency envelopes at ingress

### 2) In-system flow controls
- Bounded queues
- Worker concurrency limits
- Backpressure propagation across async boundaries

### 3) Dependency protection
- Circuit breakers
- Isolation pools/bulkheads
- Timeout budgets and fail-fast policies

### 4) Service preservation
- Priority-aware load shedding
- Graceful degradation and fallback modes

### 5) Operational feedback
- Saturation-centric telemetry
- SLO-aware alerts for near-overload zones
- Recovery safety checks (burn-rate + queue drain velocity)

## Key distinctions that reduce confusion
- **Admission control vs rate limiting:** admission decides acceptance under current system health; rate limiting enforces traffic contracts over time.
- **Backpressure vs load shedding:** backpressure slows producers; shedding rejects work that cannot be safely processed.
- **Circuit breakers vs retries:** breakers stop wasteful calls to unhealthy dependencies; retries can increase overload if unbudgeted.
- **Graceful degradation vs failure:** degradation intentionally reduces optional behavior to preserve core service.

## Design invariants
- No unbounded queues on critical paths.
- No unbounded retries without budgets and jitter.
- No shared pools without fairness or isolation in multitenant systems.
- No hidden asynchronous work without explicit ownership and limits.
- No recovery without controlled ramp-up.

## Production example: multitenant control plane
A control plane receives API writes, enqueues orchestration jobs, and executes workflows against regional agents.
- Admission gates reserve capacity for high-priority reconciliations.
- Tenant-aware limits prevent one customer’s burst from monopolizing workflow workers.
- Queue TTL and depth bounds prevent stale migrations from consuming memory indefinitely.
- Breakers isolate a failing cloud-provider API to avoid global worker exhaustion.
- Degraded mode disables non-critical notifications while preserving core reconciliation.

## What to measure
- Admission accept/reject rate by reason code and tenant
- Queue depth, age percentiles, and drain rate
- In-flight concurrency saturation by component
- Breaker state transitions and open duration
- Shed volume by priority tier
- Degradation mode activation duration and user impact

## Anti-patterns
- “Queue it and process later” without boundedness.
- “Retry until success” without budget, deadline, or jitter.
- Single global worker pool for mixed-priority workloads.
- Using p50 latency as stability evidence.

## Related concepts
- [Overload Control Pipeline](overload-control-pipeline.md)
- [Why Systems Fail Under Load](why-systems-fail-under-load.md)
- [Admission Control](../concepts/admission-control.md)
- [Backpressure](../concepts/backpressure.md)
- [Load Shedding](../concepts/load-shedding.md)
- [Graceful Degradation](../concepts/graceful-degradation.md)

## Closing summary
Overload is not an anomaly; it is an operating condition. Stable distributed systems survive it by enforcing boundedness, propagating pressure signals early, and protecting critical paths through explicit rejection and degradation policies.
