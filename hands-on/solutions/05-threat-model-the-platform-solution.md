# Lab 5 solution — Threat-model the workplace learning platform

## Assets and boundaries

High-value assets include internship dossiers, placement and contact data,
logbook hours, feedback, assessments, uploaded documents, identity and session
tokens, service credentials, audit history, availability, and backup data. The
main boundaries are internet-to-edge, edge-to-application, application-to-data
services, institutional and external identity, and human coordination access.

```mermaid
flowchart LR
    Browser[Untrusted browser] -->|HTTPS requests and identity token| Edge[Public edge]
    Edge -->|filtered request| API[Workplace Learning API]
    API -->|service identity and authorised query| DB[(Dossier database)]
    API -->|object-specific access| Store[(Object storage)]
    API -->|scan job| Queue[(Queue)]
    Queue --> Worker[Document worker]
    API -->|federated protocol| IdP[Institutional IdP]
```

## Example controls

| Abuse case | Prevent or limit | Detect | Recover | Verify |
| --- | --- | --- | --- | --- |
| Change dossier identifier | Role, current assignment, object, and state authorization | Denial count and audit event | Review session and affected routes | Two-student cross-dossier suite |
| Mentor requests unassigned intern | Current mentor-dossier assignment check | Denial metric and assignment audit | Remove stale sessions if required | Assigned and unassigned mentor tests |
| Reuse upload permission | Short expiry, one object key and operation | Rejected reuse metric | Invalidate pending submission | Reuse and wrong-key tests |
| Upload active content | Size/type policy, quarantine, scanner | Rejection event and backlog metric | Delete or isolate object | Known safe test fixture |
| Forge role claim | Validate issuer, audience, signature, time, and trusted claim mapping | Token-validation failures | Revoke client/session | Invalid issuer and modified-token tests |
| Steal worker credential | Workload identity and narrow object scope | Unusual object access audit | Revoke identity and rotate access | Attempt access to dossier and review records |
| Flood supervisor dashboard | Rate/concurrency limits and efficient query | Rate, latency, and pool metrics | Limit traffic or degrade safely | Authorised load test |
| Expose token in log | Allow-list structured fields and redaction | Automated log-content check | Restrict access and follow incident process | Representative auth-error test |
| Excess administrator privilege | Role separation and time-limited elevation | Sensitive-change audit | Remove access and reverse authorised change | Role-matrix and approval tests |

## Least privilege examples

| Identity | Required | Forbidden |
| --- | --- | --- |
| Platform runtime | Read permitted dossiers and manage workflow metadata | Schema administration and unrestricted export |
| Document worker | Read pending objects and write scan outcome | Read full dossiers, feedback, or assessments |
| Migration job | Apply approved schema changes | Serve user requests |
| Service desk | Read health and redacted diagnostic events | Read dossier content or alter records |
| Internship coordinator | Approved assignment and workflow administration | Direct database-owner access for routine work |

Strong solutions also define credential lifetime, review owner, and behaviour
when authorization or identity dependencies are unavailable.
