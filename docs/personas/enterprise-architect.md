# Persona: Enterprise Architect

## Role Overview

**Common Titles:** Enterprise Architect, Chief Architect, Solution Architect, Domain Architect, Principal Architect, VP of Architecture
**Reports To:** CTO, CIO, or VP of Engineering
**Sphere of Influence:** Cuts across all IT domains — application, infrastructure, data, security, integration

---

## Background Profile

Typically 15–25 years of experience with deep roots in software engineering, infrastructure, or systems design. Has worked across multiple technology generations and organizational scales. Often holds certifications in TOGAF, Zachman, AWS/Azure/GCP Solutions Architect, or similar. Thinks in systems — understanding how components interact, where dependencies create fragility, and how decisions made today constrain tomorrow. Equal parts technical expert and diplomat, since architecture only succeeds if stakeholders adopt it.

---

## Core Knowledge Domains

- Enterprise architecture frameworks (TOGAF, Zachman, FEAF)
- Application architecture patterns (microservices, event-driven, hexagonal, CQRS)
- Integration patterns and API design (REST, GraphQL, gRPC, event streaming)
- Data architecture and information management (data mesh, data lakehouse, MDM)
- Cloud architecture and multi-cloud strategy
- Infrastructure as code and platform engineering
- Security architecture (zero trust, defense in depth)
- Technology roadmap planning and portfolio rationalization
- Technical debt assessment and modernization strategies
- Architecture governance and review boards

---

## Primary Goals & Objectives

1. **Ensure coherence** — prevent the organization from building incompatible, siloed systems
2. **Enable business agility** — design systems that can change quickly without cascading failures
3. **Reduce technical debt** — identify and prioritize modernization of high-risk legacy components
4. **Define standards and guardrails** — establish patterns that teams can follow independently
5. **Bridge business and technology** — translate business requirements into technical architectures
6. **Manage platform risk** — identify single points of failure, vendor lock-in, and capacity risks
7. **Enable reuse** — prevent the organization from rebuilding the same capabilities repeatedly

---

## Pain Points & Frustrations

- Teams making local decisions that create global problems
- Architecture reviews being seen as a bureaucratic speed bump
- Business units buying point solutions that create integration debt
- New initiatives that don't follow established patterns or consult the architecture team
- Legacy systems that can't be changed without unpredictable ripple effects
- Pressure to make architectural compromises for short-term delivery speed
- Architecture becoming a "shelfware" document nobody follows
- Cloud migrations that lift-and-shift without re-architecting for cloud-native benefits

---

## Decision-Making Style

**Systemic thinker:** Evaluates decisions based on second- and third-order effects, not just immediate outcomes
**Pattern-first:** Prefers to establish reusable patterns over one-off solutions
**Long-horizon:** Thinks in 3–5 year roadmaps while balancing immediate delivery needs
**Evidence-based:** Relies on architectural patterns, RFC processes, and Architecture Decision Records (ADRs)
**Consensus-seeker:** Architecture decisions affect many teams, so alignment is critical before commitment

---

## Communication Preferences

- **Diagrams over prose** — C4 model, architecture diagrams, sequence diagrams communicate more than paragraphs
- **Show the context first** — place any component or decision in the larger system context before diving into detail
- **Acknowledge tradeoffs explicitly** — they don't trust anyone who claims a solution has no downsides
- **Reference established patterns** — cite Martin Fowler, AWS Well-Architected Framework, TOGAF where relevant
- **SCQA works well** — they appreciate structured argumentation with clear problem statements
- **SWOT for options analysis** — evaluating architectural alternatives benefits from structured tradeoff analysis

---

## Best Framing Approaches

| Situation | Recommended Format |
|-----------|-------------------|
| New system or service proposal | **SCQA** + architecture diagram |
| Technology selection decision | **SWOT** per option + recommendation |
| Architecture review finding | **PEEL** (Point → Evidence → Explain → Link to architectural principle) |
| Modernization roadmap | **Now, Next, Later** + dependency mapping |
| Technical debt prioritization | **What, So What, Now What** + risk matrix |

**SCQA example for architecture proposal:**
> *Situation:* We have 14 teams each building their own notification capabilities.
> *Complication:* Customer experience is inconsistent, and we're spending ~$800K/year in duplicated effort.
> *Question:* Should we build a shared notification platform, buy a SaaS solution, or continue with team-owned solutions?
> *Answer:* We recommend a shared internal platform built on an event-driven model that consolidates delivery and provides a consistent API.

**SWOT example for technology selection:**
> Evaluating Kafka vs. Pulsar for event streaming:
> Kafka Strengths: Mature ecosystem, widespread team familiarity, strong community
> Kafka Weaknesses: Operational complexity, Zookeeper dependency (legacy), storage-compute coupling
> Pulsar Opportunities: Native multi-tenancy, tiered storage, geo-replication
> Pulsar Threats: Smaller ecosystem, fewer internal skill sets, vendor support maturity

---

## Key Vocabulary (Use These Terms)

- Separation of concerns, loose coupling, high cohesion
- Architecture Decision Record (ADR), Architecture Review Board (ARB)
- Reference architecture, target state architecture, current state (AS-IS vs. TO-BE)
- Non-functional requirements (NFRs): scalability, reliability, observability, maintainability
- Technical debt, modernization, strangler fig pattern
- Domain-driven design (DDD), bounded context, ubiquitous language
- Event-driven architecture (EDA), choreography vs. orchestration
- API contract, schema registry, backward compatibility
- Platform engineering, developer experience (DX)
- Fitness functions, architectural runway

---

## Motivators

- **Elegant, coherent systems** — the intellectual satisfaction of well-designed architecture
- **Adoption of standards** — knowing that teams follow the patterns they established
- **Being consulted early** — included in project inception, not called in to fix problems
- **Business outcomes** — seeing that architectural decisions enabled measurable business results
- **Learning opportunities** — evaluating new technologies and advancing the organization's technical capability
- **Influence without authority** — architecture's unique challenge; they want to be respected, not just tolerated

---

## Common Objections

- *"We don't have time for an architecture review."* — Propose lightweight review for low-risk, full review for high-risk
- *"We've already committed to this technology."* — Provide migration path and guardrails to minimize damage
- *"That's too complex."* — Show the simplicity of the proposed pattern; complexity is in the problem, not the solution
- *"Each team should own their own stack."* — Distinguish between team autonomy and organizational coherence
- *"The vendor says it integrates with everything."* — Probe integration depth; marketing claims rarely match technical reality

---

## What to Avoid

- Proposing architectural changes without understanding existing systems and constraints
- Advocating for a technology because it's new or popular, not because it solves the problem
- Architecture documents that exist as PDFs and are never operationalized as standards
- Skipping the "why" — architecture decisions without documented rationale erode trust
- Treating architecture as a solo activity; alignment with security, data, and engineering is non-negotiable
