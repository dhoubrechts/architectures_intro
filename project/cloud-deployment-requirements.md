# End project — Local container and cloud deployment requirements

## Required progression

Students must complete the stages in order. A cloud deployment cannot replace a
broken or unreproducible local stack.

### Stage 1 — Local application

- Frontend calls backend successfully outside containers.
- Backend uses a local synthetic datastore.
- Success, failure, and unauthorized paths have automated tests.

### Stage 2 — Local container Test environment

- Separate frontend and backend images build from versioned source.
- A local datastore container starts with migrations and synthetic seed data.
- One compose command or equivalent starts the stack.
- Only the required frontend or ingress and optional debugging port are exposed.
- Backend and datastore communication remains on a private container network.
- Stop, restart, recreation, and intentional volume cleanup are documented.

### Stage 3 — Pipeline and registry

- The pipeline builds each image once.
- Application, dependency, secret, configuration, and image checks run.
- Approved images are pushed to an instructor-approved registry.
- The deployment uses immutable digests or equivalent immutable versions.
- Registry credentials are not available to untrusted pull-request code.

### Stage 4 — Cloud Acceptance

- The same approved frontend and backend image versions are deployed.
- A public DNS name resolves to an HTTPS endpoint.
- Authorised reviewers can access the frontend from another network.
- Identity and object-level authorization protect portal data.
- The backend and datastore are not broadly public.
- Environment secrets come from the approved cloud mechanism.
- Migrations run through a controlled, observable job.
- Logs, metrics, audit events, and version information are available.

### Stage 5 — External verification and recovery

- A reviewer completes a successful journey over HTTPS.
- Cross-account and unauthenticated requests remain blocked.
- A controlled dependency failure produces a safe frontend error and useful telemetry.
- The team demonstrates rollback, forward fix, or reproducible recovery.
- Cost, quotas, and cleanup are reviewed.

## Minimum container artefacts

- frontend container build definition;
- backend container build definition;
- local compose or equivalent configuration;
- safe environment-variable example;
- migration and seed mechanism;
- health/readiness definitions;
- image scan and software inventory evidence; and
- commands for build, start, test, stop, and cleanup.

## Minimum cloud artefacts

- cloud deployment diagram;
- infrastructure as code or versioned deployment configuration;
- DNS and HTTPS evidence;
- network and ingress rules;
- workload identity and secret references;
- deployment record with source commit and image digests;
- post-deployment smoke and authorization results;
- dashboard or telemetry evidence;
- cost and quota guardrails; and
- exact cleanup inventory and owner approval.

## External reviewer acceptance test

An authorised person who is not connected to the developer's local network must:

1. resolve the public course-project name;
2. establish HTTPS without bypassing certificate warnings;
3. sign in through the approved method;
4. view only the fictional records assigned to their identity;
5. receive a safe denial for a protected record outside their scope; and
6. provide the correlation identifier for a deliberately failed request so the
   team can find its telemetry.

## Safety and cost rules

- Use only instructor-approved cloud accounts, regions, services, and identity providers.
- Use fictional data and course-only identities.
- Do not expose a database, container management API, debug port, or telemetry dashboard publicly.
- Do not commit cloud keys, registry credentials, certificates, or `.env` secret values.
- Apply resource tags, budgets, quotas, and expiry information.
- Remove course resources after assessment only with exact target verification and owner approval.

## Assessment evidence

The team must show both local and cloud versions during assessment. The assessor
may compare image digests and version endpoints to confirm that the approved
artefacts were promoted rather than rebuilt manually.
