# Lab 3 — Model a logbook and document workflow

## Goal

Design two connected workplace-learning flows: student logbook submission with
workplace-mentor approval, and document upload with scanning and academic-
supervisor review.

## Learning objectives

You will practise how to:

- place responsibilities in frontend, backend, data, storage, queue, and worker;
- combine role, dossier assignment, object, and workflow-state authorization;
- model synchronous and asynchronous states and failure paths;
- select stores based on access, consistency, and retention needs; and
- define idempotency, version history, and audit evidence.

## Prerequisites

- Complete [Module 3](../course/03-applications-apis-and-data.md).
- Review the [workplace learning case](../case-study/workplace-learning-platform.md).
- Create `portfolio/03-application-flow.md`.

## Scenario

A student records workplace activity and hours in a weekly logbook. The assigned
workplace mentor approves the entry or returns it with feedback. The student also
uploads a progress document for a phase activity. The document must pass size,
type, and malware checks before the assigned academic supervisor can review it.

A network retry must not create duplicate logbook entries, approvals, document
versions, or reviews. A changed mentor assignment takes effect immediately for
new actions while historical audit evidence remains intact.

## Part 1 — Assign responsibilities

Complete the matrix.

| Responsibility | Frontend | Backend API | Object store | Queue | Document worker | Database |
| --- | :---: | :---: | :---: | :---: | :---: | :---: |
| Display phase, status, and next action | X | | | | | |
| Establish identity and current dossier assignment | | | | | | |
| Validate logbook hours and phase | | | | | | |
| Persist logbook and review state | | | | | | |
| Store document bytes | | | | | | |
| Buffer document scan work | | | | | | |
| Inspect uploaded content | | | | | | |
| Enforce valid workflow transition | | | | | | |

Add at least four responsibilities. When two components participate, identify
which one is authoritative.

## Part 2 — Define the workflow states

### Logbook entry

Use at least:

```text
draft -> submitted -> approved
                   \-> changes_requested -> submitted
```

### Document

Use at least:

```text
initiated -> uploaded -> scanning -> accepted -> under_review -> reviewed
                                \-> rejected
```

For each transition, identify:

- initiating event;
- component and role allowed to make the transition;
- current dossier assignment and required validation;
- resulting audit event; and
- user-visible state.

Prevent impossible transitions, such as a browser directly marking a document
as accepted or an unassigned mentor approving an entry.

## Part 3 — Draw the logbook sequence

Create a sequence with student, browser, API, database, workplace mentor, and
notification provider. Include:

1. student submission with an idempotency key;
2. server-side identity, dossier, phase, date, and hour validation;
3. mentor notification;
4. mentor sign-in and assignment check;
5. approval or changes-requested result;
6. audit evidence; and
7. student status retrieval.

Add an alternate path in which the mentor assignment changed after submission.

## Part 4 — Draw the document sequence

Create a sequence with student, browser, API, database, object storage, queue,
document worker, and academic supervisor. Include:

1. permission request for a specific dossier activity;
2. role, assignment, phase, deadline, size, and type validation;
3. short-lived, object-specific upload permission;
4. direct upload;
5. trusted upload verification;
6. scan request and worker processing;
7. accepted and rejected outcomes;
8. supervisor assignment check and review; and
9. frontend status retrieval.

Add an alternate path for a network timeout after the object reached storage.

## Part 5 — Decide data placement

Place:

- dossier, placement, role assignments, and phases;
- logbook entries, hours, feedback, and approval history;
- document bytes, metadata, versions, and scan state;
- work messages;
- process-template instructions; and
- immutable or append-oriented audit events.

| Data | Authoritative store | Optional derived copy | Consistency, privacy, or retention concern |
| --- | --- | --- | --- |
| Your item | | | |

## Part 6 — Idempotency and authorization

Write a design for:

- `POST /api/dossiers/{dossierId}/logbook`;
- `POST /api/logbook/{entryId}/review`; and
- `POST /api/dossiers/{dossierId}/documents`.

Address authenticated subject, current role assignment, allowed state,
idempotency-key scope and lifetime, duplicate handling, conflict response,
version history, and audit evidence.

Write six negative tests including cross-student access, unassigned workplace
mentor, unassigned academic supervisor, expired upload permission, wrong object
key, and invalid workflow transition.

## Completion checkpoint

- A role name alone never grants access to every dossier.
- Logbook and document transitions have one authoritative enforcement point.
- Document bytes do not pass through the API without an explicit reason.
- Upload permission cannot write arbitrary object keys and expires quickly.
- “Uploaded” is not treated as “accepted” or “reviewed.”
- A retry does not create a duplicate entry, approval, document version, or review.
- Historical audit records preserve who acted under which assignment at that time.

## Deliverables

- responsibility matrix;
- two state models;
- logbook sequence with alternate path;
- document sequence with alternate path;
- data-placement table;
- idempotency and authorization design; and
- six negative tests.

After completing the lab, compare with the
[reference solution](solutions/03-model-an-application-flow-solution.md).
