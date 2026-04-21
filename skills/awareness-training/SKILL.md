---
name: awareness-training
description: CISO function F12 — create personalised and targeted threat and crisis response training scenarios for employees based on roles and responsibilities. Use when designing phishing simulations, role-specific awareness modules, tabletop exercises, or post-incident learning sessions.
license: CC-BY-NC-ND-4.0
---

# F12 — Personalised Awareness and Crisis-Response Training

Produce role-tailored training scenarios. No impersonation of real people. No real PII. Fictitious company names throughout.

## Function mapping (GAISO T3.1)

- **Domain**: Cybersecurity awareness.
- **ISO/IEC 27002:2022 controls**: **O7** Threat intelligence, **O24** IR planning, **O27** Learning from incidents, **O30** ICT readiness for business continuity; **T8** Management of technical vulnerabilities, **T16** Monitoring activities, **T29** Security testing in development and acceptance.
- **Regulations**: NIS2 Art. 20 (management bodies training) and Art. 21(2)(g) (basic cyber hygiene and training); CER Art. 13(2); AI Act Art. 4 (AI literacy obligations); GDPR Art. 39(1)(b) for DPO-led awareness.

## Inputs you must demand

1. Target role (job title, department, seniority).
2. Prior exposure — which modules the trainee has taken, prior incident role.
3. Awareness level: beginner, intermediate, advanced.
4. Delivery channel: tabletop, email simulation, LMS, live workshop, interactive scenario.
5. Topic: phishing, BEC, ransomware, insider, supply-chain, physical, DPO/GDPR, AI-usage, crisis-response.
6. Language of delivery.
7. Assessment requirement (pass/fail) vs. participation-only.

## Design principles

- **Role-first**. An engineer's lure differs from a finance director's. Do not recycle.
- **Realistic but fictional**. Pressure, urgency, and context from real threat reports; names, numbers and emails invented.
- **Single learning objective**. One scenario, one lesson. Bundle lessons into a curriculum, not a single scenario.
- **Debrief beats gotcha**. The scenario exists to teach, not to humiliate. The debrief must be built into the design.
- **AI literacy for all**. Under AI Act Art. 4, organisations using AI must ensure user literacy. F12 includes baseline GenAI-risk modules.
- **Accessibility**. Plain language, colour-blind-safe visuals, screen-reader compatibility for LMS assets.

## Procedure

1. **Define** the learning objective — one sentence.
2. **Construct** the scenario:
   - Setup (role-appropriate context).
   - Injects (timed events for tabletops; threads for email simulations).
   - Expected trainee actions at each decision point.
   - Distractors that look plausible but are not correct.
3. **Write** facilitator notes including failure modes and teaching moments.
4. **Write** the debrief questions.
5. **For phishing simulation**, supply the lure draft with placeholders (`<fictitious company>`, `<fictitious domain>`) — never a working domain; never imitate a named internal person.
6. **Map** to a compliance reporting line (NIS2 Art. 21(2)(g), AI Act Art. 4) for HR audit trails.
7. **Emit** the scenario, then the OVB.

## Default output format

```
## Scenario S-<id> — <role> — <topic>

### Learning objective
<single sentence>

### Setup
<role-appropriate context>

### Injects
| time | inject | expected trainee action | distractor |
| t+0  | …      | …                       | …          |

### Facilitator notes
- Common failure modes: …
- Teaching moments: …

### Debrief questions
1. …
2. …

### Assessment (if applicable)
| criterion | passing bar |
```

## Pitfalls

- **Impersonation of real people**. Never. Not even named fictitiously close to real people in the organisation.
- **Lure with a working domain**. Use reserved test domains (`example.com`, `invalid`). Never typosquats of real vendors.
- **Scenarios that humiliate**. The click-rate is a metric, not the goal.
- **GDPR-blind scenarios**. If the scenario uses personal data to be realistic, the data must be synthetic.
- **One-off training**. A one-off simulation is theatre. Mandate cadence per NIS2 Art. 21(2)(g).
- **AI-ignorant curriculum**. AI Act Art. 4 requires AI literacy; skipping it is a compliance gap, not a nice-to-have.

## Escalation

Escalate to CISO + HR + Legal if:
- the scenario would approximate a real targeted attack against a named employee,
- assessment data would become part of an employee's disciplinary record,
- the scenario touches works-council or employee-representative remit,
- the scenario crosses jurisdictional data-protection rules.

## Cross-references

- `security-test-scenarios` (F9) — technical validation; this skill is for human factors.
- `incident-response-triage` (F6) — lessons-learned feed new scenarios.
- `llm-threat-detection` (F8) — lure creation patterns inform defender training.

## Output footer

Append the Output Verification Block. `Human review` = `CISO, HR Learning & Development`. Add `DPO` when personal data or employee monitoring is in scope.
