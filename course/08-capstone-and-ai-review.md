# Module 8 — Capstone and critical AI review

**Estimated study time:** 60 minutes plus the capstone project

## Learning objectives

After this module, you can:

- integrate requirements, application design, infrastructure, security, and operations;
- trace decisions from stakeholder need to evidence;
- review architecture for gaps and contradictions;
- use AI to generate hypotheses without outsourcing accountability; and
- prepare a concise architecture defence.

## Prerequisites

Complete Modules 1 through 7 and their labs. Review the complete
[student portal case](../case-study/student-portal.md).

## Integration before optimisation

A capstone architecture must tell one coherent story:

```text
Actors and needs
-> measurable requirements and constraints
-> responsibilities and boundaries
-> runtime interactions and data ownership
-> deployment and delivery
-> security and privacy controls
-> failure, recovery, and observability
-> decisions, consequences, and evidence
```

A polished diagram is insufficient if these parts contradict one another. For
example, a design that promises independent regional operation but depends on
one identity provider in one region has an unresolved availability dependency.

## Requirement traceability

Create a lightweight traceability table:

| Requirement | Design response | Verification evidence | Remaining risk |
| --- | --- | --- | --- |
| Students see only their own results | Subject-to-resource authorization in API | Cross-account access tests and audit events | Incorrect enrolment source data |
| Upload peaks do not overload API memory | Direct object-storage upload with bounded size | Peak test, storage metrics, expired-link test | Storage-provider outage |
| Small team operates the service | Managed runtime and database | Recovery exercise and on-call review | Provider-specific expertise |

Traceability exposes components with no justification and requirements with no
design response.

## Review from several perspectives

### Functional review

- Are every actor's authorised journeys supported?
- Are error and alternate flows defined?
- Is the source of truth clear for each important record?

### Security and privacy review

- Where does identity enter, change, or become a service identity?
- Is object-level authorization enforced for results and submissions?
- Which data appears in URLs, logs, caches, backups, and non-production?
- Which controls are preventive, detective, and corrective?

### Reliability review

- Which dependency can stop each critical journey?
- Do timeouts, retries, and queues limit or amplify failure?
- Can the team restore data and service within agreed objectives?
- Do alerts reflect user impact?

### Delivery and operations review

- How does a tested artefact reach production?
- How are schema changes sequenced and recovered?
- Who owns each component and incident decision?
- Is the design operable by the actual team?

### Cost and simplicity review

- Which component adds the most operational complexity?
- Can one component safely perform two responsibilities at this scale?
- Which costs grow with users, traffic, storage, or telemetry?
- What could be removed without violating a requirement?

## AI as a sparring partner

AI can help generate alternatives, failure hypotheses, stakeholder questions,
or review checklists. Its output is not evidence. Models can invent requirements,
misapply patterns, omit inconvenient trade-offs, use outdated product details,
or produce internally inconsistent diagrams.

Use a disciplined process:

1. Provide the case, constraints, and required output.
2. Ask for assumptions and alternatives, not one “best” answer.
3. Separate factual claims from design suggestions.
4. Verify technical claims with primary documentation and tests.
5. Map every suggested component to a requirement.
6. Identify new failure modes, skills, cost, and security boundaries.
7. Keep a short decision log of what you accepted, changed, or rejected and why.

### Example review

An AI proposes a separate login service, API gateway, five microservices,
Kubernetes, a service mesh, three databases, a queue, and two load balancers.

Ask:

- Why add a login service if the existing identity provider already authenticates users?
- Which services require independent scaling or release?
- Who operates the cluster and mesh?
- Which consistency problems follow from three databases?
- Which measured load requires this topology?
- What simpler baseline meets the same requirements?

Complexity is justified only when its benefit exceeds its cost and risk in this
context.

## Architecture defence

Prepare a ten-minute explanation:

1. problem, scope, assumptions, and top quality drivers;
2. context and main containers;
3. login, result-viewing, and upload flows;
4. security boundaries and controls;
5. deployment, scaling, recovery, and observability;
6. three trade-offs and the most important ADR; and
7. remaining risks and next validation steps.

Expect the assessor to point at any box or arrow. If you cannot explain its
requirement, responsibility, failure behaviour, and evidence, the design is not
finished.

## Final self-check

- Every major component has a requirement and owner.
- Every sensitive flow has identity, authorization, and data-protection decisions.
- Every critical journey has failure and recovery reasoning.
- Diagrams agree on names, relationships, and boundaries.
- Assumptions are visible and have validation plans.
- Major choices include alternatives and negative consequences.
- AI suggestions are labelled, checked, and either justified or rejected.
- The design can be explained without reading an AI response or hidden notes.

## Summary

- A good architecture is coherent across requirements, views, operations, and decisions.
- Traceability connects claims to design responses and evidence.
- Reviews need functional, security, reliability, delivery, and cost perspectives.
- AI expands the option space but cannot own requirements, evidence, or accountability.
- The final test is whether you can defend every important choice and uncertainty.

Complete [Lab 8 — Capstone](../hands-on/08-capstone.md) and use the
[assessment rubric](../evaluation/questions-and-rubric.md).
