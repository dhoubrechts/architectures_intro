# Lab 6 solution — Diagnose an incident

## Impact statement

From approximately 09:04, many authenticated students receive HTTP `500` when
opening results. Login and static content remain available. Result p95 latency is
9.8 seconds and 5xx rate is 37%. Database connections and pool wait are at their
observed limit after a release that added per-course queries and automatic retries.

This supports a database-connection pressure hypothesis. It does not prove the
database engine is down or that connection count is the only cause.

## Ranked hypotheses

| Hypothesis | Supporting evidence | Missing or opposing evidence | Next test |
| --- | --- | --- | --- |
| Query amplification exhausts pool | Per-course query release, pool limit, high wait | Need per-request query count | Compare pre/post-release traces |
| Retry amplification worsens saturation | Two retries after acquisition timeout | Retry volume not shown | Count attempts per user request |
| Connection leak | Pool remains full | No connection lifetime or idle count | Inspect active/idle age and code path |
| Slow database query | Elevated request latency | Database CPU only 61%; query time absent | Inspect query spans and execution plan |
| Edge or identity issue | User-facing errors | Static and login success are stable | Compare route-specific edge and auth metrics |

## Mitigation decision

Roll back version `2026.10.30.2` and temporarily disable acquisition retries if
that configuration is independently controllable. This directly removes the
known query-amplifying change and extra load, is reversible, and avoids guessing
at a safe higher database connection limit.

Success measures: pool wait and active connections fall, result 5xx rate returns
near baseline, and p95 latency recovers. Keep monitoring during rollback and stop
if migration or compatibility evidence contradicts safety.

Adding application instances could create more database connections. Restarting
the database destroys useful state and may prolong impact. Raising the connection
limit without checking database capacity and pool behaviour can move the failure.

## Structural correction

Replace per-course queries with a bounded set or one appropriate joined/batched
query. Add per-request query-count and pool-wait telemetry. Bound the pool per
instance against total database capacity. Retry only safe transient failures with
limited backoff and a total request deadline; do not retry pool exhaustion twice
inside the same user request without evidence.

Run a result-day workload in Test using representative result and course counts.
Gate release on latency, error rate, pool wait, query count, and database capacity.

## Follow-up examples

- Portal team: add a regression test for bounded query count.
- Platform team: alert on sustained pool wait before complete exhaustion.
- Release owner: require a load-impact note for query-pattern changes.
- Operations: document the rollback and safe degraded mode.
- Architecture owner: review caching or read-model options only after measuring the corrected query.
