# Lab 8 — Capstone architecture and defence

## Goal

Produce, implement, and defend a coherent architecture for a working slice of
the Northstar student portal. The implementation includes a frontend, backend,
API, datastore, automated pipeline, security checks, deployment evidence, and
operational signals. This lab integrates every earlier artefact and includes a
critical review of an AI-generated alternative.

## Prerequisites

- Complete all course modules and Labs 1 through 7.
- Complete the [implementation journey](../course/10-implementation-journey.md).
- Follow the [working end project brief](../project/README.md).
- Read the [assessment rubric](../evaluation/questions-and-rubric.md).
- Create `portfolio/08-capstone.md`.

## Part 1 — Architecture brief

Write no more than two pages covering:

- problem, scope, and stakeholders;
- top five functional requirements;
- five measurable quality scenarios;
- constraints and assumptions;
- proposed architecture in one paragraph; and
- top five risks.

## Part 2 — Required views

Create or refine:

1. system context diagram;
2. container diagram;
3. production deployment diagram;
4. login sequence;
5. assignment-upload sequence; and
6. one result-publication failure sequence.

Every diagram needs a title, scope, useful labels, and accompanying assumptions.

## Part 3 — Security and privacy case

Provide:

- data classification and flow summary;
- trust-boundary diagram;
- least-privilege matrix;
- ten security controls with verification evidence;
- privacy-safe logging rules; and
- three residual risks requiring owner acceptance.

## Part 4 — Reliability and operations case

Define:

- critical user journeys and service indicators;
- proposed service objectives for stakeholder discussion;
- RTO and RPO proposals for results and assignments;
- scaling signals and bottleneck tests;
- minimal dashboards and actionable alerts;
- backup and restore validation; and
- incident ownership and escalation.

## Part 5 — Delivery and cost

Show:

- DTAP boundaries and promotion path;
- secure delivery pipeline;
- database-change strategy;
- production release and recovery approach;
- major cost drivers; and
- ownership for platform, application, data, identity, and operations.

## Part 6 — Decisions and trade-offs

Document at least three significant decisions. One must be a complete ADR. For
each decision, include alternatives, benefits, disadvantages, evidence, and a
review trigger.

## Part 7 — Critical AI review

Ask an approved AI tool for an alternative architecture, or use an
instructor-provided proposal. Preserve the prompt and output according to course
policy, excluding sensitive data.

Review at least:

- invented or hidden assumptions;
- unnecessary components;
- missing security boundaries;
- inconsistent data ownership;
- unsupported scale or availability claims;
- operational skills and costs;
- failure and recovery gaps;
- outdated or unverified technical claims; and
- conflict with the case constraints.

Create a decision log of what you accepted, changed, and rejected. Verify factual
claims with primary documentation or tests.

## Part 8 — Traceability

For every top requirement, map:

| Requirement | Design response | Diagram or ADR | Test evidence | Operational signal | Remaining risk |
| --- | --- | --- | --- | --- | --- |
| Your requirement | | | | | |

Remove unjustified components and address requirements without a design response.

## Part 9 — Oral defence

Prepare a ten-minute presentation and a ten-minute question period. You must be
able to explain:

- every component and relationship;
- one successful and one failed end-to-end flow;
- the highest security and availability risks;
- why the selected deployment option fits the actual team;
- which assumption is most dangerous; and
- what you would validate before approving implementation.

## Part 10 — Working implementation evidence

Demonstrate the implemented vertical slice rather than a mock-up only:

- a browser-based frontend performs at least one authenticated read and one
  validated write through the backend API;
- the backend enforces authorization and does not trust client-supplied identity;
- persistent data survives an application restart;
- automated unit and integration tests cover success and negative security paths;
- a pipeline builds, tests, scans, packages, and promotes a traceable artefact;
- at least Development, Test, and a controlled Acceptance or Production-like
  environment have separated configuration and credentials;
- telemetry shows request outcome, latency, and a correlation identifier without
  leaking secrets; and
- the team demonstrates a failed deployment or dependency scenario and recovery.

Use the [end project rubric](../project/rubric.md) for implementation assessment.

## Completion checkpoint

- All views use consistent names and responsibilities.
- Every major component maps to a requirement.
- Security includes object-level authorization, not only login and TLS.
- Reliability includes recovery tests, not only redundant components.
- DTAP and delivery controls protect secrets, data, and production change.
- AI output is treated as an unverified proposal.
- The design is simple enough for the stated team or explicitly justifies added complexity.

## Deliverables

Submit the architecture brief, diagrams, security case, reliability case,
delivery plan, cost drivers, decisions, AI review, traceability table, and oral
defence notes as one navigable portfolio.

Use the [rubric](../evaluation/questions-and-rubric.md) for final self-assessment.
