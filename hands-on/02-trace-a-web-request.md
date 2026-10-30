# Lab 2 — Trace a web request

## Goal

Collect evidence from a safe public web request and turn it into an architecture
sequence. Explain exactly what each observation proves and what remains unknown.

## Learning objectives

You will practise how to:

- inspect DNS, TLS, and HTTP behaviour with basic tools;
- distinguish name resolution from the application-data path;
- interpret status, headers, protocol, and timing cautiously; and
- form competing hypotheses for a failed request.

## Prerequisites and safety

- Complete [Module 2](../course/02-networks-and-communication.md).
- Create `portfolio/02-request-trace.md`.
- Use `https://example.com` unless your instructor provides another safe target.
- Do not use port scanners, load generators, vulnerability scanners, or login attacks.
- Redact cookies, tokens, internal names, and personal data.

## Part 1 — Resolve the name

Predict what the lookup will return, then run one suitable command:

```powershell
nslookup example.com
```

or:

```bash
dig example.com
```

Record:

| Observation | Value | What it supports | What it does not prove |
| --- | --- | --- | --- |
| Resolver used | | | |
| Address record or records | | | |
| TTL, if shown | | | |

Results can differ by location, resolver, address family, and time. Record your
actual observation; do not copy a model IP address.

## Part 2 — Inspect HTTP and TLS

Run:

```bash
curl -I https://example.com
```

Then, if your environment permits verbose output:

```bash
curl -v https://example.com -o /dev/null
```

On Windows PowerShell, confirm that `curl` invokes the expected executable in
your environment. Do not paste secrets from verbose output.

Record:

- HTTP version, if displayed;
- status code;
- three response headers and their purpose;
- certificate subject or host coverage, issuer, and validity dates, if displayed;
- total time or timing observations; and
- any proxy or environment limitation.

For every observation, state what it proves and does not prove.

## Part 3 — Browser developer tools

Open the target in a browser and use the Network panel.

1. Reload the page with the panel open.
2. Select the main document request.
3. Record method, URL, status, transferred size, and timing.
4. Identify whether additional requests were made.
5. Do not copy cookies or authorization headers.

Compare browser and `curl` results. Differences may come from protocol support,
caching, headers, proxy behaviour, compression, or client configuration.

## Part 4 — Build a sequence diagram

Draw a sequence with at least:

- user or browser;
- DNS resolver;
- public endpoint; and
- origin application as a logical component.

Show DNS as a resolution exchange, followed by a separate connection to the
resolved endpoint. Annotate the diagram with the evidence you directly observed
and label unobserved internal processing as an assumption.

## Part 5 — Failure hypotheses

Scenario: the browser reports that the Workplace Learning Hub cannot load.

Create five competing hypotheses covering at least DNS, TLS, HTTP edge,
application, and data dependency.

| Hypothesis | Distinguishing test | Expected evidence if true | Safe next action |
| --- | --- | --- | --- |
| DNS returns a wrong address | Compare approved resolver output with known configuration | Unexpected record | Escalate to DNS owner; do not edit public DNS during diagnosis |
| Your hypothesis | | | |

Order the tests from least invasive and broadest evidence to deeper dependency checks.

## Completion checkpoint

- You did not claim that a DNS response proves the website works.
- You separated TLS protection from application authorization.
- You showed that the browser does not normally send application traffic through the DNS resolver.
- Every failure hypothesis has a test that could disprove it.

## Deliverables

- command and browser observations;
- evidence interpretation table;
- request sequence diagram;
- hypothesis table; and
- a short comparison of browser and command-line evidence.

After completing the lab, compare with the
[reference solution](solutions/02-trace-a-web-request-solution.md).
