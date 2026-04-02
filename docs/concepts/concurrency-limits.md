# Concurrency Limits

**Summary:** Concurrency limits bound simultaneous in-flight work so services do not exceed CPU, memory, or dependency capacity.

## What it is
Upper bounds on active requests, jobs, or dependency calls.

## Why it matters
Throughput plateaus while latency and resource contention can rise sharply beyond an optimal concurrency point.

## What problem it solves
Prevents thread-pool exhaustion and timeout cascades from excessive parallelism.

## How it works
Use permits/semaphores and adaptive algorithms to keep concurrent work near stable operating points.

## What it is not
Not equivalent to per-second rate limits or autoscaling alone.

## Tradeoffs and failure modes
Can reduce peak throughput if tuned too low; too high causes collapse.

## Where it fits in the overload-control stack
Ingress handlers, worker executors, and dependency client pools.

## Production scenario
API service caps DB-bound operations to preserve headroom for critical writes during read storm.

## What to instrument
Permit utilization, wait time for permits, and latency vs concurrency curves.

## Related concepts
- [Rate Limiting](rate-limiting.md)
- [Backpressure](backpressure.md)

## Closing summary
Concurrency controls keep systems in a stable throughput regime.
