# Foundation solution — Shape a secure delivery plan

## Example problem and outcomes

**Problem.** Students and lecturers use disconnected systems for academic
results. Access rules and support evidence are inconsistent, and publication
peaks are difficult to diagnose. Northstar needs one controlled result-viewing
flow that uses institutional identity and can be operated by its small IT team.

Example outcomes:

- at least 95% of pilot students complete result viewing without support;
- automated tests show that cross-student result access is denied in every API path; and
- the service team can identify a failed dependency from telemetry within an agreed exercise target.

The first release includes sign-in, personal result viewing, denial evidence,
and support telemetry. Assignment upload and administrative correction are out
of scope for the first increment.

## Example epic and backlog slice

| ID | Story or enabling item | Dependency | Main risk |
| --- | --- | --- | --- |
| EN-01 | Integrate the non-production institutional identity tenant | Identity team test client | Incorrect token validation |
| US-01 | As a student, I can view my fictional results | EN-01, seeded database | Object-level authorization gap |
| SEC-01 | Deny and test access to another student's result | US-01 | Incomplete endpoint coverage |
| OPS-01 | Correlate a result request across API logs and metrics | Logging platform | Sensitive values in telemetry |
| PERF-01 | Test agreed peak result reads | Stable Test environment | Unrealistic workload model |
| SUP-01 | Return a safe support code on failure | OPS-01 | Support code not searchable |

## Example security acceptance criteria

```gherkin
Given student A has a valid session
And result 124 belongs to student B
When student A requests result 124
Then the API returns no result data
And records a denial event with a correlation identifier
And does not log the result content or access token
```

```gherkin
Given the database is unavailable
When an authenticated student requests their results
Then the API returns a generic service error
And the response contains a support correlation identifier
And no stack trace or connection string is returned
```

## Example threat response

| Threat | Prevent | Detect | Recover | Verify |
| --- | --- | --- | --- | --- |
| ID manipulation | Derive subject from validated identity and authorize the resource | Denial metric and audit event | Review session and affected routes | Cross-account integration tests |
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

Implement sign-in and one `GET /api/me/results` path with seeded fictional data.
Exclude lecturer write, upload, and notifications. The riskiest assumption is
that the identity subject maps reliably to the student record. Evidence includes
token-validation tests, cross-account tests, a small load test, and a correlated
failure response. Stop promotion if authorization tests fail or protected data
appears in logs.
