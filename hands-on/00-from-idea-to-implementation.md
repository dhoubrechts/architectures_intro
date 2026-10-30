# Foundation Lab — Shape a secure delivery plan

## Goal

Turn the workplace learning platform idea into a small, secure, and testable
implementation plan. You will create a problem statement, backlog slice,
role-based wireframes, security acceptance criteria, DTAP plan, and delivery pipeline.

## Prerequisites

- Complete [From idea to secure implementation](../course/00-from-idea-to-implementation.md).
- Read the [workplace learning case](../case-study/workplace-learning-platform.md).
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

Create one epic for **internship progress and logbook management**. Split it into at least six user
stories or enabling items covering:

- identity-provider integration;
- the student's own dossier and current phase;
- logbook or hour submission;
- approval by the assigned workplace mentor;
- progress review by the assigned academic supervisor;
- denial of cross-student and unassigned-mentor access;
- audit evidence and privacy-safe logging;
- performance during a deadline peak; and
- support or failure handling.

For each item, record value, dependencies, and main risk.

| ID | Story or enabling item | Value | Dependency | Main risk |
| --- | --- | --- | --- | --- |
| US-01 | | | | |

Check whether each user story is reasonably Independent, Negotiable, Valuable,
Estimable, Small, and Testable. Split stories that contain several outcomes.

## Part 3 — Create simple role-based wireframes

Create low-fidelity wireframes for:

1. a student dashboard showing placement, phase, progress, next actions, recent
   feedback, and logbook status;
2. an academic-supervisor dashboard showing assigned students and reviews due; and
3. a workplace-mentor view showing only assigned interns, submitted hours, and
   permitted approval actions.

Use paper, a simple diagramming tool, or text boxes. Do not spend time on final
colours, branding, or pixel-perfect layout.

For each wireframe, include variants for loading, empty, validation failure,
permission denied, and dependency failure. Annotate at least five elements with:

| Wireframe element | User story | API or data need | Authorization or privacy question |
| --- | --- | --- | --- |
| Current phase | Student understands progress | Dossier summary | May this identity see this dossier? |
| Your element | | | |

Use fictional identities and data. Do not include screenshots or personal data
from a real workplace learning platform.

## Part 4 — Write acceptance criteria

Choose the logbook submission and review stories and write at least ten Given-When-Then
examples covering:

- student submission and assigned-mentor approval;
- unauthenticated access;
- another student's dossier identifier;
- workplace-mentor access with and without a current assignment;
- academic-supervisor review with and without assignment;
- an invalid or repeated workflow transition;
- invalid input;
- identity-provider or database unavailability;
- privacy-safe logging; and
- deadline-peak response measurement.

Do not prescribe UI details unless they are essential to the outcome.

## Part 5 — Add threat-informed requirements

Draw the first data flow for dossier and logbook review and mark trust
boundaries. Create a table with at least eight threats.

| Threat or abuse case | Affected asset | Prevent | Detect | Recover | Verification |
| --- | --- | --- | --- | --- | --- |
| Student changes a dossier ID | Internship dossier | Role, assignment, and object authorization | Authorization-denial metric and audit event | Investigate and invalidate affected sessions if needed | Cross-dossier automated test |
| Your threat | | | | | |

Include identity spoofing, tampering, information disclosure, denial of service,
and privilege escalation. Add repudiation if auditability is important.

## Part 6 — Design DTAP

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

## Part 7 — Draw the secure delivery pipeline

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

## Part 8 — Definition of Ready and Done

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

## Part 9 — Plan the first increment

Select the smallest end-to-end slice that proves institutional sign-in and
authorized access to one fictional internship dossier in a non-production
environment. The slice should show the current phase and one logbook action. Write:

- included stories and excluded features;
- architecture decision still required;
- highest-risk assumption;
- test evidence needed before acceptance;
- operational signal after release; and
- stop or rollback condition.

## Completion checkpoint

- The plan begins with outcomes, not a cloud product.
- Stories include security, failure, and operation, not only the happy-path UI.
- Wireframes expose role differences, non-happy states, and implied API needs.
- Production data and secrets are absent from lower environments.
- The same traceable artefact is promoted through DTAP where practical.
- Pipeline automation is combined with accountable exception handling.
- The first increment is thin, end to end, and designed to produce learning.

## Deliverables

- problem, outcomes, scope, stakeholders, and assumptions;
- epic and story map;
- three role-based wireframes and annotations;
- acceptance criteria;
- threat and control table;
- DTAP matrix;
- secure delivery pipeline;
- Definitions of Ready and Done; and
- first-increment plan.

Use these artefacts as input to [Lab 1 — Map the system](01-map-the-system.md).
