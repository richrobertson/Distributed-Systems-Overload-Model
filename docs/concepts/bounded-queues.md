# Bounded Queues

**Summary:** Bounded queues cap backlog size and age to prevent latency explosion and memory-based failure under overload.

## What it is
Queues with explicit limits on depth, age, and retention behavior.

## Why it matters
Unbounded queues hide overload temporarily and convert short spikes into long recovery tails.

## What problem it solves
They stop infinite backlog accumulation that eventually destabilizes workers and storage.

## How it works
Enforce max depth, per-item TTL, priority lanes, and clear reject/defer semantics when limits are reached.

## What it is not
It is not “set and forget” buffering and not equivalent to durability guarantees.

## Tradeoffs and failure modes
More immediate rejections and potential client-visible errors under bursty demand.

## Where it fits in the overload-control stack
Between ingress and worker execution in job, workflow, and event processing systems.

## Production scenario
Workflow engine queue depth limit prevents command flood from causing hour-long stale backlog after incident.

## What to instrument
Queue depth, age percentiles, dropped/expired items, and drain velocity after surge.

## Related concepts
- [Backpressure](backpressure.md)
- [Bounded Queues vs Unbounded Work](../comparisons/bounded-queues-vs-unbounded-work.md)

## Closing summary
A bounded queue makes overload explicit and recoverable.
