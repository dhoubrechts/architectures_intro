# End project rubric

## Assessment matrix

| Criterion | Weight | Pass evidence | Strong evidence |
| --- | ---: | --- | --- |
| Working vertical slice | 15% | Wireframes lead to a working frontend, backend, data, logbook, document, and review journey | Clear multi-role states, accessible interaction, and consistent API behaviour |
| Architecture and traceability | 15% | Required views and ADRs match implementation | Requirements, tests, deployments, and signals are linked and current |
| Identity and authorization | 15% | Approved authentication plus role, assignment, object, and state checks | Thorough student, supervisor, and mentor negative tests, least privilege, and clear trust boundaries |
| Secure implementation | 10% | Validation, safe data access, secrets, and errors are addressed | Threat-informed controls are automated and residual risks are explicit |
| Tests and quality | 10% | Unit and integration tests cover critical paths | Contract, migration, failure, and security tests prevent regressions |
| Pipeline and DTAP | 15% | Automated build, tests, scans, packaging, and controlled promotion | Same traceable artefact, protected credentials, gate policy, and deployment verification |
| Reliability and observability | 10% | Health, logs, metrics, backup/rebuild, and failure exercise exist | User-focused indicators, actionable alert, correlation, and measured recovery |
| Defence and teamwork | 10% | Team explains choices and contributions | Evidence-led trade-offs, honest limitations, and disciplined AI review |

## Critical conditions

The project cannot pass while any of these conditions remains:

- a student can access another student's dossier, document, feedback, or logbook by changing an identifier;
- a workplace mentor can access a student who is not currently assigned to them;
- real credentials or personal data are committed;
- the frontend connects directly to the database with privileged credentials;
- pipeline or deployment evidence is fabricated or replaced by screenshots without source;
- critical security findings are hidden rather than corrected or explicitly accepted by the authorised owner;
- the submitted application cannot be reproduced from the repository instructions; or
- the team cannot explain the code, configuration, or diagrams it submits.

## Individual verification

Every student must independently explain one end-to-end request, one security
control, one pipeline gate, one failure diagnosis, and one architecture trade-off.
Group output does not replace individual understanding.

## Stretch work

Stretch work is considered only after the minimum slice is reliable and secure:

- asynchronous document scanning with idempotent processing;
- configurable process templates or advanced assessment forms;
- OpenID Connect integration with an instructor-approved provider;
- infrastructure as code and policy checks;
- software bill of materials and artefact signing;
- canary or blue-green release;
- distributed tracing; or
- measured load and recovery experiments.

Complexity without a requirement, test, owner, and operational plan does not earn extra credit.
