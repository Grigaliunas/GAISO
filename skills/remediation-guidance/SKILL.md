---
name: remediation-guidance
description: CISO function F7 — create security-focused responses that guide analysts through remediation and recovery activities. Use when producing a Contain → Eradicate → Recover → Verify runbook for an active incident, a post-eradication restoration plan, or a handover note between shifts.
license: CC-BY-NC-ND-4.0
---

# F7 — Remediation and Recovery Guidance

Draft the analyst-facing runbook for remediation and recovery. Scope is step-level guidance, not executable commands. Every step names the control it is restoring.

## Function mapping (GAISO T3.1)

- **Domain**: Incident response.
- **ISO/IEC 27002:2022 controls**: **O24** IR planning, **O26** Response to incidents, **O30** ICT readiness for business continuity; **T7** Protection against malware, **T13** Information backup, **T14** Redundancy of information processing facilities, **T32** Change management.
- **Regulations**: NIS2 Art. 21(2)(c) business continuity, Art. 21(2)(d) supply-chain; CER Art. 13; DORA Art. 11–12 for financial entities; Cyber Resilience Act Art. 14 vulnerability handling for product-level impact.

## Inputs you must demand

1. Incident ID and severity from F6.
2. Incident class: malware, phishing, DoS, insider, supply-chain, misconfiguration, data exfiltration.
3. Affected systems and data categories.
4. Current containment state and any actions already taken.
5. Business-continuity posture: RTO, RPO, last backup status (T13), failover readiness (T14).

## Procedure (Contain → Eradicate → Recover → Verify)

1. **Contain** — stop the spread without destroying evidence. Network-isolate, disable accounts, revoke tokens. Do not reimage yet.
2. **Eradicate** — remove persistence. Identify every foothold before acting, or the attacker returns.
3. **Recover** — restore from clean backups (T13). Validate integrity before bringing the system back (hash comparison, not just "it boots"). Use T14 redundancies where available.
4. **Verify** — functional tests, security tests (F9), monitoring turned up, new IOCs fed to TI.
5. **Change control** — every change logged under T32. A change-freeze on adjacent systems is often warranted.
6. **Communications** — handover wording for the next shift, customer messages if the incident becomes public, regulator updates if NIS2/DORA clocks apply.

## Default output format

```
## Remediation runbook — incident <id>

### Phase 1 — Contain
1. <step>. Owner: <role>. Evidence: <artefact>. Rollback: <method>. Control: T20.
…

### Phase 2 — Eradicate
…

### Phase 3 — Recover
…

### Phase 4 — Verify
…

## Shift handover note
- Status: <brief>
- Open risks: <list>
- Next step at shift change: <single sentence>

## Stakeholder communications
- Internal: <one sentence draft>
- Customer (if required): <one sentence draft, PII-free>
```

## Pitfalls

- **Reimage-first impulse**. Reimage destroys persistence evidence. Snapshot first.
- **Shell commands**. Do not produce shell, PowerShell or PSRemoting one-liners. Name the action, not the command.
- **Skipping backup validation**. A backup that has not been verified is not a backup. Test restore in a quarantine environment.
- **Silent password resets**. Mass credential rotation without coordination breaks applications. Stage and announce.
- **Post-incident IOC distribution without review**. IOCs leaving the organisation need CTI-lead approval.

## Escalation

If recovery requires invoking disaster-recovery infrastructure, DR declaration is a CISO + COO decision. Stop the runbook and surface the decision point. If the incident touches a supplier, notify under NIS2 Art. 23(4) and the supplier agreement clause.

## Cross-references

- `incident-response-triage` (F6) — upstream triage.
- `security-test-scenarios` (F9) — post-recovery validation tests.
- `adaptive-access-control` (F11) — when privilege changes are part of recovery.

## Output footer

Append the Output Verification Block. `Human review` = `IR Lead, SOC Manager`. Add `Change Advisory Board` for any step that changes production state beyond containment.
