# Overload Control Pipeline

**Summary:** The overload-control pipeline describes the ordered decision points that keep work bounded from ingress to dependency interactions.

## Pipeline stages
1. Ingress classification
2. Admission control
3. Rate limiting and fairness
4. Backpressure propagation
5. Circuit breaking and isolation
6. Load shedding
7. Graceful degradation

## Implementation note
These stages can be distributed across edge proxies, service code, workers, and control-plane orchestration, but each stage should have clear ownership.

## Related concepts
- [Diagram: Overload Control Pipeline](../diagrams/overload-control-pipeline.md)
- [Admission Control](../concepts/admission-control.md)
- [Graceful Degradation](../concepts/graceful-degradation.md)
