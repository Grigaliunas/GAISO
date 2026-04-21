# CISO Functions F1–F12 — ISO/IEC 27002:2022 and EU Regulation Mapping

Source: GAISO project (P-ITP-24-13) — Objective O3 deliverable, task T3.1 mapping of legal basis to organisational and technical controls. Reproduced in English from the Lithuanian deliverable.

The twelve functions below are the authoritative scope of this plugin. Each function skill in `skills/` implements one of them.

## F1 — Analyse security events and threat intelligence

Predict risk scores and recommend preventive measures.

- **Domain**: Threat detection and response.
- **Skill**: `threat-intelligence-analysis`.
- **ISO/IEC 27002:2022**: O7, O25, O27; T8, T15, T16, T23.
- **Regulations**: NIS2 Art. 21(2)(b), (c), (h); Implementing Reg. 2024/2690 Annex; AI Act Art. 15.

## F2 — Map policies, standards and procedures

Map against industry and regulatory frameworks to meet compliance requirements.

- **Domain**: Cyber risk management and compliance.
- **Skill**: `regulatory-compliance-mapping`.
- **ISO/IEC 27002:2022**: O31, O36; T24.
- **Regulations**: NIS2 Art. 21(2), Art. 24; Implementing Reg. 2024/2690; AI Act Art. 9, 15; GDPR Art. 24, 28, 32; CER Art. 13; CRA Annex I.

## F3 — Assess cyber-risk maturity

Identify gaps in cyber strategy and generate improvement recommendations.

- **Domain**: Cyber risk management and compliance.
- **Skill**: `cyber-risk-management`.
- **ISO/IEC 27002:2022**: O1, O35, O36; T8, T9, T29.
- **Regulations**: NIS2 Art. 21; AI Act Art. 9; CER Art. 13; CRA Art. 13.

## F4 — Generate executive threat briefings

Summarise active threats from historic trends or publicly available data.

- **Domain**: Threat detection and response.
- **Skill**: `executive-threat-briefing`.
- **ISO/IEC 27002:2022**: O7; T15, T16.
- **Regulations**: NIS2 Art. 20, Art. 21(2)(g); AI Act Art. 15.

## F5 — Alert / threat-intelligence correlation

Correlate alert data and threat-intelligence reports to determine infrastructure impact.

- **Domain**: Threat detection and response.
- **Skill**: `alert-correlation`.
- **ISO/IEC 27002:2022**: O7, O25; T8, T15, T16, T23.
- **Regulations**: NIS2 Art. 21(2)(b), (h); Implementing Reg. 2024/2690 Annex; AI Act Art. 15.

## F6 — Incident-response triage

Triage alerts, correlate events, guide incident handlers.

- **Domain**: Incident response.
- **Skill**: `incident-response-triage`.
- **ISO/IEC 27002:2022**: O24, O25, O26; T7, T12, T15, T16, T20, T23.
- **Regulations**: NIS2 Art. 23; Implementing Reg. 2024/2690 Annex; GDPR Art. 33; AI Act Art. 26.

## F7 — Remediation and recovery guidance

Create security-focused responses that guide analysts in remediation and recovery activities.

- **Domain**: Incident response.
- **Skill**: `remediation-guidance`.
- **ISO/IEC 27002:2022**: O24, O26, O30; T7, T13, T14, T32.
- **Regulations**: NIS2 Art. 21(2)(c), (d); CER Art. 13; DORA Art. 11–12 (financial); CRA Art. 14.

## F8 — LLM-generated threat detection

Detect threats and phishing attempts created by large-language models.

- **Domain**: Threat detection and response.
- **Skill**: `llm-threat-detection`.
- **ISO/IEC 27002:2022**: O6, O7, O25; T8, T15, T16, T20, T23.
- **Regulations**: NIS2 Art. 21(2)(b), (g); Implementing Reg. 2024/2690 Annex; AI Act Art. 50; GDPR Art. 32.

## F9 — Security test cases and scenarios

Create test cases / sample scenarios; define expected outcomes; develop supporting documentation.

- **Domain**: Security testing.
- **Skill**: `security-test-scenarios`.
- **ISO/IEC 27002:2022**: O24, O30, O37; T13, T14, T29.
- **Regulations**: NIS2 Art. 21(2)(f); Implementing Reg. 2024/2690 Annex; DORA Art. 24 (TIBER-EU / TIBER-LT); AI Act Art. 15; CER Art. 13.

## F10 — Vulnerability prioritisation

Correlate vulnerability data (scan data, external information and remediation plans) to prioritise action plans.

- **Domain**: Vulnerability management.
- **Skill**: `vulnerability-prioritization`.
- **ISO/IEC 27002:2022**: O7, O24, O27; T8, T29.
- **Regulations**: NIS2 Art. 21(2)(a), (e); Implementing Reg. 2024/2690 Annex; CRA Art. 13–14; AI Act Art. 15.

## F11 — Adaptive access control

Control role assignments based on user attributes (identity, privilege) to ensure adaptive access management.

- **Domain**: Access management.
- **Skill**: `adaptive-access-control`.
- **ISO/IEC 27002:2022**: O15, O16, O18; T2, T3.
- **Regulations**: NIS2 Art. 21(2)(i); Implementing Reg. 2024/2690 Annex; GDPR Art. 25, 32; AI Act Art. 10.

## F12 — Personalised awareness and crisis-response training

Create personalised and targeted threat and crisis response scenarios for employees based on roles and responsibilities.

- **Domain**: Cybersecurity awareness.
- **Skill**: `awareness-training`.
- **ISO/IEC 27002:2022**: O7, O24, O27, O30; T8, T16, T29.
- **Regulations**: NIS2 Art. 20, Art. 21(2)(g); CER Art. 13(2); AI Act Art. 4; GDPR Art. 39(1)(b).

## Summary matrix

| # | Function | Domain | Org controls | Tech controls |
|---|----------|--------|--------------|---------------|
| F1 | Security event & TI analysis | TDR | O7, O25, O27 | T8, T15, T16, T23 |
| F2 | Policy ↔ regulation mapping | RMC | O31, O36 | T24 |
| F3 | Maturity assessment | RMC | O1, O35, O36 | T8, T9, T29 |
| F4 | Executive threat briefing | TDR | O7 | T15, T16 |
| F5 | Alert ↔ TI correlation | TDR | O7, O25 | T8, T15, T16, T23 |
| F6 | IR triage | IR | O24, O25, O26 | T7, T12, T15, T16, T20, T23 |
| F7 | Remediation & recovery | IR | O24, O26, O30 | T7, T13, T14, T32 |
| F8 | LLM threat detection | TDR | O6, O7, O25 | T8, T15, T16, T20, T23 |
| F9 | Test cases & scenarios | ST | O24, O30, O37 | T13, T14, T29 |
| F10 | Vulnerability prioritisation | VM | O7, O24, O27 | T8, T29 |
| F11 | Adaptive access control | AM | O15, O16, O18 | T2, T3 |
| F12 | Awareness training | CA | O7, O24, O27, O30 | T8, T16, T29 |

Legend — RMC: risk management & compliance; TDR: threat detection & response; IR: incident response; VM: vulnerability management; ST: security testing; AM: access management; CA: cybersecurity awareness.
