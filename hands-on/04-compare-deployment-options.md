# Lab 4 — Compare deployment options

## Goal

Compare three deployment options for the portal without selecting a platform by
fashion or familiarity alone. Produce a decision matrix and a provisional recommendation.

## Learning objectives

You will practise how to:

- turn quality drivers into weighted evaluation criteria;
- compare control, responsibility, cost, and operational complexity;
- identify hidden costs and shared responsibilities; and
- define evidence and a review trigger for a provisional decision.

## Prerequisites

- Complete [Module 4](../course/04-infrastructure-cloud-and-delivery.md).
- Create `portfolio/04-deployment-decision.md`.

## Options

Evaluate:

1. application on one or more virtual machines with a managed database;
2. managed application platform with a managed database; and
3. containers on an orchestrated platform with a managed database.

Assume the institution does not yet operate a shared container platform. State
any additional assumptions.

## Part 1 — Define decision drivers

Choose six to eight criteria. Include at least:

- operational simplicity for a small team;
- peak scaling;
- security and patching responsibility;
- recovery capability;
- delivery speed; and
- total cost.

Assign weights that total 100. Explain each weight in one sentence.

| Criterion | Weight | Why it matters |
| --- | ---: | --- |
| Your criterion | | |
| **Total** | **100** | |

## Part 2 — Score the options

Use a 1-5 scale, where 5 best satisfies the criterion. Every score needs a short
justification. Do not use false precision beyond this simple exercise.

| Criterion | Weight | VM score | Managed platform score | Orchestrated containers score |
| --- | ---: | ---: | ---: | ---: |
| Your criterion | | | | |

Calculate weighted totals, then perform a sensitivity check: increase the weight
of the weakest area in your winning option by ten points and rebalance another
weight. Does the recommendation change?

## Part 3 — Responsibility map

For each option, identify who handles:

- host or platform patching;
- application runtime updates;
- application deployment;
- database configuration and schema;
- identities and secrets;
- backups and restore testing;
- monitoring and incident response; and
- capacity and cost review.

Use `provider`, `platform team`, or `portal team`, but add a note where responsibility is shared.

## Part 4 — Environment and delivery diagram

Draw a path from versioned change to production. Include build, tests, security
checks, acceptance, approval, database migration, deployment verification, and
rollback or forward fix. Show that environment configuration and secrets are not
embedded in the build artefact.

## Part 5 — Recommendation

Write 250-400 words containing:

- chosen option and scope;
- top three decision drivers;
- two disadvantages;
- the strongest rejected alternative and why it lost;
- evidence still needed; and
- a measurable review trigger.

Example trigger: “Revisit if platform limits prevent the measured peak workload
or if the institution establishes a supported shared container platform.”

## Completion checkpoint

- Your highest score follows from weights and evidence, not a preferred product.
- The managed option still assigns security, data, recovery, and monitoring work to the portal team.
- People and telemetry appear in the cost analysis.
- The recommendation contains negative consequences and a review trigger.

## Deliverables

- weighted criteria and scoring matrix;
- sensitivity check;
- responsibility map;
- delivery diagram; and
- provisional recommendation.

After completing the lab, compare with the
[reference solution](solutions/04-compare-deployment-options-solution.md).
