# Sources and further study

Use primary documentation to verify protocol behaviour, security requirements,
and architecture notation. Vendor guidance can illustrate an implementation,
but a vendor product page does not prove that a design fits this case.

## Architecture communication and decisions

- [C4 model](https://c4model.com/) — hierarchical software architecture views.
- [C4 diagrams](https://c4model.com/diagrams) — context, container, component,
  code, dynamic, and deployment views.
- [Architecture Decision Records](https://adr.github.io/) — background and
  examples for lightweight decision records.

## Web and network protocols

- [RFC 9110 — HTTP Semantics](https://www.rfc-editor.org/rfc/rfc9110.html).
- [RFC 8446 — TLS 1.3](https://www.rfc-editor.org/rfc/rfc8446.html).
- [RFC 1034 — Domain Names concepts and facilities](https://www.rfc-editor.org/rfc/rfc1034.html).
- [RFC 9000 — QUIC](https://www.rfc-editor.org/rfc/rfc9000.html).

## Security

- [OWASP Application Security Verification Standard](https://asvs.owasp.org/) —
  requirements for designing, developing, and testing modern web applications.
- [OWASP Authorization Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html).
- [NIST SP 800-207 — Zero Trust Architecture](https://csrc.nist.gov/pubs/sp/800/207/final).
- [OpenID Connect Core 1.0](https://openid.net/specs/openid-connect-core-1_0.html).
- [OAuth 2.0 Security Best Current Practice](https://www.rfc-editor.org/rfc/rfc9700.html).

## Reliability and observability

- [OpenTelemetry documentation](https://opentelemetry.io/docs/) — telemetry
  concepts and implementation guidance.
- [Google SRE books](https://sre.google/books/) — freely available material on
  reliability engineering, service levels, monitoring, and incident response.

## Cloud architecture guidance

- [Azure Architecture Center](https://learn.microsoft.com/azure/architecture/).
- [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html).
- [Google Cloud Architecture Framework](https://cloud.google.com/architecture/framework).

Cloud frameworks use different names and product examples. Compare their
underlying questions: security, reliability, performance, cost, operations, and
sustainability. Always re-evaluate advice against the actual requirements.
