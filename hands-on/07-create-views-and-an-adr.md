# Lab 7 — Create architecture views and an ADR

## Goal

Create a small, consistent architecture description for the Workplace Learning Hub and document
one significant decision.

## Learning objectives

You will practise how to:

- select detail appropriate to a view and audience;
- maintain consistent names and responsibilities across diagrams;
- model runtime and deployment separately; and
- write an ADR with alternatives and negative consequences.

## Prerequisites

- Complete [Module 7](../course/07-views-and-decisions.md).
- Bring outputs from Labs 1 through 6.
- Create `portfolio/07-views-and-adr.md`.

## Part 1 — Audience questions

For each audience, write its three most important questions:

- project sponsor;
- application developer;
- security reviewer;
- operations engineer; and
- service desk.

Choose which questions are answered by context, container, deployment, or
sequence views.

## Part 2 — Context view

Create a system context diagram for the Workplace Learning Hub. Include actors and external
systems only. Add:

- title and scope;
- relationship labels;
- a short description of platform responsibility; and
- one paragraph on what is out of scope.

## Part 3 — Container view

Create a container view with browser application, Workplace Learning API,
dossier database, object storage, document queue, and document worker. Add
institutional identity, external-mentor identity, notification, and student
information systems for context.

Each element must have:

- unique name;
- type or technology category where useful;
- one-sentence responsibility; and
- owner.

Each relationship must show direction, purpose, and protocol or data where useful.

## Part 4 — Production deployment view

Map containers to a production environment using your Lab 4 decision. Show:

- public and private network boundaries;
- instance multiplicity or scaling range;
- managed data services;
- environment-specific identity and secrets;
- telemetry destination; and
- backup or recovery path.

State which failure domains are shown and which are not.

## Part 5 — Logbook and document sequences

Create one sequence for student logbook submission and assigned workplace-mentor
approval. Create a second sequence for successful document upload, scanning, and
academic-supervisor review. Add alternate paths for changed mentor assignment,
expired upload permission, rejected file, and unassigned supervisor. Ensure names
match the container view.

## Part 6 — Consistency review

Create a table:

| Element | Context | Container | Deployment | Sequence | Consistent responsibility? |
| --- | :---: | :---: | :---: | :---: | --- |
| Workplace Learning API | | X | X | X | |

Correct mismatches before continuing.

## Part 7 — Write ADR 001

Decision: **managed application platform or orchestrated containers for the
first Workplace Learning Hub release**.

Include:

- status;
- context and decision drivers;
- at least three considered options, including VMs;
- decision and scope;
- positive and negative consequences;
- validation evidence; and
- review triggers.

Do not hide disadvantages of the selected option. Refer to the weighted evidence
from Lab 4.

## Completion checkpoint

- The context view has no internal database or queue.
- The container view uses C4 “container” correctly.
- The deployment view names one environment and shows instances and boundaries.
- The sequence uses the same element names as the static views.
- The ADR can be understood without opening the diagrams.

## Deliverables

- audience-question map;
- context, container, deployment, and sequence views;
- consistency table; and
- ADR 001.

After completing the lab, compare with the
[reference solution](solutions/07-create-views-and-an-adr-solution.md).
