# End project — Working student portal slice

## Project outcome

Build, deliver, and defend a working vertical slice of the Northstar student
portal. The result must include a browser frontend, backend API, persistent data,
automated tests, a secure delivery pipeline, separated environments,
local containers, an externally accessible cloud environment, cybersecurity
controls, observability, and architecture documentation.

This is not a full student information system. Use fictional users and data.
The purpose is to prove that architecture decisions survive implementation.

## Minimum functional scope

Implement these journeys:

1. A student signs in through an instructor-approved identity mechanism.
2. The student views only their own fictional results.
3. An authorized lecturer creates or updates a fictional result, or an
   administrator publishes a fictional notification.
4. An unauthorized user receives a safe denial.
5. The frontend displays loading, empty, validation, forbidden, and service-failure states.

Optional extension: assignment upload through object storage and asynchronous
malware-scan simulation. Do not add it until the minimum slice is complete.

## Required technical parts

### Frontend

- Runs in a browser and communicates with the backend over HTTP.
- Does not store a database credential or trust a client-supplied role.
- Performs usability validation and handles API errors safely.
- Has automated tests for at least one success and three failure states.

### Backend

- Exposes a documented API.
- Validates all untrusted input on the server.
- Establishes identity through an approved library or provider.
- Enforces role and object-level authorization.
- Uses parameterized data access or an approved data-access library.
- Returns consistent error responses without stack traces or secret data.
- Produces structured, privacy-aware logs and correlation identifiers.

### Data

- Uses a versioned schema and repeatable migrations.
- Contains synthetic seed data only.
- Persists across application restarts.
- Documents ownership, retention, backup, and restore.

### Deployment

- Packages frontend and backend as separate reproducible container images.
- Runs frontend, backend, and a local test datastore together through a compose
  file or equivalent.
- Keeps configuration outside the built artefact where practical.
- Injects secrets through an approved environment mechanism.
- Separates at least Development, Test, and Acceptance or Production-like environments.
- Pushes scanned, versioned images to an approved registry.
- Deploys the same image versions to an instructor-approved cloud environment.
- Exposes only the application through HTTPS for authorised external reviewers;
  the datastore is not public.
- Records deployed version and post-deployment verification.

Follow the [cloud deployment requirements](cloud-deployment-requirements.md).

## Pipeline requirements

The automated pipeline must visibly perform applicable stages:

1. validate formatting and lint rules;
2. run frontend and backend unit tests;
3. run API or integration tests with a temporary safe database;
4. scan for committed secrets;
5. inspect third-party dependencies and licences;
6. run static security analysis;
7. inspect infrastructure or container configuration when used;
8. build and version the deployable artefact;
9. deploy to Test and run smoke and negative authorization tests;
10. promote the same artefact to Acceptance after approval;
11. verify health and one critical user journey; and
12. preserve test, scan, and deployment evidence.

Document blocking thresholds and the exception owner. Protected environment
credentials must not be exposed to untrusted code or ordinary pull requests.

## Mandatory cybersecurity evidence

- data classification and trust-boundary diagram;
- threat model with at least ten abuse cases;
- automated cross-account authorization tests;
- server-side input-validation tests;
- secret and dependency scan results;
- least-privilege identities for application, migration, and pipeline;
- privacy-safe logging review;
- backup or rebuild and restore exercise;
- dependency or database failure exercise; and
- residual-risk register with owners.

## Architecture evidence

- problem statement, scope, assumptions, and measurable quality scenarios;
- context, container, deployment, and two sequence diagrams;
- API contract and data model;
- DTAP and pipeline diagram;
- at least three ADRs;
- traceability from requirements to tests and operational signals;
- operational runbook; and
- AI proposal review with verified accept/reject decisions.

## Gradual milestones

| Milestone | Working demonstration | Architecture or security evidence |
| --- | --- | --- |
| 0 — Workspace | Frontend calls backend health endpoint | Repository rules, setup, scope |
| 1 — Read | Student sees seeded results | API contract, data flow, cross-account test |
| 2 — Write | Authorized role performs one validated write | Authorization matrix, audit event, negative tests |
| 3 — Local containers | Frontend, backend, and test datastore run with one documented command | Container diagram, network and secret model, image inventory |
| 4 — Pipeline | Quality and security gates run automatically | Gate policy and exception process |
| 5 — DTAP and cloud | Scanned image versions move from local/Test to cloud Acceptance | Environment matrix, HTTPS and access evidence, image digests |
| 6 — Operate | Dashboard and controlled failure exercise | Runbook, restore result, incident timeline |
| 7 — Defend | End-to-end demo and oral defence | Updated views, ADRs, traceability, residual risks |

Each milestone must work before the team adds the next layer. A team may not
replace missing functionality with slides or unverified AI-generated code.

## Team practice

- Keep changes small and reviewable.
- Require peer review before merging.
- Link each change to a story, defect, risk, or technical item.
- Record decisions that affect architecture, security, data, or operations.
- Keep the default branch buildable.
- Never place real secrets or personal data in the repository.
- Declare AI assistance according to instructor policy and review every generated change.

## Demonstration script

The final demonstration should show:

1. repository and pipeline status;
2. deployment version in the selected environment;
3. successful student read;
4. blocked cross-student read;
5. successful authorized write and blocked unauthorized write;
6. validation failure without server information leakage;
7. correlated frontend request, backend log, metric, and audit event;
8. controlled dependency failure and recovery; and
9. the diagram and ADR that explain the implemented choice.

## Submission

Submit the source repository, pipeline definitions, deployment evidence,
architecture portfolio, test and scan reports, threat model, runbook, and a short
recorded or live demonstration. Use the [project rubric](rubric.md).
