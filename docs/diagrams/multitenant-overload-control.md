# Multitenant Overload Control

**Summary:** Diagram and interpretation for multitenant overload control.

```mermaid
flowchart LR
    T1[Tenant A Burst] --> G[Ingress Gateway]
    T2[Tenant B Normal] --> G
    T3[Tenant C Critical] --> G
    G --> L[Per-tenant Limits]
    L --> Q1[Priority Queue: Critical]
    L --> Q2[Priority Queue: Standard]
    L --> Q3[Priority Queue: Background]
    Q1 --> W1[Reserved Workers]
    Q2 --> W2[Shared Workers]
    Q3 --> S[Shed under saturation]
    W1 --> Core[Critical path preserved]
```

## Interpretation
This diagram highlights overload decision points and containment boundaries.

## Related concepts
- [Overload Control Model](../overview/overload-control-model.md)
