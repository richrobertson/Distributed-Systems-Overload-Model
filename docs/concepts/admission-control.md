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

## Closing summary
Admission control turns overload from accidental collapse into intentional policy.
