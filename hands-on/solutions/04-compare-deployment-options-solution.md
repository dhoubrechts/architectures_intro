# Lab 4 solution — Compare deployment options

## Example criteria and weights

| Criterion | Weight | Reason |
| --- | ---: | --- |
| Operational simplicity | 25 | The portal has a small operating team. |
| Security and patch responsibility | 15 | Unpatched platform layers create material risk. |
| Peak scaling | 15 | Publication and deadline traffic is bursty. |
| Recovery capability | 15 | Academic records and assignments require tested recovery. |
| Delivery speed | 10 | The team needs safe, frequent change. |
| Total cost | 15 | People and managed-service costs must fit the budget. |
| Portability and exit | 5 | Provider coupling matters but is not the main first-release driver. |
| **Total** | **100** | |

## Example scoring

Scores are illustrative and depend on organisational capability.

| Criterion | Weight | VM | Managed platform | Orchestrated containers |
| --- | ---: | ---: | ---: | ---: |
| Operational simplicity | 25 | 3 | 5 | 2 |
| Security and patch responsibility | 15 | 2 | 4 | 3 |
| Peak scaling | 15 | 3 | 4 | 5 |
| Recovery capability | 15 | 3 | 4 | 4 |
| Delivery speed | 10 | 3 | 5 | 3 |
| Total cost | 15 | 4 | 4 | 2 |
| Portability and exit | 5 | 4 | 2 | 4 |

Weighted totals favour the managed application platform in this scenario. The
result changes if the organisation already has a supported container platform;
that assumption must be recorded and revisited.

## Responsibility example

With a managed platform, the provider operates physical infrastructure and much
of the runtime. The portal team still owns application dependencies,
configuration, identity, authorization, data classification, schema, queries,
backup policy, restore testing, telemetry, incidents, and cost review.

## Recommendation

Use a managed application platform and managed relational database for the
first release. The strongest drivers are the small team, need for repeatable
delivery, and burst handling without operating a cluster. The choice reduces OS
and orchestration work but introduces provider-specific configuration and a
recurring service cost. Platform limits can also constrain networking or runtime
features.

Orchestrated containers are the strongest rejected alternative because they
offer flexible scheduling and scaling. They lose for the first release because
the institution has no existing shared platform and the portal does not yet
justify the new control-plane and on-call burden.

Validate platform limits with a vertical slice, peak test, recovery exercise,
and monthly cost estimate. Revisit if the measured workload exceeds supported
limits, required controls are unavailable, or the institution establishes a
supported shared container platform.
