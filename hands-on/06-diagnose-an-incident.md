# Lab 6 — Diagnose an incident

## Goal

Diagnose an evaluation-deadline incident using incomplete evidence. Separate observations,
hypotheses, decisions, and proof.

## Learning objectives

You will practise how to:

- define user impact and the known-good boundary;
- rank competing hypotheses;
- use metrics, logs, and traces together;
- choose a reversible mitigation; and
- propose a structural correction and validation plan.

## Prerequisites

- Complete [Module 6](../course/06-reliability-and-observability.md).
- Create `portfolio/06-incident-analysis.md`.

## Scenario

At 09:00 on the final evaluation deadline, academic supervisors open their
assigned-student dashboards. By 09:04, many can sign in but receive HTTP `500`
from the dashboard. Student static pages remain fast.

Observed dashboard values:

| Signal | 08:55 | 09:05 |
| --- | ---: | ---: |
| Assigned-student requests per second | 8 | 160 |
| Dashboard request p95 latency | 220 ms | 9.8 s |
| Dashboard HTTP 5xx rate | 0.1% | 37% |
| Application CPU | 28% | 52% |
| Application instances | 3 | 3 |
| Database active connections | 18 | 100 |
| Database connection limit | 100 | 100 |
| Database CPU | 35% | 61% |
| Connection-pool wait p95 | 12 ms | 8.9 s |
| Login success rate | 98.7% | 98.4% |

Recent changes:

- version `2026.10.30.2` was deployed at 08:30;
- the release changed dashboard enrichment from one bounded query to one base
  query plus separate queries per student for phase, overdue activities, and review count;
- no database schema migration ran;
- automatic retries occur twice after a database acquisition timeout.

Representative log excerpts:

```text
09:05:11 ERROR request_id=7f2 route=/api/supervisors/me/dossiers db_pool_timeout_ms=5000
09:05:11 WARN  request_id=7f2 retry=1 operation=load_dossier_progress
09:05:17 ERROR request_id=7f2 response_status=500 duration_ms=11240
```

## Part 1 — State impact and evidence

Write:

- user-visible impact;
- start time and affected function;
- functions that still work;
- facts directly supported by evidence; and
- important unknowns.

Do not write “database is down”; the evidence does not support that claim.

## Part 2 — Build a hypothesis table

Create at least five hypotheses.

| Hypothesis | Evidence for | Evidence against or missing | Next distinguishing test | Rank |
| --- | --- | --- | --- | ---: |
| Connection pool is exhausted by query amplification | Pool at limit; per-course query change; long waits | Need query count and connection lifetime | Compare traces before and after release | 1 |
| Your hypothesis | | | | |

Include DNS or edge, identity, application capacity, database query behaviour,
and connection leakage or amplification.

## Part 3 — Reconstruct one request

Draw a trace-style sequence for request `7f2`. Mark:

- successful edge and application entry;
- base assigned-dossier query;
- per-dossier phase, activity, and review queries;
- connection wait;
- retry;
- timeout; and
- HTTP `500` response.

Label inferred steps as hypotheses.

## Part 4 — Choose a mitigation

Evaluate these actions:

1. add five application instances;
2. increase database connection limit immediately;
3. disable retries and roll back the application release;
4. restart the database; and
5. hide all internship dossiers from students and supervisors.

For each, record expected benefit, risk, reversibility, and evidence needed.
Select a primary mitigation and an explicit success measure.

## Part 5 — Structural correction

Propose a correction that addresses query amplification or connection use.
Include:

- code or query change;
- connection-pool and timeout policy;
- retry policy and idempotency consideration;
- peak-load test;
- dashboard and alert changes; and
- deployment and rollback validation.

## Part 6 — Incident learning

Write five follow-up actions across prevention, detection, mitigation, recovery,
and process. Assign an owner and due condition, not a fictional calendar date.

## Completion checkpoint

- You separated observed facts from inferred cause.
- You did not add frontend capacity without analysing database impact.
- The mitigation is reversible and has a success signal.
- The structural fix includes a representative load test.
- Follow-up improves the system, not only the person or procedure.

## Deliverables

- impact statement;
- hypothesis table;
- request sequence;
- mitigation decision;
- structural correction; and
- incident follow-up table.

After completing the lab, compare with the
[reference solution](solutions/06-diagnose-an-incident-solution.md).
