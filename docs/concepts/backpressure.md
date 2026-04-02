# Backpressure

**Summary:** Backpressure propagates downstream saturation upstream so producers slow down before queues and retries explode.

## What it is
Capacity feedback that tells upstream components to reduce send rate or concurrency.

## Why it matters
Without backpressure, producers continue at full speed while downstream collapses.

## What problem it solves
It prevents hidden queue growth and timeout cascades across service boundaries.

## How it works
Signals include explicit protocol responses, queue-full responses, stream flow control, adaptive concurrency signals, and reduced permit issuance.

## What it is not
It is not mere observability and not the same as dropping traffic.

## Tradeoffs and failure modes
Slowdown can increase latency for low-priority work. Poor signal propagation causes oscillations.

## Where it fits in the overload-control stack
Between APIs and workers, between workflow scheduler and executors, and across service-to-service calls.

## Production scenario
Workflow command ingestion outruns executors. Executor queue limits trigger reduced dispatcher credits, preventing runaway backlog.

## What to instrument
Producer send-rate reduction, queue-full events, in-flight permits, and backlog drain time.

## Related concepts
- [Bounded Queues](bounded-queues.md)
- [Load Shedding](load-shedding.md)
- [Request Lifecycle Diagram](../diagrams/request-lifecycle-under-load.md)

## Related reading on myrobertson.com
- [Distributed Systems Writing Hub](https://www.myrobertson.com/blog/)
- [Backpressure in Distributed Systems: Stability, Correctness, and Graceful Degradation](https://www.myrobertson.com/blog/backpressure-stability-correctness-distributed-systems)
- [API Backpressure Explained Simply](https://www.myrobertson.com/blog/api-backpressure-explained-simply)
- [What Is a Control Plane?](https://www.myrobertson.com/blog/what-is-a-control-plane)
- [Architecting a Multitenant Control Plane for a Next-Generation Data Tier](https://www.myrobertson.com/blog/architecting-a-multitenant-control-plane-for-a-next-generation-data-tier)
- [Distributed Systems Case Studies](https://www.myrobertson.com/case-studies/)

## Closing summary
Backpressure is the braking system that keeps distributed throughput aligned with real capacity.
