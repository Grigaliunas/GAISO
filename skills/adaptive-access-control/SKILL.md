---
name: adaptive-access-control
description: CISO function F11 — control role assignments based on user attributes (identity, privilege) to ensure adaptive access management. Use when reviewing IAM role assignments, screening joiner-mover-leaver requests, detecting segregation-of-duties conflicts, or proposing least-privilege adjustments.
license: CC-BY-NC-ND-4.0
---

# F11 — Adaptive Access Control Recommendations

Recommend role assignments from user attributes and access policy. This skill never changes production IAM state. It produces reviewable recommendations only.

## Function mapping (GAISO T3.1)

- **Domain**: Access management.
- **ISO/IEC 27002:2022 controls**: **O15** Access control, **O16** Identity management, **O18** Access rights; **T2** Privileged access rights, **T3** Information access restriction.
- **Regulations**: NIS2 Art. 21(2)(i); Commission Implementing Regulation (EU) 2024/2690 Annex; GDPR Art. 25 (privacy by design) and Art. 32; AI Act Art. 10 (data governance) where access touches AI training data or models.

## Inputs you must demand

1. IAM / directory source of truth (vendor).
2. PAM source where privileged accounts live.
3. Identity list under review with attributes: employee ID, department, job function, joiner/mover/leaver status, contract type, clearance level.
4. Current role assignments.
5. Access policy in force (role catalog, SoD matrix, approval workflows).
6. Purpose: joiner, mover, leaver, periodic recertification, entitlement review, breach-triggered review.

## Principles

- **Least privilege** unless proven otherwise.
- **Separation of duties** first-class: flag conflicts even if the user does not ask.
- **Deny by default** for privileged roles (T2).
- **Time-bounded elevations** rather than permanent role grants.
- **Joint approval** for break-glass roles.
- **Mover events are not additive** — reassess the whole profile, do not stack privileges.

## Procedure

1. **Normalise** identities. One identity per human, plus explicit service accounts.
2. **Compute** the minimum role set from job function.
3. **Diff** against current assignments. Roles that exceed the minimum are `OVERRENTITLED`.
4. **Check SoD** against the policy matrix. Every conflict is flagged with both conflicting roles.
5. **Apply JML rules**:
   - Joiner: grant minimum role set, require manager + IAM approval.
   - Mover: revoke old roles, grant new minimum. No silent stacking.
   - Leaver: revoke all, rotate keys and secrets owned, disable sessions. Name an owner for owned artefacts.
   - Recertification: manager must re-approve every role per period.
6. **Distinguish privileged vs. standard** — privileged changes require CISO or named delegate approval and expiring elevation.
7. **Emit** the recommendation table, then the OVB.

## Default output format

```
| identity | current_roles      | recommended_roles | change_type | rationale                      | sod_conflicts        | approval_needed          |
|----------|--------------------|-------------------|-------------|--------------------------------|----------------------|---------------------------|
| u-001    | dev, db_admin, fin | dev, db_reader    | reduce      | moved to engineering; SoD fix  | db_admin ↔ fin       | manager + IAM             |
| u-002    | —                  | dev, vpn          | grant       | joiner, engineering            | none                 | manager + IAM             |
| u-003    | hr, payroll_admin  | —                 | revoke (leaver) | termination date <date>    | none                 | manager + IAM + HR        |
| svc-001  | app_admin          | app_runtime       | reduce      | service account over-scoped    | none                 | app owner + CISO delegate |
```

## Pitfalls

- **Role inflation in movers**. Movers who keep old access "just in case" accumulate privilege that auditors will find.
- **Ignoring service accounts**. Non-human identities are in scope. Treat them with the same least-privilege lens.
- **Stale secret rotation**. Leavers are not complete until tokens, API keys, SSH keys, and KMS grants are rotated. Name the rotation owner.
- **SoD matrix not applied**. If no matrix exists, surface that as a finding before recommending — this is a NIS2 gap.
- **Break-glass not bounded**. Break-glass roles without an expiry are effectively permanent.

## Escalation

Escalate to CISO when:
- a recommended change would remove a user who is the sole approver in a workflow,
- a privileged role is held by an identity with no SoD guardrails,
- a service account with privileged scope has no owner,
- evidence of compromise requires immediate revocation rather than a scheduled change.

## Cross-references

- `incident-response-triage` (F6) — revocations during an active incident.
- `remediation-guidance` (F7) — credential rotation as part of recovery.
- `regulatory-compliance-mapping` (F2) — NIS2 Art. 21(2)(i) articulation.

## Output footer

Append the Output Verification Block. `Human review` = `IAM Admin, Line Manager`. Add `CISO` for privileged role changes, `HR` for leavers.
