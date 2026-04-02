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

## Closing summary
Bulkheads are practical blast-radius boundaries for overload conditions.
