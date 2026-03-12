# Enterprise Personas Index

A reference library of key enterprise stakeholder personas — their knowledge domains, goals, communication preferences, and how to frame information effectively for each audience.

---

## Personas

| Persona | File | Primary Framing Format |
|---------|------|----------------------|
| [IT Executive](#it-executive) | [it-executive.md](it-executive.md) | BLUF, SCQA |
| [Cyber Security Expert](#cyber-security-expert) | [cyber-security-expert.md](cyber-security-expert.md) | PEEL, Five Whys |
| [Enterprise Architect](#enterprise-architect) | [enterprise-architect.md](enterprise-architect.md) | SCQA, SWOT |
| [Engineer](#engineer) | [engineer.md](engineer.md) | Five Whys, Now-Next-Later |
| [Business Requestor](#business-requestor) | [business-requestor.md](business-requestor.md) | AIDA, PAR |
| [Governance, Risk & Compliance](#grc) | [governance-risk-compliance.md](governance-risk-compliance.md) | PEEL, PAR |
| [Legal](#legal) | [legal.md](legal.md) | PEEL, SCQA |
| [AI Expert / AI Executive](#ai-expert) | [ai-expert.md](ai-expert.md) | SCQA, AIDA |

---

## Format-to-Persona Mapping

Which communication formats from `docs/formats/` work best for each persona:

| Format | Best Personas | Why |
|--------|--------------|-----|
| **BLUF** | IT Executive, Legal (time-sensitive) | Executives are time-constrained; lead with the decision/recommendation |
| **SCQA** | IT Executive, Enterprise Architect, Business Requestor, Legal | Structured problem → solution narrative; works for complex decisions |
| **AIDA** | Business Requestor, AI Expert | Persuasion/adoption framing; works when building enthusiasm for change |
| **PEEL** | Cyber Security Expert, GRC, Legal | Evidence-based argument with regulatory or risk linkage |
| **Five Whys** | Engineer, Cyber Security Expert | Root cause analysis; technical depth valued; blame-free inquiry |
| **PAR** | GRC, Business Requestor, Enterprise Architect | Outcome documentation; proves impact and remediation |
| **STAR** | Engineer, Business Requestor | Behavioral/achievement storytelling; separates role from context |
| **SWOT** | Enterprise Architect, GRC, IT Executive | Options analysis with structured tradeoffs |
| **Now-Next-Later** | Engineer, Business Requestor, IT Executive | Prioritization clarity without over-committing to timelines |
| **What-So-What-Now-What** | Engineer, GRC, Business Requestor | Retrospective and incident review framing |
| **GROW** | Engineer (coaching), Business Requestor (goal alignment) | Goal-setting and coaching conversations |

---

## Quick Reference: Framing by Situation

### Proposing a new initiative
- **To IT Executive:** BLUF + business case (cost/risk/revenue impact)
- **To Business Requestor:** AIDA (hook with the problem they feel)
- **To Enterprise Architect:** SCQA + architecture diagram
- **To GRC:** PEEL + control mapping
- **To Legal:** SCQA + data flow + DPA status
- **To Engineer:** Direct requirements with context; Five Whys on why existing approach falls short
- **To AI Expert:** SCQA + capability/limitation framing

### Escalating a risk or problem
- **To IT Executive:** BLUF — state the risk, business impact, and recommended action first
- **To Cyber Security Expert:** PEEL — finding, CVE/evidence, blast radius, remediation
- **To GRC:** PEEL — control gap, evidence, regulatory linkage, remediation timeline
- **To Legal:** SCQA — situation, legal complication, question to resolve, recommended action
- **To Enterprise Architect:** What-So-What-Now-What — system impact, architectural implications, proposed fix

### Requesting approval or sign-off
- **To IT Executive:** BLUF with 2–3 options and recommended choice
- **To Business Requestor:** PAR — show the problem, proposed action, expected result
- **To GRC:** Evidence package — policy, design doc, control mapping, test evidence
- **To Legal:** Complete technical description + privacy/contract analysis

---

## Persona Quick Profiles

### IT Executive
- **Wants:** Business outcomes, risk reduction, cost efficiency
- **Speaks:** ROI, TCO, transformation, alignment
- **Fears:** Board-level surprises, operational disruption, budget overruns
- **Best hook:** Dollar figures and competitive risk

### Cyber Security Expert
- **Wants:** Reduced attack surface, faster detection, shift-left security
- **Speaks:** CVE, MITRE ATT&CK, blast radius, zero trust
- **Fears:** Undetected breaches, shadow IT blind spots, compliance without security
- **Best hook:** Threat scenario with blast radius

### Enterprise Architect
- **Wants:** Coherent systems, reusable patterns, reduced technical debt
- **Speaks:** ADR, bounded context, reference architecture, NFRs
- **Fears:** Siloed decisions creating global problems, unreviewed integrations
- **Best hook:** How this aligns with (or risks) the target state architecture

### Engineer
- **Wants:** Ownership, interesting problems, clean code, stability
- **Speaks:** PR, CI/CD, p99, refactor, test coverage
- **Fears:** Changing requirements, technical debt blocking progress, being told how to implement
- **Best hook:** The technical challenge and the autonomy to solve it

### Business Requestor
- **Wants:** Problem solved, on time, adopted by users, ROI justified
- **Speaks:** KPIs, user adoption, milestones, go-live, compliance
- **Fears:** IT solving the wrong problem, delays, disruption to operations
- **Best hook:** Quantify the current pain in their business terms

### Governance, Risk & Compliance (GRC)
- **Wants:** Documented controls, audit-ready evidence, clean findings
- **Speaks:** ITGC, risk appetite, SOC 2, residual risk, remediation
- **Fears:** Undocumented control gaps, repeat findings, regulatory exposure
- **Best hook:** The audit or regulatory consequence of not acting

### Legal
- **Wants:** Liability minimized, obligations met, contracts watertight
- **Speaks:** DPA, indemnification, lawful basis, regulatory exposure
- **Fears:** Undisclosed data processing, unreviewed contracts, breach notification failures
- **Best hook:** Specific regulatory citation and liability exposure

### AI Expert / AI Executive
- **Wants:** AI adoption, capability enablement, responsible deployment
- **Speaks:** LLM, RAG, fine-tuning, inference, responsible AI, AI governance
- **Fears:** AI washing, governance gaps that block deployment, missed competitive opportunity
- **Best hook:** Concrete capability demonstration with clear governance approach
