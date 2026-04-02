# Admission Control

**Summary:** Admission control is the explicit accept/reject boundary that prevents a system from ingesting work beyond safe operating limits.

## What it is
A policy and mechanism at ingress (or queue ingestion) that decides whether new work may enter now.

## Why it matters
Without admission, systems accept unlimited work and move failure deeper into queues and dependencies.

## What problem it solves
It prevents overload collapse caused by optimistic acceptance during saturation.

## How it works
Admission evaluates live signals (concurrency saturation, queue depth/age, error rates, reserved capacity) and returns accept, defer, or reject with reason codes.

## What it is not
It is not generic authentication, and it is not equivalent to static per-client rate limiting.

## Tradeoffs and failure modes
Rejecting requests increases short-term error rates and may require client behavior changes. Poor thresholds can underutilize capacity or admit too much during spikes.

## Where it fits in the overload-control stack
Front-door control at API gateways, job ingest endpoints, and internal workflow command submission.

## Production scenario
A customer API spike hits 20x normal QPS. Admission enforces global and per-tenant ceilings, preserving headroom for checkout and reconciliation operations.

## What to instrument
Accept/reject counts by reason, reserved-capacity utilization, queue age at rejection, and admission decision latency.

## Related concepts
- [Rate Limiting](rate-limiting.md)
- [Load Shedding](load-shedding.md)
- [Where to Enforce Admission Control](../design-guides/where-to-enforce-admission-control.md)

## Related reading on myrobertson.com
- [Distributed Systems Writing Hub](https://www.myrobertson.com/blog/)
- [Backpressure in Distributed Systems: Stability, Correctness, and Graceful Degradation](https://www.myrobertson.com/blog/backpressure-stability-correctness-distributed-systems)
- [API Backpressure Explained Simply](https://www.myrobertson.com/blog/api-backpressure-explained-simply)
- [What Is a Control Plane?](https://www.myrobertson.com/blog/what-is-a-control-plane)
- [Architecting a Multitenant Control Plane for a Next-Generation Data Tier](https://www.myrobertson.com/blog/architecting-a-multitenant-control-plane-for-a-next-generation-data-tier)
- [Distributed Systems Case Studies](https://www.myrobertson.com/case-studies/)

## Closing summary
Admission control turns overload from accidental collapse into intentional policy.
