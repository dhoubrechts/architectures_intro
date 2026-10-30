# Course Repository Guidelines

## Purpose

This repository is named `architectures_intro` and contains the English,
hands-on **Intro to Architectures** course for PXL students. Keep every
contribution practical, approachable, and suitable for learners who have
technical foundations but limited architecture experience.

## Language and tone

- Write all learner-facing content in clear English.
- Define an architectural term before using it in a complex explanation.
- Prefer concrete systems, trade-offs, and decisions over abstract descriptions.
- Address the learner directly and use active voice.
- Avoid vendor marketing language and unsupported claims.

## Course structure

- Store course modules in `course/` and reusable assets in `assets/`.
- Give every module a numbered filename and a descriptive title.
- Start each module with learning objectives and estimated study time.
- Combine concise theory with examples, diagrams, checkpoints, and a hands-on lab.
- End each module with a summary, review questions, and pointers to the next module.
- Keep instructor solutions separate from learner instructions under `solutions/`.

## Lab requirements

Every lab must include:

1. A realistic scenario and learner role.
2. Clear objectives and expected deliverables.
3. Prerequisites and required tools.
4. Numbered tasks with verification checkpoints.
5. Reflection questions about trade-offs and consequences.
6. A cleanup section when the lab creates local resources.
7. A matching reference solution or assessment rubric.

Labs should work locally with free tools where possible. Cloud work must use an
instructor-approved education or sandbox account with budgets, quotas, expiry,
and an exact cleanup plan. Never require personal cloud accounts, real
production credentials, personal data, or destructive actions against shared
resources. Use synthetic data and fictional organizations.

The end project grows incrementally: local frontend and backend, persistence,
local containers, pipeline gates, cloud deployment, external HTTPS access,
observability, recovery, and defence. Do not introduce a later layer until the
earlier working slice is reproducible and tested.

## Markdown conventions

- Use one `#` heading per file and a logical heading hierarchy below it.
- Add a blank line around headings, lists, tables, and fenced code blocks.
- Specify a language on fenced code blocks when applicable.
- Use relative links for repository files and descriptive text for external links.
- Add accessible alternative text to every image.
- Prefer Mermaid for architecture diagrams that benefit from version control.
- Keep lines readable and avoid raw HTML unless Markdown cannot express the result.

## Technical quality

- Explain assumptions and distinguish facts from design choices.
- Present alternatives and trade-offs instead of declaring one architecture universally best.
- Use consistent terminology across modules and update the glossary when introducing terms.
- Test commands and validate Mermaid diagrams before publishing.
- Check all internal links and ensure that learner instructions match the provided solutions.
- Preserve existing user-authored files unless the task explicitly asks to change them.

## Definition of done

A contribution is complete when the content is technically accurate, understandable without instructor improvisation, internally linked, accompanied by the required lab materials, and reviewed for spelling, formatting, and safety.
