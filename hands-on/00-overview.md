# Hands-on labs

The labs turn the Northstar Workplace Learning Hub case into an evidence portfolio. Work
in order: each lab reuses earlier requirements, names, and decisions.

## How to work

For every activity:

1. **Predict.** Record what you expect before drawing, calculating, or testing.
2. **Create.** Produce the requested artefact in Markdown, Mermaid, or a table.
3. **Check.** Use the checkpoint to find missing reasoning.
4. **Reflect.** State one benefit, one cost, and one remaining uncertainty.
5. **Compare.** Open the reference solution only after a serious attempt.

Model solutions show one defensible route, not the only correct architecture.
Different answers are valid when they satisfy the case, state assumptions, and
explain consequences.

## Suggested sequence

| Lab | Main artefact | Suggested time |
| --- | --- | ---: |
| Foundation — Idea to implementation | Secure backlog and DTAP delivery plan | 90 min |
| 1 — Map the system | Requirements, dependencies, and context diagram | 75 min |
| 2 — Trace a web request | Evidence log and request sequence | 75 min |
| 3 — Model an application flow | Upload sequence and data-placement table | 90 min |
| 4 — Compare deployment options | Weighted decision matrix | 75 min |
| 5 — Threat-model the platform | Trust boundaries and control tests | 90 min |
| 6 — Diagnose an incident | Hypothesis and evidence log | 75 min |
| 7 — Create views and an ADR | Diagram set and decision record | 120 min |
| 8 — Docker local to cloud | Docker Compose stack and cloud deployment evidence | 2-4 h |
| 9 — Capstone | Complete implementation, architecture portfolio, and defence | 4-6 h |

## Tools

- A text editor.
- A Markdown viewer with Mermaid support, such as GitHub.
- Browser developer tools for Lab 2.
- `nslookup` or `dig`, and `curl`, for Lab 2.

If a Mermaid renderer is unavailable, draw with labelled boxes and arrows in an
instructor-approved tool. Export the source as well as an image so the artefact
remains editable.

## Safety boundaries

- Use only fictional data.
- Run network commands only against `example.com`, your own test environment, or
  an instructor-approved target.
- Do not scan ports, bypass controls, generate disruptive load, or modify a target.
- Do not copy tokens, cookies, passwords, or personal data into submissions.
- Redact identifiers in screenshots and terminal output.

## Lab file convention

Store your work using this structure:

```text
portfolio/
├── 00-idea-to-implementation.md
├── 01-system-map.md
├── 02-request-trace.md
├── 03-application-flow.md
├── 04-deployment-decision.md
├── 05-threat-model.md
├── 06-incident-analysis.md
├── 07-views-and-adr.md
├── 08-docker-local-to-cloud.md
└── 09-capstone.md
```

Keep diagrams inside the matching Markdown file where practical. Commit or save
after each checkpoint so you can explain how your design evolved.
