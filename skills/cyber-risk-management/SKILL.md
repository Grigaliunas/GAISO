---
name: cyber-risk-management
description: CISO function F3 — assess cyber-risk maturity, identify gaps in cyber strategy and generate improvement recommendations. Use when the CISO needs a maturity review, a board-level strategy gap analysis, or a prioritised list of strategic improvements.
license: CC-BY-NC-ND-4.0
---

# F3 — Cyber-Risk Management and Maturity Assessment

Assess cyber-risk maturity, identify strategy gaps, and draft improvement recommendations grounded in a named framework (NIST CSF 2.0, ISO/IEC 27001/27002, CIS Controls v8.1, DORA for financial entities).

## Function mapping (GAISO T3.1)

- **Domain**: Cyber risk management and compliance.
- **ISO/IEC 27002:2022 controls**: **O1** Policies for information security, **O35** Independent review of information security, **O36** Compliance with policies, rules and standards; **T8** Management of technical vulnerabilities, **T9** Configuration management, **T29** Security testing in development and acceptance.
- **Regulations**: NIS2 Art. 21 (risk-management measures), Commission Implementing Regulation (EU) 2024/2690 Annex, AI Act Art. 9 (risk management system), CER Directive Art. 13, Cyber Resilience Act Art. 13.

## Inputs you must demand

1. **Governing framework** — NIST CSF 2.0 / ISO 27001 / CIS v8.1 / DORA. If the user does not name one, ask.
2. **Scope** — entity, subsidiaries in scope, geographies.
3. **Evidence** — policy inventory, last audit findings, prior maturity scores, control-test results.
4. **Sector and size** — for NIS2 classification (important vs. essential).
5. **Period** — current assessment window.

If any are missing, stop and ask. Do not guess. Guessing changes the control set, the threshold, and the regulator.

## Procedure

1. **Inventory controls in scope**. List the control families from the named framework.
2. **For each family**, score current maturity on the framework's own scale (NIST CSF tiers 1–4; ISO 27001 PDCA evidence levels; CIS implementation groups IG1–IG3).
3. **Identify gap** against the target level defined by regulation or board risk appetite. If the target is not provided, use the regulation minimum (NIS2 Art. 21 baseline for essential entities; AI Act Art. 9 for GenAI-related systems).
4. **Recommend** the smallest set of actions that closes each gap. Every recommendation must name:
   - the ISO/IEC 27002:2022 control it restores,
   - the responsible role,
   - a measurable completion criterion,
   - a target horizon (0–3 / 3–6 / 6–12 months).
5. **Rank** by (risk reduction) / (effort), not by comfort. Flag board-level risks separately.
6. **Emit** the deliverable, then the OVB.

## Default output format

```
| Control family | Current (1–5) | Target | Gap | Recommendation | Owner | Horizon | 27002 control |
```

Follow the table with a one-paragraph executive narrative naming the top three strategic risks.

## Pitfalls

- **Benchmarking with invented peers**. Never cite "sector average maturity" unless the data is in the provided context. If you must, flag as PARAMETRIC in the OVB.
- **Over-optimistic scoring**. Without evidence, scoring defaults to the lower of the plausible range.
- **Framework mixing**. Do not translate NIST scores into ISO language mid-document — pick one or map explicitly in an appendix.
- **Confusing maturity with compliance**. A control can be mature and still non-compliant, and vice versa. Score them separately.
- **Horizon inflation**. Anything longer than 12 months should be broken into a shorter milestone.

## Escalation

If the assessment reveals a control gap that, on its own, would fail NIS2 Art. 21 minimum or AI Act Art. 9 for a GenAI system already in production, stop the deliverable and raise as a finding that the CISO must acknowledge before the report is finalised.

## Cross-references

- `regulatory-compliance-mapping` — when the gap analysis leads to a control-to-regulation mapping (F2).
- `security-test-scenarios` — when the remediation plan requires controls to be validated (F9).
- `vulnerability-prioritization` — when technical debt is a dominant driver (F10).

## Output footer

Append the Output Verification Block. `Human review` = `CISO`. If DORA is in scope, add `Management Body` per DORA Art. 5.
