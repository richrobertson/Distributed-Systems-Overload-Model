# Priority and Fairness

**Summary:** Priority and fairness policies allocate constrained capacity across workload classes so critical operations survive and tenants remain protected.

## What it is
Scheduling and quota strategies that balance business criticality and tenant equity.

## Why it matters
Shared systems fail socially and technically when one class or tenant monopolizes resources.

## What problem it solves
Prevents starvation of critical paths and noisy-neighbor dominance.

## How it works
Combine weighted fair queuing, per-tier budgets, reserve pools, and starvation guards.

## What it is not
Not “first come, first served” and not only a product-pricing feature.

## Tradeoffs and failure modes
Policy complexity and occasional underutilization of reserved capacity.

## Where it fits in the overload-control stack
Ingress, scheduler queues, worker pools, and control-plane orchestration.

## Production scenario
Enterprise tenant burst is capped while free-tier and internal control traffic keep minimum guaranteed throughput.

## What to instrument
Throughput by class, starvation incidents, fairness ratio, and reserve utilization.

## Related concepts
- [Load Shedding](load-shedding.md)
- [Multitenant Overload Diagram](../diagrams/multitenant-overload-control.md)

## Closing summary
Fairness is a reliability requirement in multitenant distributed systems.
