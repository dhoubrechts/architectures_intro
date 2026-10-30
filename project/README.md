# End project — Working workplace learning platform

## Project outcome

Build, deliver, and defend a working vertical slice of the fictional **Northstar
Workplace Learning Hub**. The application supports collaboration between a
student, academic supervisor, workplace mentor, and internship coordinator.

The result must include a browser frontend, backend API, persistent data,
document storage, automated tests, local Docker containers, a secure delivery pipeline,
separated environments, an externally accessible cloud deployment,
cybersecurity controls, observability, and architecture documentation.

This is not a copy of OnStage and not a complete internship administration
system. Use fictional users, organisations, placements, logbooks, reviews, and
documents. The purpose is to prove that architecture decisions survive
implementation.

## Minimum functional scope

Implement these end-to-end journeys:

1. A user signs in through an instructor-approved identity mechanism.
2. A student views their own internship dossier, current phase, assigned
   supervisors, required activities, and progress.
3. The student creates and submits a logbook or hour entry.
4. The assigned workplace mentor approves the entry or returns it with feedback.
5. The student uploads a document to a dossier activity and sees its processing
   and review status.
6. The assigned academic supervisor reviews the document or progress milestone
   and records feedback.
7. The internship coordinator can monitor workflow status and reassign a
   supervisor through an audited action.
8. A user without a current dossier assignment receives a safe denial.

Optional extensions include placement matching, agreements, integrated
messaging, advanced assessment forms, emergency-location support, and SIS
integration. Do not add them until the minimum slice is reliable and secure.

## Required domain model

At minimum, model:

- user and role assignment;
- organisation and workplace;
- internship dossier and placement period;
- process phase and required activity;
- student logbook or hour entry;
- approval or review with feedback;
- document metadata and version;
- notification; and
- audit event.

Authorization must combine identity, role, current dossier assignment, action,
and resource state. A generic `mentor` role must not grant access to every student.

## Required technical parts

### Frontend

- Runs in a browser and communicates with the backend over HTTP.
- Presents a role-appropriate dashboard and dossier detail.
- Does not store database credentials or trust a client-supplied role or user ID.
- Handles loading, empty, validation, forbidden, conflict, and service-failure states.
- Has automated tests for at least one successful journey and four failure states.

### Backend

- Exposes a documented API for dossiers, activities, logbook entries, documents,
  reviews, and workflow status.
- Validates all untrusted input on the server.
- Establishes identity through an approved library or provider.
- Enforces role, assignment, object, and state-based authorization.
- Uses parameterized data access or an approved data-access library.
- Protects workflow transitions against invalid or repeated actions.
- Returns consistent error responses without stack traces or secret data.
- Produces structured, privacy-aware logs and correlation identifiers.

### Data and documents

- Uses a versioned schema and repeatable migrations.
- Contains synthetic seed data only.
- Persists across application restarts.
- Stores document bytes outside ordinary relational rows where appropriate and
  keeps metadata, ownership, version, and status in the database.
- Validates size and permitted type on the server.
- Applies an instructor-approved malware-scan service or safe scan simulation
  before a document becomes available to reviewers.
- Documents retention, archive, controlled deletion, backup, and restore.

### Deployment

- Packages frontend and backend as separate reproducible Docker images using
  versioned Dockerfiles.
- Runs frontend, backend, datastore, and local object-storage or scan substitute
  through Docker Compose.
- Keeps configuration outside the built artefact where practical.
- Injects secrets through an approved environment mechanism.
- Separates at least Development, Test, and Acceptance or Production-like environments.
- Pushes scanned, versioned images to an approved registry.
- Deploys the same image versions to an instructor-approved cloud environment.
- Exposes only the application through HTTPS for authorised external users;
  data stores, debug ports, and management surfaces are not public.
- Records deployed version and post-deployment verification.

Follow the [cloud deployment requirements](cloud-deployment-requirements.md).

## Pipeline requirements

The automated pipeline must visibly perform applicable stages:

1. validate formatting and lint rules;
2. run frontend and backend unit tests;
3. run API, workflow, migration, and integration tests with safe temporary services;
4. scan for committed secrets;
5. inspect third-party dependencies and licences;
6. run static security analysis;
7. inspect infrastructure and container configuration;
8. build, scan, inventory, and version the deployable images;
9. deploy to Test and run smoke, workflow, and negative authorization tests;
10. promote the same images to Acceptance after approval;
11. verify HTTPS, identity, health, document processing, and one critical journey; and
12. preserve test, scan, and deployment evidence.

Document blocking thresholds and the exception owner. Protected environment
credentials must not be exposed to untrusted code or ordinary pull requests.

## Mandatory cybersecurity evidence

- data classification and trust-boundary diagram;
- threat model with at least twelve abuse cases;
- automated tests proving a student cannot access another dossier;
- automated tests proving a workplace mentor sees only assigned interns;
- automated tests for invalid workflow transitions and document access;
- server-side input and upload validation tests;
- secret, dependency, code, configuration, and image scan results;
- least-privilege identities for application, migration, pipeline, and document worker;
- privacy-safe logging and screenshot review;
- backup or rebuild and restore exercise;
- dependency, datastore, or document-processing failure exercise; and
- residual-risk register with owners.

## Architecture evidence

- problem statement, scope, actors, assumptions, and measurable quality scenarios;
- low-fidelity wireframes for student, academic-supervisor, workplace-mentor,
  and coordinator views, plus selected visual mock-ups;
- context, container, deployment, data-flow, and sequence diagrams;
- API contract, workflow state model, and data model;
- DTAP and pipeline diagram;
- at least three ADRs;
- traceability from requirements to tests and operational signals;
- operational runbook; and
- AI proposal review with verified accept, change, or reject decisions.

## Gradual milestones

| Milestone | Working demonstration | Architecture or security evidence |
| --- | --- | --- |
| 0 — Discovery | Role journeys, wireframes, and frontend shell | Repository rules, setup, actors, scope, privacy review |
| 1 — Dossier read | Student sees a seeded dossier and phase | API contract, data flow, cross-dossier denial |
| 2 — Logbook workflow | Student submits and assigned mentor reviews an entry | State model, assignment authorization, audit event |
| 3 — Document workflow | Student uploads and supervisor reviews an accepted document | Object storage, scan status, access and retention rules |
| 4 — Local containers | Complete slice runs with one documented command | Container diagram, network and secret model, image inventory |
| 5 — Pipeline | Quality and security gates run automatically | Gate policy and exception process |
| 6 — DTAP and cloud | Approved images move from local/Test to cloud Acceptance | Environment matrix, HTTPS and external-role evidence, image digests |
| 7 — Operate | Dashboard and controlled failure exercise | Runbook, restore evidence, incident timeline |
| 8 — Defend | End-to-end multi-role demo and oral defence | Updated views, ADRs, traceability, residual risks |

Each milestone must work before the team adds the next layer. A team may not
replace missing functionality with slides, static mock-ups, or unverified
AI-generated code.

## Team practice

- Keep changes small and reviewable.
- Require peer review before merging.
- Link each change to a story, defect, risk, or technical item.
- Record decisions that affect architecture, security, privacy, data, or operations.
- Keep the default branch buildable.
- Never place real secrets, personal data, real internship records, or unredacted screenshots in the repository.
- Declare AI assistance according to instructor policy and review every generated change.

## Demonstration script

The final demonstration should show:

1. repository and pipeline status;
2. deployment version in the cloud environment;
3. successful student dossier and progress view;
4. blocked cross-student dossier or document access;
5. student logbook submission and assigned workplace-mentor approval;
6. document upload, scan state, and academic-supervisor review;
7. blocked action by an unassigned mentor or wrong role;
8. correlated frontend request, backend log, metric, and audit event;
9. controlled dependency failure and recovery; and
10. the diagram and ADR that explain the implemented choice.

## Submission

Submit the source repository, pipeline definitions, cloud deployment evidence,
architecture portfolio, test and scan reports, threat model, runbook, and a short
recorded or live demonstration. Use the [project rubric](rubric.md).
