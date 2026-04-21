---
name: security-test-scenarios
description: CISO function F9 — create test cases and sample scenarios with expected outcomes and supporting documentation. Use when designing control-validation tests, purple-team exercises, tabletop scenarios, regression tests after an incident, or UAT for a new security control.
license: CC-BY-NC-ND-4.0
---

# F9 — Security Test Cases and Scenarios

Design test cases, exercises and supporting documentation so that a given security requirement can be validated and regressions can be caught. All scenarios operate at tactic-level (MITRE ATT&CK). Never produce executable exploit payloads against named third parties.

## Function mapping (GAISO T3.1)

- **Domain**: Security testing.
- **ISO/IEC 27002:2022 controls**: **O24** IR planning, **O30** ICT readiness for business continuity, **O37** Documented operating procedures; **T13** Information backup, **T14** Redundancy of information processing facilities, **T29** Security testing in development and acceptance.
- **Regulations**: NIS2 Art. 21(2)(f) testing of effectiveness; Commission Implementing Regulation (EU) 2024/2690 Annex; DORA Art. 24 threat-led penetration testing (TIBER-EU / TIBER-LT); AI Act Art. 15 testing obligations; CER Art. 13.

## Inputs you must demand

1. Requirement or control being tested (e.g., "block unauthenticated SMB from user segment", "backup restore within RPO=1h").
2. Environment: staging / pre-prod / prod. If prod, approvals required.
3. Data classification available in that environment.
4. Test type: control test, functional test, tabletop, purple team, TLPT.
5. Success criteria supplied by the control owner.

## Procedure

1. **Derive expected outcomes from the requirement**, not from the test steps. A test that can only produce "it passed" was not thought through.
2. **Write** the test case:
   - `test_id`, `description`, `requirement_ref`.
   - `preconditions` — environment, data, approvals.
   - `steps` — numbered, tactic-level (ATT&CK T-IDs where relevant).
   - `expected_results` — unambiguous pass/fail criteria.
   - `cleanup / rollback` — state you must leave the system in.
   - `owner`, `frequency` (one-off / per-release / quarterly).
3. **Document** supporting material: data seed, mock identities (no real PII), expected logs, alert signatures that should fire (T15, T16).
4. **For tabletops**, produce timed injects with branches and facilitator notes.
5. **For regression tests** after an incident, include the scenario that reproduced the incident — with harmless substitutions — and the control the fix restores.
6. **Emit** the artefacts, append the OVB.

## Default output format

```
## Test case T-<id>
Requirement: <requirement_ref>
Environment: <env>   Data classification: <class>   Owner: <role>

### Preconditions
- …

### Steps
1. <tactic-level action> (ATT&CK <Tid> if applicable)
2. …

### Expected results
- <pass-fail criterion>

### Cleanup
- <action>

### Evidence captured
- logs from <source>, alert signature <id>, ticket <id>
```

## Pitfalls

- **Executable payloads**. Do not produce working exploits against named third-party products or environments. Tactic-level description only.
- **Using real PII as seed data**. Generate synthetic identifiers. Note synthetic status in evidence.
- **Tests without pass criteria**. A test without a clear failure mode does not improve assurance.
- **Testing in prod without approval**. Prod tests require named approvers and a rollback plan.
- **Tabletops that "always go well"**. Build failures into injects — degraded backup, unreachable vendor, pager silence — or the tabletop teaches nothing.

## DORA / TIBER-EU note

For financial entities under DORA, TLPT follows a regulated process. This skill produces preparatory artefacts, not the engagement itself. Named TLPT providers conduct the live test under supervisory oversight.

## Cross-references

- `cyber-risk-management` (F3) — maturity improvements usually need new tests.
- `remediation-guidance` (F7) — post-incident regression tests come from this skill.
- `awareness-training` (F12) — scenario skeletons overlap; this skill focuses on technical validation.

## Output footer

Append the Output Verification Block. `Human review` = `Control owner, QA lead`. For TLPT under DORA, add `Lead TLPT Tester, Competent Authority`.
