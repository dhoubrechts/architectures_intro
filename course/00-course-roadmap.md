# Course roadmap and study method

**Estimated study time:** 20-30 minutes

## The learning path

The course moves from an initial idea to a defensible, implemented, and
operable architecture.

1. **Shape the idea.** Define the problem, stakeholders, user stories,
   acceptance criteria, security needs, delivery path, and feedback loop.
2. **See the system.** Translate a need into actors, responsibilities,
   dependencies, quality attributes, and constraints.
3. **Follow the request.** Trace name resolution, transport security, HTTP, and
   application processing end to end.
4. **Place logic and data.** Decide what belongs in the client, backend, API,
   database, object store, cache, or queue.
5. **Choose an execution environment.** Compare servers, virtual machines,
   containers, and managed platforms without starting from product names.
6. **Secure the boundaries.** Separate authentication from authorization and
   apply controls wherever trust changes.
7. **Operate the service.** Design for failure, recovery, scaling, and useful
   telemetry.
8. **Communicate decisions.** Use the smallest set of views that answers the
   audience's questions and record significant trade-offs.
9. **Integrate and defend.** Produce a coherent design and critique AI-generated
   suggestions.

Complete the modules in order. Every lab adds an artefact to the same student
Workplace Learning Hub design, so later work depends on decisions and vocabulary introduced
earlier.

## Progressive levels

| Level | Modules | Learner can demonstrate |
| --- | --- | --- |
| Beginner | Foundation, 1, and 2 | Explain a problem, story, system boundary, and web request without product jargon. |
| Developing | 3, 4, and 5 | Model an application flow, compare deployment options, and design security controls. |
| Applied | 6 and 7 | Diagnose failure and communicate architecture with consistent views and ADRs. |
| Integrated | Implementation journey, Docker deployment, and final capstone | Build locally with Docker Compose, deliver the same images to cloud, observe, and defend a working vertical slice. |

Each level reuses earlier artefacts. Instructors should require a small working
result before adding another layer. A learner first connects one frontend action
to one backend endpoint; only then adds persistence, authorization, pipeline
gates, deployment, and operational evidence.

## Lesson template

Every lesson follows the same study cycle:

1. learning objectives and prerequisites;
2. core concepts and an end-to-end example;
3. an architecture diagram or decision model;
4. short practice questions;
5. a checkpoint and summary; and
6. a link to the matching hands-on lab.

## How to reason about a design

Use this chain whenever you evaluate a component or proposal:

```text
Need -> requirement -> design decision -> consequence -> evidence
```

For example:

```text
Students upload large assignments
-> uploads must not consume all web-server memory
-> upload directly to object storage using short-lived permission
-> more components and a new authorization flow
-> load test, access-control test, storage metrics, and an expiry check
```

Skipping a link in this chain produces weak architecture. A component without a
requirement may be unnecessary. A decision without a consequence hides a
trade-off. A claim without evidence is only an assumption.

## Recommended pace

| Activity | Suggested time per module |
| --- | ---: |
| Lesson and notes | 45-60 minutes |
| Guided lab work | 60-90 minutes |
| Review and reflection | 20-30 minutes |

The capstone normally requires an additional half day. Instructors can compress
or extend the sequence by changing the depth of the lab deliverables.

## Evidence portfolio

Keep these artefacts in a personal portfolio folder:

- requirement and quality-attribute tables;
- role-based wireframes and selected visual mock-ups;
- context, container, deployment, and sequence diagrams;
- request-trace observations;
- a data-placement decision table;
- a threat model and security-control table;
- an incident hypothesis log;
- at least one Architecture Decision Record;
- Dockerfiles, Docker Compose configuration, image digests, and cloud deployment evidence; and
- the capstone design and oral defence notes.

Version the artefacts. Architecture evolves as assumptions are tested; replacing
an earlier design without recording why removes useful evidence.
