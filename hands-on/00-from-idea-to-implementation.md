# Foundation Lab — Shape a secure delivery plan

## Goal

Turn the student portal idea into a small, secure, and testable implementation
plan. You will create a problem statement, backlog slice, security acceptance
criteria, DTAP plan, and delivery pipeline.

## Prerequisites

- Complete [From idea to secure implementation](../course/00-from-idea-to-implementation.md).
- Read the [student portal case](../case-study/student-portal.md).
- Create `portfolio/00-idea-to-implementation.md`.

## Part 1 — Define the problem and outcomes

Write:

1. a problem statement of no more than 120 words;
2. three measurable outcomes;
3. explicit in-scope and out-of-scope lists for the first release;
4. five stakeholders, including security/privacy and operations; and
5. four assumptions that require validation.

### Checkpoint 1

At least one outcome measures user success, one measures cybersecurity or
privacy, and one measures operability. None of the outcomes requires a specific
vendor product.

## Part 2 — Create an epic and story map

Create one epic for **secure result viewing**. Split it into at least five user
stories or enabling items covering:

- identity-provider integration;
- authorized result retrieval;
- denial of cross-student access;
- audit evidence and privacy-safe logging;
- performance during publication peak; and
- support or failure handling.

For each item, record value, dependencies, and main risk.

| ID | Story or enabling item | Value | Dependency | Main risk |
| --- | --- | --- | --- | --- |
| US-01 | | | | |

Check whether each user story is reasonably Independent, Negotiable, Valuable,
Estimable, Small, and Testable. Split stories that contain several outcomes.

## Part 3 — Write acceptance criteria

Choose the authorized-result story and write at least eight Given-When-Then
examples covering:

- the authorized happy path;
- unauthenticated access;
- another student's result identifier;
- lecturer access with and without course assignment;
- invalid input;
- identity-provider or database unavailability;
- privacy-safe logging; and
- peak-response measurement.

Do not prescribe UI details unless they are essential to the outcome.

## Part 4 — Add threat-informed requirements

Draw the first data flow for result viewing and mark trust boundaries. Create a
table with at least six threats.

| Threat or abuse case | Affected asset | Prevent | Detect | Recover | Verification |
| --- | --- | --- | --- | --- | --- |
| Student changes a result ID | Academic result | Object-level authorization | Authorization-denial metric and audit event | Investigate and invalidate affected sessions if needed | Cross-account automated test |
| Your threat | | | | | |

Include identity spoofing, tampering, information disclosure, denial of service,
and privilege escalation. Add repudiation if auditability is important.

## Part 5 — Design DTAP

Complete this matrix:

| Topic | Development | Test | Acceptance | Production |
| --- | --- | --- | --- | --- |
| Purpose | | | | |
| Data | | | | |
| Identity provider | | | | |
| Secrets and keys | | | | |
| Deployment permission | | | | |
| Logging access | | | | |
| Scale | | | | |
| Reset or recovery | | | | |

Then answer:

1. Which artefact is promoted between environments?
2. Which configuration changes per environment?
3. How do you prevent production credentials from entering lower environments?
4. Which acceptance difference from production creates the greatest test risk?

## Part 6 — Draw the secure delivery pipeline

Create a pipeline from commit to production. Include:

- peer review;
- build and unit tests;
- secret, dependency, static-code, and infrastructure checks where applicable;
- test deployment and integration tests;
- acceptance and security validation;
- risk-based approval;
- production deployment;
- migration handling;
- post-deployment verification; and
- rollback or forward-fix decision.

For every gate, state what blocks promotion and who can accept an exception.

## Part 7 — Definition of Ready and Done

Write a practical Definition of Ready with five items and Definition of Done with
ten items. Include:

- ownership and acceptance criteria;
- data classification and threat review;
- code and architecture review where needed;
- tests and security findings;
- telemetry and support documentation;
- deployment evidence; and
- no unresolved critical risk without explicit acceptance.

Avoid rules that are impossible to apply to small changes. State which checks
are conditional.

## Part 8 — Plan the first increment

Select the smallest end-to-end slice that proves institutional sign-in and
authorized result access in a non-production environment. Write:

- included stories and excluded features;
- architecture decision still required;
- highest-risk assumption;
- test evidence needed before acceptance;
- operational signal after release; and
- stop or rollback condition.

## Completion checkpoint

- The plan begins with outcomes, not a cloud product.
- Stories include security, failure, and operation, not only the happy-path UI.
- Production data and secrets are absent from lower environments.
- The same traceable artefact is promoted through DTAP where practical.
- Pipeline automation is combined with accountable exception handling.
- The first increment is thin, end to end, and designed to produce learning.

## Deliverables

- problem, outcomes, scope, stakeholders, and assumptions;
- epic and story map;
- acceptance criteria;
- threat and control table;
- DTAP matrix;
- secure delivery pipeline;
- Definitions of Ready and Done; and
- first-increment plan.

Use these artefacts as input to [Lab 1 — Map the system](01-map-the-system.md).
