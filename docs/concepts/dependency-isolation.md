# Dependency Isolation

**Summary:** Dependency isolation prevents one unhealthy downstream from exhausting shared resources needed by other critical paths.

## What it is
Separating connection pools, worker pools, budgets, and timeout domains per dependency or dependency class.

## Why it matters
Shared pools let a single failing dependency consume global capacity.

## What problem it solves
Stops cross-contamination between healthy and unhealthy call paths.

## How it works
Per-dependency bulkheads, timeout budgets, and independent breaker states limit blast radius.

## What it is not
Not merely code modularity or microservice decomposition.

## Tradeoffs and failure modes
Higher operational overhead and potential idle capacity fragmentation.

## Where it fits in the overload-control stack
At service edges where multiple downstreams are called concurrently.

## Production scenario
Identity provider latency spike isolated from billing provider calls, preserving checkout authorization.

## What to instrument
Pool saturation by dependency, breaker open time per dependency, and cross-path latency correlation.

## Related concepts
- [Bulkheads](bulkheads.md)
- [Dependency Failure Diagram](../diagrams/dependency-failure-containment.md)

## Related reading on myrobertson.com
- [Distributed Systems Writing Hub](https://www.myrobertson.com/blog/)
- [Backpressure in Distributed Systems: Stability, Correctness, and Graceful Degradation](https://www.myrobertson.com/blog/backpressure-stability-correctness-distributed-systems)
- [API Backpressure Explained Simply](https://www.myrobertson.com/blog/api-backpressure-explained-simply)
- [What Is a Control Plane?](https://www.myrobertson.com/blog/what-is-a-control-plane)
- [Architecting a Multitenant Control Plane for a Next-Generation Data Tier](https://www.myrobertson.com/blog/architecting-a-multitenant-control-plane-for-a-next-generation-data-tier)
- [Distributed Systems Case Studies](https://www.myrobertson.com/case-studies/)

## Closing summary
Isolation converts dependency failures into local degradations rather than systemic outages.
