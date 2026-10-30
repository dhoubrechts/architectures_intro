# Lab 5 — Threat-model the workplace learning platform

## Goal

Identify trust boundaries, abuse cases, security controls, and verification
evidence for dossier access, logbook approval, document upload, and review.

## Learning objectives

You will practise how to:

- distinguish authentication from object-level authorization;
- model trust boundaries and service identities;
- connect threats to preventive, detective, and recovery controls; and
- define negative security tests.

## Prerequisites

- Complete [Module 5](../course/05-identity-and-security.md).
- Reuse the flow from [Lab 3](03-model-an-application-flow.md).
- Create `portfolio/05-threat-model.md`.

## Part 1 — Identify assets and actors

List at least ten assets, such as dossier records, placement and contact data,
logbook hours, feedback, assessments, uploaded documents, identity tokens,
audit history, service credentials, and availability. For each asset,
state the required confidentiality, integrity, and availability.

List human and technical actors. Include student, academic supervisor, workplace
mentor, internship coordinator, support analyst, platform service, document
worker, identity provider, and notification service.

## Part 2 — Draw data flows and boundaries

Draw one data-flow view covering browser, public edge, Workplace Learning API, identity
provider, external identity flow, database, object storage, queue, and document worker.

Mark boundaries for:

- internet to public edge;
- edge to application environment;
- application to data services;
- platform ownership to external identity or notification ownership; and
- human administrative access.

Label data and identity on every arrow.

## Part 3 — Create abuse cases

Write at least ten abuse cases. Include:

- changing a dossier or document identifier;
- using a workplace-mentor role to access an unassigned student;
- replaying or reusing an upload permission;
- uploading unexpected content;
- forging identity or role claims;
- stealing a service credential;
- flooding login, assigned-student dashboard, logbook, or upload endpoints;
- changing hours, feedback, assessment, or supervisor assignment without a defensible audit record;
- exposing tokens or personal data in logs;
- a compromised document worker; and
- a coordinator using excessive privilege.

## Part 4 — Map controls and evidence

| Abuse case | Prevent or limit | Detect | Recover | Verification evidence | Owner |
| --- | --- | --- | --- | --- | --- |
| Change dossier ID | Server-side role, assignment, object, and state authorization | Denial metric and audit event | Investigate affected session and route | Automated cross-dossier test | Platform team |
| Your case | | | | | |

Avoid generic controls such as “use encryption” without specifying where,
against which threat, and how it is checked.

## Part 5 — Design negative tests

Write at least eight tests. Use this format:

```gherkin
Given <identity and state>
When <action or malicious variation>
Then <protected outcome>
And <safe evidence>
```

Include tests for cross-student dossier and document access, unassigned mentor
access, expired upload permission, oversized upload, invalid role claim, missing
token, repeated logbook approval, invalid phase transition, log redaction, and
worker access outside its object scope.

## Part 6 — Least-privilege matrix

| Identity | Required actions | Explicitly forbidden | Credential type and lifetime | Review owner |
| --- | --- | --- | --- | --- |
| Workplace Learning runtime | | | | |
| Document worker | | | | |
| Migration job | | | | |
| Service desk | | | | |
| Administrator | | | | |

## Completion checkpoint

- Every sensitive object and workflow transition has a server-side authorization rule.
- Network location is not the only reason to trust a caller.
- Logs provide evidence without storing credentials or protected content.
- Service identities have different scopes when their responsibilities differ.
- Controls have owners and verification methods.

## Deliverables

- asset and actor list;
- data-flow and trust-boundary diagram;
- abuse cases;
- control and evidence table;
- negative tests; and
- least-privilege matrix.

After completing the lab, compare with the
[reference solution](solutions/05-threat-model-the-platform-solution.md).
