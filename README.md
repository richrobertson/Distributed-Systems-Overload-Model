# Distributed Systems Overload Model

A structured model for how distributed systems stay stable under load using admission control, rate limiting, backpressure, circuit breakers, load shedding, and graceful degradation.

## Why this repo exists
Overload control is usually documented in fragments: one team documents retries, another team documents rate limiting, and incident reviews mention queue growth without tying it to front-door admission. This repository provides an end-to-end model so engineers can reason about stability as a coordinated control system rather than isolated mechanisms.

## The overload-control pipeline

**Ingress → Admission Control → Rate Limiting → Backpressure → Circuit Breakers → Load Shedding → Graceful Degradation**

This sequence is not strictly linear in implementation, but it is the operational order in which stable systems decide what work to accept, execute, defer, or reject.

## Who this is for
- Senior backend engineers operating high-throughput APIs
- Platform and control-plane engineers running shared infrastructure
- Staff/principal candidates preparing for systems-level architecture interviews
- SREs, operators, and architects responsible for reliability under stress

## Start here
- [Overload Control Model](docs/overview/overload-control-model.md)
- [Overload Control Pipeline](docs/overview/overload-control-pipeline.md)
- [Admission Control](docs/concepts/admission-control.md)
- [Backpressure](docs/concepts/backpressure.md)
- [Case Examples](docs/case-examples/customer-api-spike-example.md)

## Topic map
### Front-door control
- [Admission Control](docs/concepts/admission-control.md)
- [Rate Limiting](docs/concepts/rate-limiting.md)
- [Concurrency Limits](docs/concepts/concurrency-limits.md)

### In-system propagation
- [Backpressure](docs/concepts/backpressure.md)
- [Bounded Queues](docs/concepts/bounded-queues.md)
- [Retries and Retry Storms](docs/concepts/retries-and-retry-storms.md)

### Failure containment
- [Circuit Breakers](docs/concepts/circuit-breakers.md)
- [Dependency Isolation](docs/concepts/dependency-isolation.md)
- [Bulkheads](docs/concepts/bulkheads.md)
- [Load Shedding](docs/concepts/load-shedding.md)

### Recovery and degraded modes
- [Graceful Degradation](docs/concepts/graceful-degradation.md)
- [Designing for Degraded Modes](docs/design-guides/designing-for-degraded-modes.md)
- [Designing Safe Fallbacks](docs/design-guides/designing-safe-fallbacks.md)

### Observability and operations
- [Overload Observability](docs/concepts/overload-observability.md)
- [Instrumentation and Alerting](docs/design-guides/instrumentation-and-alerting.md)
- [Sample Metrics](examples/sample-metrics.md)

## Design principles
- Never accept work you cannot safely process.
- Bound queues, concurrency, and retries.
- Protect critical paths first.
- Fail early instead of failing slowly.
- Design degraded modes before incidents.
- Treat retries as additional demand, not recovery magic.

## Diagrams
- [Overload Control Pipeline](docs/diagrams/overload-control-pipeline.md)
- [Request Lifecycle Under Load](docs/diagrams/request-lifecycle-under-load.md)
- [Dependency Failure Containment](docs/diagrams/dependency-failure-containment.md)
- [Multitenant Overload Control](docs/diagrams/multitenant-overload-control.md)

## Machine-readable knowledge
- [Knowledge Schema](schemas/knowledge.json)
- [Content Index](schemas/content-index.json)
- [Topic Graph](schemas/topic-graph.json)

## Roadmap
- Adaptive concurrency control and token-aware admission
- Retry budgets and tenant-specific retry governance
- Tail-latency containment patterns at p99.9
- Bulkheads vs isolation pools with quantitative sizing guidance
- Overload in event-driven and stream-processing architectures
- Overload-aware API contracts and explicit degradation semantics
- Load and chaos experiments focused on saturation transitions

## Contributing
See [CONTRIBUTING.md](CONTRIBUTING.md), [SECURITY.md](SECURITY.md), and [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).
