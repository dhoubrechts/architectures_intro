# Lab 3 — Model an application flow

## Goal

Design the assignment-upload flow, including API responsibilities, storage,
asynchronous malware scanning, state transitions, authorization, and retries.

## Learning objectives

You will practise how to:

- place responsibilities in frontend, backend, storage, queue, and worker;
- select stores based on access and consistency needs;
- model asynchronous states and failure paths; and
- define idempotency and object-level authorization.

## Prerequisites

- Complete [Module 3](../course/03-applications-apis-and-data.md).
- Review the [student portal case](../case-study/student-portal.md).
- Create `portfolio/03-application-flow.md`.

## Scenario

Students can upload one final PDF per assignment. The file limit is 100 MB. A
submission is not accepted until malware scanning succeeds. A student may retry
after a network interruption, but the portal must not create duplicate final
submissions. Lecturers can view accepted submissions for their assigned courses.

Treat all numbers as case requirements for this lab.

## Part 1 — Assign responsibilities

Complete the table.

| Responsibility | Frontend | Backend API | Object store | Queue | Scan worker | Database |
| --- | :---: | :---: | :---: | :---: | :---: | :---: |
| Display progress | X | | | | | |
| Verify assignment window | | | | | | |
| Store PDF bytes | | | | | | |
| Persist submission state | | | | | | |
| Decide whether student may submit | | | | | | |
| Buffer scan work | | | | | | |
| Inspect file content | | | | | | |

Add at least four responsibilities. If two components participate, explain which
one is authoritative.

## Part 2 — Define the state model

Use at least these states:

```text
initiated -> uploaded -> scanning -> accepted
                                \-> rejected
```

Add failure or expiry states where needed. For each transition, identify:

- the initiating event;
- the component allowed to make the transition;
- the required validation; and
- the user-visible result.

Prevent impossible transitions, such as a browser directly marking a file as accepted.

## Part 3 — Draw the sequence

Create a sequence diagram with student, browser, API, database, object storage,
queue, and scan worker. Include:

1. permission request;
2. server-side authorization and assignment-window check;
3. a short-lived, object-specific upload permission;
4. direct upload;
5. scan request;
6. worker processing;
7. accepted and rejected outcomes; and
8. frontend status retrieval.

Add an alternate path for a network timeout after the file reached storage.

## Part 4 — Data placement

Decide where to store:

- student and assignment identifiers;
- PDF bytes;
- file hash and scan state;
- scan work messages;
- frequently read public assignment instructions; and
- audit events.

| Data | Authoritative store | Optional derived copy | Consistency or retention concern |
| --- | --- | --- | --- |
| Your item | | | |

## Part 5 — Idempotency and authorization

Write a design for `POST /assignments/{assignmentId}/submissions` that addresses:

- authenticated subject;
- course enrolment and deadline;
- one final submission rule;
- retry after an uncertain timeout;
- idempotency-key scope and lifetime;
- conflict response; and
- audit evidence.

Then write three negative authorization tests, including cross-student access.

## Completion checkpoint

- File bytes do not pass through the API without an explicit reason.
- The upload permission cannot write arbitrary object keys and expires quickly.
- “Uploaded” is not treated as “accepted.”
- Retrying an uncertain request does not create a second final submission.
- The worker, not the browser, records the scan outcome.

## Deliverables

- responsibility matrix;
- state transition table or diagram;
- sequence diagram with alternate paths;
- data-placement table;
- idempotency design; and
- three authorization tests.

After completing the lab, compare with the
[reference solution](solutions/03-model-an-application-flow-solution.md).
