# Review questions and capstone rubric

## Knowledge-check questions

1. Why is “use Kubernetes” not a complete architecture proposal?
2. What is the difference between a functional requirement, a quality
   attribute, and a constraint?
3. Which steps can occur between entering a URL and receiving an HTTP response?
4. Why does HTTPS not prove that application authorization is correct?
5. What responsibilities usually belong to a frontend, backend, and database?
6. When is object storage a better fit than a relational database?
7. What new failure modes appear when work is moved to a message queue?
8. How does a container differ from a virtual machine?
9. What does the shared-responsibility idea mean for a managed service?
10. What is the difference between authentication and authorization?
11. Why is hiding a button in the user interface not an authorization control?
12. What are RTO and RPO, and why must stakeholders agree on them?
13. Why might adding web-server instances make a database incident worse?
14. How do metrics, logs, and traces answer different diagnostic questions?
15. What does a context diagram show that a deployment diagram does not?
16. What makes an Architecture Decision Record useful months later?
17. Which evidence would support a claim that the system handles a result-day peak?
18. Name five warning signs in an AI-generated architecture proposal.

## Short model-answer direction

Strong answers connect concepts. For example, adding web instances increases
potential concurrency; if the database connection pool is already exhausted,
more callers can increase contention rather than remove the bottleneck. A load
balancer distributes requests but does not optimise queries, increase a fixed
connection limit, or repair an overloaded dependency.

For security questions, distinguish controls by purpose. TLS protects the
confidentiality and integrity of communication and normally authenticates the
server. Authentication establishes an identity. Authorization checks whether
that identity may perform a specific action on a specific resource.

## Capstone rubric

| Criterion | Weight | Evidence of strong performance |
| --- | ---: | --- |
| Requirements and scope | 15% | Assumptions, functional requirements, quality scenarios, and constraints are explicit. |
| Architecture correctness | 20% | Components have clear responsibilities; relationships, protocols, and data are coherent. |
| End-to-end reasoning | 15% | Login, result viewing, and upload flows can be followed across boundaries. |
| Security and privacy | 15% | Trust boundaries, object-level authorization, secrets, logging, and abuse cases are addressed. |
| Reliability and operations | 15% | Failure modes, recovery, scaling, deployment, and telemetry are testable. |
| Decisions and trade-offs | 10% | Major choices have alternatives, consequences, and decision drivers. |
| Communication and defence | 10% | Diagrams fit their audience; the student can explain every element without relying on AI output. |

## Minimum capstone evidence

- one system context diagram;
- one container diagram;
- one deployment diagram;
- two sequence diagrams: login and assignment upload;
- a quality-attribute scenario table;
- a security-control and trust-boundary table;
- an observability and recovery plan;
- three documented trade-offs;
- one complete ADR; and
- a critical review of one AI-generated alternative.

## Oral defence prompts

The assessor may choose any component or relationship and ask:

- Which requirement justifies it?
- What fails if it is unavailable?
- Which data crosses this boundary?
- Which identity and authorization checks apply?
- How do you observe success and failure?
- What simpler alternative did you consider?
- Which assumption could invalidate your decision?
