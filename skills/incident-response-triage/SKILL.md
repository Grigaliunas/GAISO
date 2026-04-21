---
name: incident-response-triage
description: CISO function F6 — incident-response activities including triaging alerts, correlating events, and guiding incident handlers. Use when a live or suspected incident needs an ordered playbook, severity classification, NIS2 notification assessment, and evidence-preservation guidance.
license: CC-BY-NC-ND-4.0
---

# F6 — Incident Response Triage

Convert a noisy alert batch and some threat intelligence into an ordered incident-response playbook with severity, NIS2 notification judgment, and evidence-preservation steps. Never execute the playbook. Draft only.

## Function mapping (GAISO T3.1)

- **Domain**: Incident response.
- **ISO/IEC 27002:2022 controls**: **O24** Information security incident management planning and preparation, **O25** Assessment and decision on information security events, **O26** Response to information security incidents; **T7** Protection against malware, **T12** Data leakage prevention, **T15** Logging, **T16** Monitoring activities, **T20** Networks security, **T23** Web filtering.
- **Regulations**: NIS2 Art. 23 (incident notification), Commission Implementing Regulation (EU) 2024/2690 Annex (significance thresholds), GDPR Art. 33 (personal data breach notification), AI Act Art. 26 where a high-risk AI system is involved.

## Inputs you must demand

1. Alert / event batch.
2. Current SOC tier of the handler.
3. Named IR playbook in force (or state that none applies — this changes the output).
4. Data categories touched (personal data? trade secrets? classified?).
5. Regulated sector (drives notification clocks and bodies).
6. Containment state today.

## Procedure

1. **Classify the incident**. Use the organisation's severity schema; if none, use CISA severity 1–5 and name it.
2. **Assess significance under NIS2**. Apply the criteria in the Annex of Implementing Regulation 2024/2690: (i) affected users, (ii) duration, (iii) geography, (iv) economic loss, (v) damage to physical or legal persons. Record yes/no per criterion.
3. **Assess GDPR breach notification** (Art. 33) if personal data may be involved. The clock starts on awareness, not confirmation.
4. **Build the playbook** as an ordered list:
   - `Contain` steps first. No destructive actions without human approval.
   - `Preserve evidence` next (O28 Collection of evidence).
   - `Eradicate` third.
   - `Recover` and validate.
   - `Notify` — regulator, data subjects, law enforcement, customers — driven by the significance assessment.
   - `Post-incident learning` (O27) queued for the lessons-learned meeting.
5. **For each step**, name: `owner`, `expected_evidence`, `rollback`, `27002 control`.
6. **Emit** the playbook, then the OVB.

## Default output format

```
## Incident <id> — severity <n>, NIS2 significance: <Y/N>, GDPR art. 33: <Y/N>

| step | phase    | action                                  | owner   | expected_evidence | rollback | control |
|------|----------|-----------------------------------------|---------|-------------------|----------|---------|
| 1    | Contain  | Isolate host <H> from production VLAN   | SOC T2  | ticket + VLAN log | Reattach | T20     |
| 2    | Preserve | Acquire memory image on host <H>        | Forensic| hash, chain of custody | n/a | O28     |
…

## Notification clocks
- NIS2 early warning: 24h from awareness → <national CSIRT body> <Y/N required>
- NIS2 incident notification: 72h from awareness → <body>
- NIS2 final report: 1 month → <body>
- GDPR Art. 33: 72h to supervisory authority if personal data is in scope
```

## Pitfalls

- **Starting with eradication**. Preserve evidence first; eradication without artefacts closes the investigation.
- **Destructive shell commands**. Never produce commands. Describe the action; the handler's runbook has the command.
- **Guessing significance**. If any Annex criterion is unknown, do not assume. Report as `unknown` and escalate.
- **Starting the 72h clock late**. The GDPR clock begins on awareness. Record the awareness timestamp explicitly.
- **Mixing IOCs with PII**. Separate the forensic appendix from the executive summary so PII handling is clean.

## Escalation

Immediate escalation to the CISO, Legal, and DPO if:
- NIS2 significance thresholds are met or unknown.
- Personal data categories under GDPR Art. 9–10 are involved.
- A high-risk AI system is affected (AI Act Art. 26, 73).
- Ransomware encryption or exfiltration is confirmed or suspected.
- A regulator, law enforcement, or press is already in the loop.

## Cross-references

- `alert-correlation` (F5) — source of the correlated alerts.
- `remediation-guidance` (F7) — handler-level remediation draft.
- `security-test-scenarios` (F9) — lessons-learned regression tests.

## Output footer

Append the Output Verification Block. `Human review` = `IR Lead, CISO`. Add `Legal + DPO` when GDPR Art. 33 is in play.
