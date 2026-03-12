# Persona: Engineer

## Role Overview

**Common Titles:** Software Engineer, Senior Software Engineer, Staff Engineer, Platform Engineer, DevOps Engineer, Site Reliability Engineer (SRE), Backend Engineer, Full-Stack Engineer, Infrastructure Engineer
**Reports To:** Engineering Manager or Tech Lead
**Sphere of Influence:** Implementation quality, delivery velocity, system reliability, technical decisions within the team

---

## Background Profile

Typically 2–15 years of hands-on engineering experience. Background varies — CS degree, bootcamp, self-taught, or domain-specific (embedded, data, infrastructure). Deeply focused on their technical domain. Reads documentation, browses GitHub repositories, follows engineering blogs (e.g., Netflix Tech Blog, Stripe Engineering). Values craftsmanship and takes pride in code quality. Increasingly expected to own systems end-to-end, including deployment, monitoring, and on-call responsibilities. May be skeptical of top-down mandates that don't make technical sense.

**Seniority spectrum matters:**
- **Junior:** Needs clear direction, focused tasks, mentorship
- **Mid-level:** Owns features end-to-end, increasing autonomy
- **Senior:** Mentors others, influences design, navigates ambiguity
- **Staff/Principal:** Cross-team technical leadership, sets engineering standards

---

## Core Knowledge Domains

- Programming languages and frameworks relevant to their stack
- Software design patterns and principles (SOLID, DRY, clean code)
- Version control and branching strategies (Git, trunk-based development)
- CI/CD pipelines and deployment automation
- Testing strategies (unit, integration, contract, end-to-end)
- Observability: logging, metrics, tracing (e.g., Prometheus, Grafana, Datadog, OpenTelemetry)
- Cloud platforms and managed services (AWS, GCP, Azure)
- Infrastructure as code (Terraform, Pulumi, CDK)
- Security fundamentals (OWASP, secrets management, least privilege)
- Performance optimization and capacity planning

---

## Primary Goals & Objectives

1. **Ship quality code on time** — deliver features and fixes without introducing regressions
2. **Maintain and improve system reliability** — keep services running, reduce toil
3. **Grow technically** — learn new skills, tools, and approaches
4. **Reduce friction in the development workflow** — better tooling, faster feedback loops
5. **Solve interesting problems** — engineers are motivated by technical challenge
6. **Have autonomy** — be trusted to make technical decisions within their scope
7. **Work in a well-functioning team** — good processes, psychological safety, clear priorities

---

## Pain Points & Frustrations

- Unclear or constantly changing requirements that cause rework
- Accumulated technical debt that makes every change painful
- Insufficient test coverage making deployments risky
- Overly bureaucratic processes that don't seem to add value
- Being asked to cut corners on quality for speed, then blamed when things break
- Alert fatigue from poorly tuned monitoring
- Inconsistent environments between local, staging, and production
- Top-down technical mandates without understanding the implementation reality
- Context-switching across too many unrelated tasks
- Documentation that is missing, outdated, or wrong

---

## Decision-Making Style

**Pragmatic:** Makes tradeoffs between ideal solutions and practical constraints of time, complexity, and risk
**Evidence-first:** Wants to see benchmarks, test results, and runbooks — not just opinions
**Skeptical of abstractions:** Prefers concrete examples and working code over theoretical frameworks
**Iterative:** Favors small, reversible decisions over big-bang designs
**Opinionated:** Has strong views on technology choices, coding standards, and process — and will voice them

---

## Communication Preferences

- **Be concrete and specific** — show the actual code, the real error, the specific metric, not a summary
- **Respect their time** — don't schedule a meeting when a well-written ticket or async message suffices
- **Explain the "why"** — engineers resist changes they don't understand; explain the reasoning
- **Acknowledge complexity** — if a requirement is complicated, say so; don't pretend it's simple
- **Two-way conversation** — engineers want to push back and propose alternatives; make space for that
- **Five Whys for problems** — engineers respond well to systematic root cause analysis
- **What, So What, Now What for retros** — works well for post-incident reviews and retrospectives

---

## Best Framing Approaches

| Situation | Recommended Format |
|-----------|-------------------|
| Bug or incident analysis | **Five Whys** (root cause, not blame) |
| Project retrospective | **What, So What, Now What** |
| New feature request | **PAR** framing of the user problem |
| Process improvement proposal | **SCQA** with concrete before/after |
| Prioritization of tech debt | **Now, Next, Later** with impact reasoning |

**Five Whys example (incident):**
> Why did the API return 500s? → The database connection pool was exhausted.
> Why was the pool exhausted? → Connection cleanup wasn't happening correctly under load.
> Why not? → A new async code path didn't call `connection.close()` in the finally block.
> Why wasn't this caught? → No integration test covered concurrent connection behavior.
> Why? → Our test suite doesn't run concurrent scenario tests — we need to add this pattern.

**Now, Next, Later example (tech debt backlog):**
> *Now:* Fix the N+1 query causing production slowdowns (severity: P1, users affected)
> *Next:* Refactor the auth middleware to remove the shared mutable state (risk: concurrency bugs)
> *Later:* Migrate from REST polling to WebSocket for real-time updates (enables new product features)

---

## Key Vocabulary (Use These Terms)

- PR (pull request), LGTM, code review, merge conflict
- Test coverage, unit test, integration test, flaky test
- Deployment, rollback, feature flag, canary release
- Latency, throughput, p99, SLA/SLO/SLI
- Observability, logging, tracing, dashboards
- Technical debt, refactor, code smell, dead code
- CI/CD, pipeline, build, artifact, container, Docker, Kubernetes
- Environment parity, IaC, idempotent, immutable infrastructure
- Edge case, race condition, memory leak, bottleneck
- Dependency injection, interface, abstraction, coupling

---

## Motivators

- **Interesting technical problems** — challenges that require creative solutions
- **Ownership** — being trusted to design and deliver end-to-end
- **Craft** — writing clean, maintainable, elegant code
- **Impact** — seeing their work used by real users at scale
- **Learning** — opportunities to use new technologies or approaches
- **Team cohesion** — working with people they respect who are also strong engineers
- **Stability** — a codebase and process that don't create unnecessary chaos

---

## Common Objections

- *"That will break existing behavior."* — Acknowledge the risk; discuss backward compatibility or migration strategy
- *"We don't have test coverage for that."* — Agree to add tests before changing, not after
- *"That adds complexity without clear benefit."* — Justify the architectural decision with concrete examples
- *"I'd rather fix the root cause than add a workaround."* — Honor this; create space for real fixes, not just patches
- *"The requirements aren't clear enough to implement."* — This is valid; requirements need refinement before coding

---

## What to Avoid

- Dictating implementation details without understanding the technical context
- Changing priorities mid-sprint without acknowledging the cost of context switching
- Asking for estimates without sharing the complexity and constraints with the engineer
- Treating engineers as code factories — they are problem-solvers and need to be involved in shaping solutions
- Ignoring technical debt indefinitely — it erodes morale and delivery speed over time
- Delivering feedback on code quality without constructive, specific guidance
