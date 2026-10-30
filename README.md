# Applied Application Architecture: From Idea to Cloud

Repository name: `applied_application_architecture`

## Course overview

This course teaches you to reason about complete IT systems instead of isolated
products. You will learn how users, networks, applications, data, identity,
infrastructure, security, and operations work together. The course uses one
continuous case: the fictional **Northstar Workplace Learning Hub**, a platform
for managing internships and workplace learning.

The domain is inspired by the type of integrated internship process supported
by [OnStage](https://www.onstagesoftware.com/en), including placement,
guidance, documents, progress, assessment, and collaboration with external
organisations. The course project is an independent fictional implementation;
it does not copy the OnStage interface, source code, branding, or private data.

Architecture is not a list of technologies. It is a set of important decisions
about responsibilities, boundaries, relationships, and trade-offs. By the end
of the course, you should be able to explain why each major component exists,
trace a user request through the system, predict the impact of failures, and
defend a design with evidence.

## Learning outcomes

After completing the course, you can:

- distinguish functional requirements from quality attributes and constraints;
- turn user journeys into simple wireframes, mock-ups, stories, and API needs;
- map a user journey to components, dependencies, protocols, and data flows;
- explain the roles of clients, DNS, proxies, applications, APIs, databases,
  object storage, queues, and identity providers;
- compare physical servers, virtual machines, containers, and managed services;
- identify trust boundaries and apply authentication, authorization, least
  privilege, safe secret handling, and defence in depth;
- reason about scalability, availability, recovery, and observability;
- create readable context, container, deployment, and sequence diagrams;
- document a significant decision in an Architecture Decision Record; and
- review an AI-generated architecture critically instead of accepting it as fact.

## Course structure

| Module | Topic | Matching lab |
| --- | --- | --- |
| Foundation | [From idea to secure implementation](course/00-from-idea-to-implementation.md) | [Shape a secure delivery plan](hands-on/00-from-idea-to-implementation.md) |
| 1 | [Systems thinking and architecture](course/01-systems-thinking.md) | [Map the system](hands-on/01-map-the-system.md) |
| 2 | [Networks and communication](course/02-networks-and-communication.md) | [Trace a web request](hands-on/02-trace-a-web-request.md) |
| 3 | [Applications, APIs, and data](course/03-applications-apis-and-data.md) | [Model an application flow](hands-on/03-model-an-application-flow.md) |
| 4 | [Infrastructure, cloud, and delivery](course/04-infrastructure-cloud-and-delivery.md) | [Compare deployment options](hands-on/04-compare-deployment-options.md) |
| 5 | [Identity and security by design](course/05-identity-and-security.md) | [Threat-model the platform](hands-on/05-threat-model-the-platform.md) |
| 6 | [Scalability, reliability, and observability](course/06-reliability-and-observability.md) | [Diagnose an incident](hands-on/06-diagnose-an-incident.md) |
| 7 | [Architecture views and decisions](course/07-views-and-decisions.md) | [Create views and an ADR](hands-on/07-create-views-and-an-adr.md) |
| Implementation | [From first vertical slice to production](course/10-implementation-journey.md) | [Working end project](project/README.md) |
| Deployment | [Docker from local test to cloud](course/11-containers-local-to-cloud.md) | [Docker-to-cloud lab](hands-on/08-docker-local-to-cloud.md) |
| Final | [Capstone and critical AI review](course/12-capstone-and-ai-review.md) | [Defend the implemented architecture](hands-on/09-capstone.md) |

Use the [course roadmap](course/00-course-roadmap.md) and the
[hands-on overview](hands-on/00-overview.md) to plan your work. The
[glossary](course/09-glossary.md) provides concise definitions.

## Study method

Treat each lesson and its lab as one learning unit.

1. **Understand.** Read the lesson, study the diagrams, and explain each
   component and relationship in your own words.
2. **Predict.** Before revealing or running anything, predict the outcome.
3. **Apply.** Complete the matching hands-on lab using the case study.
4. **Verify.** Compare your result with the checkpoint and, only after a serious
   attempt, the reference solution.
5. **Reflect.** Record what your design improves, what it costs, and which risk
   remains.

There is rarely one universally correct architecture. A strong answer states
its assumptions, connects choices to requirements, and acknowledges
consequences.

## Practice environment and safety

The design labs require only a text editor and a Markdown viewer that supports
Mermaid, such as GitHub. The request-tracing lab also uses browser developer
tools, `nslookup` or `dig`, and `curl`. Use only the provided public test target
or an instructor-approved system.

Never scan, stress-test, reconfigure, or attempt to bypass access controls on a
system without explicit permission. Do not place real credentials, tokens, or
personal data in course files.

## Viewing the course as a website

The repository includes a Docsify entry point. When published with GitHub Pages,
open `index.html` through the site URL. For local viewing, serve the repository
with any local static-file server; opening it directly with a `file://` URL may
prevent navigation from working.

## Progressive learning levels

The course deliberately grows in difficulty:

1. **Beginner — understand and describe.** Learn actors, user stories,
   protocols, components, data, and basic security in plain language.
2. **Developing — model and test.** Draw flows, write acceptance criteria,
   inspect requests, compare options, and identify threats.
3. **Applied — build a vertical slice.** Connect a small frontend to a backend
   API and datastore, then run the parts as local Docker containers with automated
   tests and configuration per environment.
4. **Integrated — deliver securely.** Add DTAP promotion, pipeline checks, an
   externally accessible cloud deployment, observability, recovery, and
   architecture evidence.
5. **Independent — defend and improve.** Explain trade-offs, diagnose failure,
   review AI suggestions, and justify the implemented solution.

Students are never asked to build the complete platform at once. The
[implementation journey](course/10-implementation-journey.md) and
[end project](project/README.md) split it into small, demonstrable increments.

## Assessment

Use the [review questions and capstone rubric](evaluation/questions-and-rubric.md)
to prepare for assessment. Your diagrams are evidence of reasoning, not a
substitute for it: you must be able to explain each box, arrow, boundary, and
trade-off.

## License

Unless noted otherwise, course content is licensed under
[CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/).

<small>Course development by Dominique Houbrechts, PXL.</small>
