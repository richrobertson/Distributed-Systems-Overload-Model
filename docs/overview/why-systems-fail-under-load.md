# Why Systems Fail Under Load

**Summary:** Distributed systems usually fail as a chain reaction of latency, queueing, retries, and resource contention after safe limits are crossed.

## Failure progression
1. Demand exceeds effective processing capacity.
2. Queue depth and in-flight work increase.
3. Latency rises; clients hit deadlines.
4. Retries add additional traffic.
5. Dependencies saturate and timeout.
6. Control-plane operations stall; recovery slows.

## Why this is systemic
The failure is produced by interactions across APIs, queues, workers, dependencies, and clients. No single layer can solve it alone.

## Common amplification vectors
- Unbounded work queues
- Aggressive client retries without backoff
- Shared worker pools without isolation
- Global caches under invalidation storms
- Long timeout chains across many hops

## Related concepts
- [Overload Control Model](overload-control-model.md)
- [Retries and Retry Storms](../concepts/retries-and-retry-storms.md)
- [Bounded Queues](../concepts/bounded-queues.md)

## Related reading on myrobertson.com
- [Distributed Systems Writing Hub](https://www.myrobertson.com/blog/)
- [Backpressure in Distributed Systems: Stability, Correctness, and Graceful Degradation](https://www.myrobertson.com/blog/backpressure-stability-correctness-distributed-systems)
- [API Backpressure Explained Simply](https://www.myrobertson.com/blog/api-backpressure-explained-simply)
- [What Is a Control Plane?](https://www.myrobertson.com/blog/what-is-a-control-plane)
- [Architecting a Multitenant Control Plane for a Next-Generation Data Tier](https://www.myrobertson.com/blog/architecting-a-multitenant-control-plane-for-a-next-generation-data-tier)
- [Distributed Systems Case Studies](https://www.myrobertson.com/case-studies/)
