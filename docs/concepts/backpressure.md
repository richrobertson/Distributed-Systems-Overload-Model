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

## Closing summary
Backpressure is the braking system that keeps distributed throughput aligned with real capacity.
