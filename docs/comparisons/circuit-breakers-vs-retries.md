# Circuit Breakers vs Retries

**Summary:** Breakers stop futile calls; retries reattempt failures and can amplify load.

## Definitions of both concepts
See linked concept pages for canonical definitions.

## Core distinction
This page distinguishes decision timing, control objective, and failure behavior under saturation.

## Where they overlap
Both are overload-control mechanisms intended to preserve stability and critical paths.

## Where they differ
They act at different layers and use different signals, policies, and tradeoffs.

## When to use both
Use both in production systems with variable demand and shared dependencies to avoid single-point control assumptions.

## Failure modes when confused
Teams either reject too late, retry too aggressively, or assume one mechanism covers all overload behaviors.

## Related concepts
- [Overload Control Model](../overview/overload-control-model.md)
- [Concepts Index](../concepts)

## Related reading on myrobertson.com
- [Distributed Systems Writing Hub](https://www.myrobertson.com/blog/)
- [Backpressure in Distributed Systems: Stability, Correctness, and Graceful Degradation](https://www.myrobertson.com/blog/backpressure-stability-correctness-distributed-systems)
- [API Backpressure Explained Simply](https://www.myrobertson.com/blog/api-backpressure-explained-simply)
- [What Is a Control Plane?](https://www.myrobertson.com/blog/what-is-a-control-plane)
- [Architecting a Multitenant Control Plane for a Next-Generation Data Tier](https://www.myrobertson.com/blog/architecting-a-multitenant-control-plane-for-a-next-generation-data-tier)
- [Distributed Systems Case Studies](https://www.myrobertson.com/case-studies/)
