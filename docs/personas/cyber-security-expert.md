# Persona: Cyber Security Expert

## Role Overview

**Common Titles:** CISO, VP of Cybersecurity, Security Architect, Director of Information Security, Security Engineering Lead
**Reports To:** CIO, CTO, COO, or directly to CEO/Board (in mature orgs)
**Direct Reports:** Security engineers, SOC analysts, penetration testers, security architects, GRC team

---

## Background Profile

Typically 10–20 years in security, often starting as a network engineer, systems administrator, or software developer before specializing. May hold certifications such as CISSP, CISM, CISA, CEH, OSCP, or cloud security certs (AWS Security Specialty, CCSP). Deeply technical at their core but increasingly required to communicate risk in business language. Has lived through real incidents — breaches, ransomware, audit failures — which shape a threat-first worldview. Reads threat intelligence feeds, tracks CVEs, and follows APT group activity as a professional habit.

---

## Core Knowledge Domains

- Threat intelligence and threat modeling (MITRE ATT&CK, STRIDE)
- Vulnerability management and patch cycles
- Identity and access management (IAM/PAM/Zero Trust)
- Security operations (SIEM, SOAR, EDR, NDR)
- Application security (SAST, DAST, OWASP Top 10, secure SDLC)
- Cloud security (CSPM, CWPP, shared responsibility model)
- Regulatory compliance (NIST CSF, ISO 27001, SOC 2, PCI-DSS, HIPAA, GDPR)
- Incident response and digital forensics
- Red team / blue team operations
- Security architecture patterns (zero trust, defense in depth, microsegmentation)

---

## Primary Goals & Objectives

1. **Reduce the organization's attack surface** — minimize exploitable vulnerabilities and exposure
2. **Detect and respond faster** — shrink mean time to detect (MTTD) and mean time to respond (MTTR)
3. **Build security into the SDLC** — shift security left so it's not a gating bottleneck at the end
4. **Achieve and maintain compliance** — pass audits, maintain certifications, satisfy regulators
5. **Educate and influence** — make every engineer and employee a security-aware stakeholder
6. **Justify security investment** — translate risk into financial exposure to secure budget
7. **Protect the organization from reputational and financial harm** — the real cost is a breach

---

## Pain Points & Frustrations

- Engineers shipping insecure code because security is seen as someone else's job
- Shadow IT and unmanaged assets creating blind spots
- Alert fatigue — too many false positives drowning out real threats
- Security being brought in at the end of a project, not the beginning
- Business pressure to go faster overriding security controls
- Leadership treating security as a compliance checkbox, not a risk discipline
- Vendors selling "silver bullet" security tools that require significant tuning
- Budget allocated to compliance theater instead of actual risk reduction

---

## Decision-Making Style

**Evidence-driven:** Makes decisions based on threat data, vulnerability scores (CVSS), and risk assessments — not gut feel
**Risk quantification:** Increasingly uses frameworks like FAIR (Factor Analysis of Information Risk) to express risk in dollar terms
**Worst-case-first thinker:** Defaults to asking "what's the worst that could happen?" before approving anything
**Adversarial mindset:** Evaluates every decision by asking "how would an attacker exploit this?"
**Consensus with caution:** Will escalate and block if risk isn't addressed, but prefers to enable with guardrails over blocking outright

---

## Communication Preferences

- **Lead with risk, not features** — frame everything in terms of what could go wrong and likelihood
- **Use threat scenarios** — "an attacker who gains access to X can do Y, resulting in Z impact"
- **Cite standards and frameworks** — references to NIST, MITRE ATT&CK, and CIS Controls add credibility
- **Show the blast radius** — what systems, data, and processes are affected if this goes wrong
- **PEEL format works well** — make a point, show evidence (CVE data, threat intel), explain the implication, link to business risk
- **Don't oversimplify** — unlike executives, security experts appreciate technical depth

---

## Best Framing Approaches

| Situation | Recommended Format |
|-----------|-------------------|
| Presenting a vulnerability | **PEEL** (Point → Evidence → Explain → Link to business risk) |
| Incident debrief | **Five Whys** (root cause analysis) |
| Security architecture proposal | **SCQA** + threat model |
| Security awareness request | **What, So What, Now What** |
| Risk prioritization | **SWOT** or risk matrix |

**PEEL example framing:**
> *Point:* Our API authentication layer has a critical misconfiguration.
> *Evidence:* CVE-2024-XXXX affects our current JWT implementation; confirmed in scanning results from [date].
> *Explain:* An unauthenticated attacker can forge tokens and access customer PII across all tenants.
> *Link:* This is a P0 finding under our SOC 2 controls and a GDPR breach notification trigger if exploited.

**Five Whys example (post-incident):**
> Why did the breach occur? → Unpatched system.
> Why was it unpatched? → Not in the asset inventory.
> Why wasn't it in inventory? → Deployed via shadow IT.
> Why was shadow IT allowed? → No enforced provisioning controls.
> Why no controls? → Policy existed but was never enforced technically.

---

## Key Vocabulary (Use These Terms)

- Attack surface, threat vector, threat actor, adversary
- Blast radius, lateral movement, privilege escalation
- Zero trust, least privilege, defense in depth
- CVE, CVSS score, vulnerability, exploit
- MTTD, MTTR, mean time to contain
- Compensating control, detective control, preventive control
- Risk appetite, residual risk, risk acceptance
- Shift left, DevSecOps, security by design
- MITRE ATT&CK, kill chain, TTP (Tactics, Techniques, Procedures)
- Crown jewel assets, data classification

---

## Motivators

- **Preventing a breach** — nothing motivates them more than keeping the organization safe
- **Being included early** — respected as a partner in design, not a reviewer at the end
- **Accurate threat intelligence** — access to current, credible data on what's actually happening
- **Measurable risk reduction** — seeing the metrics move in the right direction
- **Influencing culture** — making security a shared responsibility, not a security team problem
- **Technical excellence** — being able to implement elegant, effective controls

---

## Common Objections

- *"That will slow down development."* — Address with automation and guardrails that enable speed safely
- *"The risk is acceptable."* — They want to see who accepted the risk and with what documentation
- *"We've never been breached."* — They know this means nothing; use data on similar org breaches
- *"That's overkill for our threat profile."* — Show the threat model that backs the recommendation
- *"We'll address it in the next sprint."* — Requires clear SLAs on remediation timelines

---

## What to Avoid

- Presenting security as a compliance exercise rather than a risk discipline
- Proposing solutions without a threat model or security architecture review
- Bypassing security controls under schedule pressure without documented risk acceptance
- Oversimplifying security risk as "low/medium/high" without quantification
- Treating the security team as a gating body rather than a collaborative partner
