# Persona: Governance, Risk & Compliance (GRC)

## Role Overview

**Common Titles:** Chief Risk Officer (CRO), VP of Compliance, Director of GRC, IT Risk Manager, Compliance Manager, Internal Audit Director, Risk and Controls Lead
**Reports To:** CFO, General Counsel, CEO, or Board Audit Committee
**Sphere of Influence:** Policy, controls, audit readiness, regulatory posture, third-party risk

---

## Background Profile

Background in audit, finance, law, or information security with 10–20 years of experience. Often holds certifications such as CISA, CISM, CRISC, CIA (Certified Internal Auditor), or CGEIT. Has deep familiarity with regulatory frameworks and control standards — they read the actual regulatory text, not summaries. Typically operates in a tension between enabling the business and maintaining controls. Lives with the consequences of control failures: audit findings, regulatory fines, reputational damage. Increasingly required to also understand technology deeply enough to assess IT controls and cloud risk.

---

## Core Knowledge Domains

- Regulatory frameworks: SOX, HIPAA, GDPR, CCPA, PCI-DSS, DORA, FedRAMP, CMMC
- Control frameworks: NIST CSF, ISO 27001, CIS Controls, COBIT, COSO
- IT General Controls (ITGCs): access management, change management, availability, data integrity
- Third-party risk management (TPRM) and vendor due diligence
- Risk quantification: RCSA (Risk and Control Self-Assessment), FAIR methodology
- Audit lifecycle: planning, fieldwork, findings, remediation, reporting
- Data governance and privacy compliance
- Policy and procedure development and governance
- Business continuity and disaster recovery from a compliance perspective
- Records management and e-discovery

---

## Primary Goals & Objectives

1. **Ensure the organization meets regulatory and contractual obligations** — pass audits, avoid fines
2. **Maintain a defensible risk posture** — document and evidence the controls that are in place
3. **Reduce the likelihood and impact of control failures** — prevent audit findings before they occur
4. **Embed risk and compliance into business processes** — not as a reactive function, but proactively
5. **Provide the board and leadership accurate risk visibility** — no surprises, clear risk appetite alignment
6. **Manage third-party risk** — ensure vendors and partners don't introduce compliance exposure
7. **Respond effectively when things go wrong** — breach notifications, incident reporting, regulator communication

---

## Pain Points & Frustrations

- Technology changes deployed without controls review (shadow IT, unapproved tools)
- Lack of evidence for controls that "everyone knows are in place" but aren't documented
- IT teams treating compliance as a box-checking exercise rather than genuine risk management
- Audit season being the only time controls are actually tested
- Regulatory requirements changing faster than controls can be updated
- Inadequate access reviews — accounts and permissions that persist long after they should have been removed
- Data stored in places nobody knows about, creating undisclosed compliance exposure
- Projects going live without a compliance sign-off, creating retroactive remediation work
- Vendors claiming compliance certifications that don't actually cover the services being used

---

## Decision-Making Style

**Evidence-first:** Every control assertion must be supported by documented evidence — policies, logs, screenshots, configurations
**Conservative:** When in doubt, defaults to the more controlled approach; the cost of a missed control exceeds the cost of excessive caution
**Framework-anchored:** Evaluates decisions against recognized standards (NIST, ISO, COBIT) as authoritative references
**Audit-lens thinking:** Constantly asks "how would an auditor view this?"
**Collaborative but firm:** Will work with teams to find compliant paths forward, but will not waive requirements without documented risk acceptance

---

## Communication Preferences

- **Be specific and documented** — "we believe controls are in place" is not acceptable; show the evidence
- **Use the framework language they know** — reference NIST controls by identifier, cite SOX section numbers, use COBIT terminology
- **PEEL format is ideal** — assertion, evidence, explanation, link to regulatory or policy requirement
- **Control mapping is key** — show how a system or process maps to specific control objectives
- **Risk acceptance documentation** — if proposing to accept rather than mitigate a risk, provide a formal risk acceptance memo
- **Timeline clarity** — remediation commitments must have realistic, documented due dates with owners

---

## Best Framing Approaches

| Situation | Recommended Format |
|-----------|-------------------|
| Presenting a compliance gap | **PEEL** (finding → evidence → risk implication → regulatory linkage) |
| Risk assessment report | **SWOT** + risk register |
| Audit finding remediation plan | **PAR** (Problem → Action → Result) with timelines |
| Policy change proposal | **SCQA** (why now, what's the risk, what do we need to decide, what's recommended) |
| Control effectiveness review | **What, So What, Now What** |

**PEEL example (compliance gap):**
> *Point:* Privileged access accounts are not reviewed on the required quarterly cycle.
> *Evidence:* The last access review was completed 9 months ago per the access management log; our policy requires quarterly review.
> *Explain:* Stale privileged accounts represent a material risk under NIST AC-2 and are a recurring finding category in SOC 2 audits.
> *Link:* This is a direct SOX ITGC finding under the access management control domain and will be flagged in Q3 audit if not remediated.

**PAR example (remediation summary):**
> *Problem:* Encryption at rest was not configured for three S3 buckets containing PII, creating a GDPR Article 32 gap.
> *Action:* Enabled default AES-256 encryption on all affected buckets; implemented a detective control (AWS Config rule) to alert on unencrypted bucket creation going forward; updated the data asset registry.
> *Result:* All PII storage is now encrypted at rest. Preventive and detective controls in place. Evidence package prepared for auditor review.

---

## Key Vocabulary (Use These Terms)

- Control objective, control activity, control effectiveness
- Audit finding, deficiency, material weakness
- Risk appetite, risk tolerance, residual risk
- Evidence, documentation, audit trail
- Remediation, compensating control, risk acceptance
- ITGC (IT General Controls), application controls
- SOC 1 / SOC 2 Type I / Type II
- Data classification, data inventory, data mapping
- Third-party risk, vendor assessment, right-to-audit
- Change management controls, segregation of duties (SoD)

---

## Motivators

- **Clean audit results** — no findings, no repeat findings
- **Regulatory confidence** — knowing the organization can survive a regulatory examination
- **Risk visibility** — accurate, current picture of the organization's risk posture
- **Process maturity** — controls that are embedded in daily operations, not just test-season theater
- **Partnership with IT and business** — being consulted proactively, not just brought in after the fact
- **Protecting the organization** — genuinely motivated by preventing harm — financial, reputational, legal

---

## Common Objections

- *"We're already compliant with that."* — Request the evidence; assertion is not compliance
- *"That control doesn't apply to us."* — Requires a documented scoping decision, not a verbal claim
- *"We'll fix it after the audit."* — Escalate: this creates deliberate control failures with known risk
- *"We don't have time to do a controls review."* — Frame the cost: retroactive remediation is far more expensive
- *"Other companies don't do this."* — GRC doesn't follow peer behavior; they follow regulatory text

---

## What to Avoid

- Presenting undocumented claims of compliance ("we do that already")
- Requesting compliance sign-off without providing evidence and design documentation
- Treating GRC as a formality to be completed after implementation decisions are locked in
- Skipping change management controls for "urgent" deployments — this is a top audit finding category
- Confusing compliance with security — compliance is necessary but not sufficient for security
- Making risk acceptance decisions without formal documentation and appropriate authority level
