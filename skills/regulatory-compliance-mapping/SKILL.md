---
name: regulatory-compliance-mapping
description: CISO function F2 — map existing policies, standards and procedures against industry and regulatory frameworks to meet compliance requirements. Use when drafting a compliance matrix, preparing for an audit, consolidating policy overlaps, or translating between ISO/IEC 27002 controls and EU regulatory articles.
license: CC-BY-NC-ND-4.0
---

# F2 — Policy-to-Regulation Mapping

Produce a compliance matrix that links each policy or procedure to the ISO/IEC 27002:2022 control it implements and to the specific articles of the EU regulations the control supports.

## Function mapping (GAISO T3.1)

- **Domain**: Cyber risk management and compliance.
- **ISO/IEC 27002:2022 controls**: **O31** Legal, statutory, regulatory and contractual requirements; **O36** Compliance with policies, rules and standards; **T24** Use of cryptography.
- **Regulations**: NIS2 Art. 21(2) and Art. 24, Commission Implementing Regulation (EU) 2024/2690, AI Act Art. 9 and Art. 15, GDPR Art. 24, 28, 32, CER Art. 13, Cyber Resilience Act Annex I.

## Inputs you must demand

1. **Policy / procedure inventory** (IDs, titles, short description).
2. **In-scope regulations** — at minimum NIS2, AI Act, GDPR; add CER, CRA, CSA, DORA as the sector requires.
3. **Sector and size** — drives NIS2 annex (I vs. II) and the DORA scope.
4. **Control baseline** — confirm ISO/IEC 27002:2022 as the pivot, or name the alternative (NIST SP 800-53 Rev. 5).
5. **Output audience** — internal audit, external auditor, regulator, or board. Formality differs.

## Procedure

1. **Normalise policy identifiers**. Use stable IDs (`POL-INFOSEC-001`), not file names.
2. **For each policy**, identify the ISO/IEC 27002:2022 control(s) it most directly implements. Cite the ID. When no direct match exists, mark `NO-PRIMARY-MATCH` and note the closest.
3. **Extend the control to regulation articles**. Use the mapping table in `references/iso27002-controls.md`. Prefer article-level citations, never vague "NIS2 requires".
4. **Mark gaps** — every regulation in scope that has no policy linked to it is a `GAP` row.
5. **Mark overlaps** — multiple policies mapping to the same control signals either redundancy or differing scope. Surface either way.
6. **For overlaps**, propose consolidation only when the policies materially say the same thing. Never silently merge policies that differ on roles, retention, or data categories.
7. **Emit** the matrix. Follow with a gap summary and a consolidation proposal.

## Default output format

```
| Policy ID | Policy title | ISO/IEC 27002 control | Regulation | Article | Status | Notes |
|-----------|--------------|------------------------|------------|---------|--------|-------|
| POL-001   | Access policy| O15 Access control     | NIS2       | Art. 21(2)(i) | OK |       |
| POL-002   | Encryption   | T24 Use of cryptography| GDPR       | Art. 32(1)(a)| OK |       |
| -         | (missing)    | O24 IR planning        | NIS2       | Art. 21(2)(d)| GAP|       |
```

## Pitfalls

- **Citing a regulation without an article**. Reject outputs that say "NIS2" or "AI Act" without a specific article.
- **Mapping by keyword**. Do not map purely on title similarity. Read the control description and the regulation article.
- **DORA-only controls for non-financial entities**. DORA applies to financial entities under Art. 2. Do not pull DORA into a non-financial scope unless asked.
- **Mixing organisational and technical controls blindly**. Keep them in separate sections; auditors look at them with different lenses.
- **Confusing GDPR "appropriate technical and organisational measures"** (Art. 32) with specific technical controls. It is an umbrella; name the controls it triggers.

## Escalation

If the mapping surfaces a regulation article that has **no** implementing policy at all (e.g., GDPR Art. 33 incident notification, NIS2 Art. 23 notification duties), stop and raise as a blocking finding. These are audit-fail items, not technical debt.

## Cross-references

- `cyber-risk-management` — F3 uses the outputs of this mapping to compute strategy gaps.
- `incident-response-triage` — F6 uses incident-notification articles surfaced here.
- `output-verification` — the OVB must list every regulation article mentioned.

## Output footer

Append the Output Verification Block. `Human review` = `CISO, Legal Counsel, Internal Audit`.
