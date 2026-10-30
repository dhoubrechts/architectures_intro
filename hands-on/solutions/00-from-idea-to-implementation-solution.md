# Foundation solution — Shape a secure delivery plan

## Example problem and outcomes

**Problem.** Students, academic supervisors, workplace mentors, and coordinators
use disconnected email, spreadsheets, folders, and forms. Access rules,
progress status, and support evidence are inconsistent. Northstar needs one
controlled workplace-learning flow that can be operated by its small IT team.

Example outcomes:

- at least 95% of pilot students can find their next required internship action without support;
- automated tests show that cross-dossier and unassigned-mentor access is denied in every API path; and
- the service team can identify a failed dependency from telemetry within an agreed exercise target.

The first release includes sign-in, personal dossier viewing, one logbook
submission and mentor-review flow, denial evidence, and support telemetry.
Advanced matching and final assessment are out of scope for the first increment.

## Example epic and backlog slice

| ID | Story or enabling item | Dependency | Main risk |
| --- | --- | --- | --- |
| EN-01 | Integrate the non-production institutional identity tenant | Identity team test client | Incorrect token validation |
| US-01 | As a student, I can view my fictional internship dossier and next action | EN-01, seeded database | Dossier authorization gap |
| US-02 | As a workplace mentor, I can review an assigned student's logbook | US-01, active assignment | Stale mentor assignment |
| SEC-01 | Deny and test access to an unassigned dossier | US-01 | Incomplete endpoint coverage |
| OPS-01 | Correlate a dossier request across API logs and metrics | Logging platform | Sensitive values in telemetry |
| PERF-01 | Test agreed deadline-peak dashboard reads | Stable Test environment | Unrealistic workload model |
| SUP-01 | Return a safe support code on failure | OPS-01 | Support code not searchable |

## Example student wireframe

```text
+--------------------------------------------------------------+
| Workplace Learning Hub                   Student | Sign out  |
+--------------------------------------------------------------+
| Placement: Example Lab     Phase: Active       Progress 42%  |
| Academic supervisor: A. Example  Mentor: W. Example          |
+--------------------------------------------------------------+
| Next actions                                                 |
| [Submit week 4 logbook]     Due Friday                       |
| [Upload progress document]  Not started                      |
+--------------------------------------------------------------+
| Recent feedback: Week 3 logbook approved                     |
+--------------------------------------------------------------+
```

The student wireframe implies a dossier-summary read, logbook write, document
workflow, and authorization based on the signed-in student's dossier. Mentor and
academic-supervisor versions must show only assigned dossiers and permitted actions.

## Example security acceptance criteria

```gherkin
Given workplace mentor A has a valid session
And dossier 124 is assigned to workplace mentor B
When workplace mentor A requests dossier 124
Then the API returns no dossier data
And records a denial event with a correlation identifier
And does not log dossier content or the access token
```

```gherkin
Given the database is unavailable
When an authenticated student requests their internship dossier
Then the API returns a generic service error
And the response contains a support correlation identifier
And no stack trace or connection string is returned
```

## Example threat response

| Threat | Prevent | Detect | Recover | Verify |
| --- | --- | --- | --- | --- |
| ID manipulation | Derive subject from validated identity and authorize role, assignment, resource, and state | Denial metric and audit event | Review session and affected routes | Cross-dossier and unassigned-mentor tests |
| Token theft | Protected transport, safe token storage, short lifetime | Suspicious session and auth events | Revoke session or client credentials | Browser and log review |
| Query flood | Rate and concurrency limits; efficient query | Request, latency, and pool metrics | Reduce traffic or disable expensive feature | Controlled load test |
| Log disclosure | Structured allow-list logging and redaction | Log-content test and access audit | Remove access and purge according to policy | Automated token-pattern test |

## Example DTAP choices

| Topic | Development | Test | Acceptance | Production |
| --- | --- | --- | --- | --- |
| Data | Local synthetic seed | Repeatable synthetic fixtures | Representative synthetic data | Real classified data |
| Identity | Developer test identities | Automated test identities | Business pilot identities | Institutional identities |
| Secrets | Local approved store | Test secret scope | Separate acceptance scope | Production-only scope |
| Changes | Developer run | Pipeline only | Pipeline plus approval | Pipeline plus authorised approval |

The versioned frontend and backend artefacts are promoted. Endpoints, connection
settings, feature flags, and secret references vary by environment.

## Example first increment

Implement sign-in and one `GET /api/me/dossier` path with seeded fictional data,
then a thin logbook submission. Exclude document review, matching, and final
assessment. The riskiest assumption is that identity and current role assignment
map reliably to the dossier. Evidence includes token validation, cross-dossier
and unassigned-mentor tests, a small load test, and a correlated failure response.
Stop promotion if authorization tests fail or protected data appears in logs.
