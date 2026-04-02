# Bulkheads

**Summary:** Bulkheads partition resources so failures in one workload compartment do not sink the entire service.

## What it is
Resource partitioning patterns for threads, queues, pools, and quotas.

## Why it matters
Without compartments, hotspots consume all shared capacity.

## What problem it solves
Contain overload and failure blast radius inside bounded compartments.

## How it works
Allocate independent pools with per-compartment limits and fallback behaviors.

## What it is not
Not full tenant isolation or complete failure prevention.

## Tradeoffs and failure modes
Capacity fragmentation and tuning complexity across compartments.

## Where it fits in the overload-control stack
Worker pools, dependency clients, and multitenant schedulers.

## Production scenario
Notification worker pool split by channel (email, SMS, push) prevents SMS provider outage from stalling email throughput.

## What to instrument
Compartment saturation, spillover attempts, and protected-path availability.

## Related concepts
- [Dependency Isolation](dependency-isolation.md)
- [Priority and Fairness](priority-and-fairness.md)

## Related reading on myrobertson.com
- [Distributed Systems Writing Hub](https://www.myrobertson.com/blog/)
- [Backpressure in Distributed Systems: Stability, Correctness, and Graceful Degradation](https://www.myrobertson.com/blog/backpressure-stability-correctness-distributed-systems)
- [API Backpressure Explained Simply](https://www.myrobertson.com/blog/api-backpressure-explained-simply)
- [What Is a Control Plane?](https://www.myrobertson.com/blog/what-is-a-control-plane)
- [Architecting a Multitenant Control Plane for a Next-Generation Data Tier](https://www.myrobertson.com/blog/architecting-a-multitenant-control-plane-for-a-next-generation-data-tier)
- [Distributed Systems Case Studies](https://www.myrobertson.com/case-studies/)

## Closing summary
Bulkheads are practical blast-radius boundaries for overload conditions.
