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

## Closing summary
Isolation converts dependency failures into local degradations rather than systemic outages.
