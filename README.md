# GAISO — CISO Skills for Generative AI

> **GAISO** — *Research on Cyber Resilience Through Application of Generative Artificial Intelligence in Chief Information Security Officer Operations*
> Research Council of Lithuania, project P-ITP-24-13.
> Vilnius University, Kaunas Faculty (2024–2026).

This repository is the prototype deliverable of **Objective O4** of the GAISO project:
*"Implement a prototype that enhances Chief Information Security Officer functions with the assistance of generative Artificial Intelligence."*

It ships as a Claude Code plugin that bundles fifteen skills — twelve covering the CISO functions F1–F12 identified in the project application, plus three cross-cutting skills for governance, structured prompting and output verification. Every skill is grounded in the ISO/IEC 27002:2022 control catalogue and the EU cybersecurity acquis (NIS2, AI Act, GDPR, CER, CRA, CSA).

The design uses a single-file skill pattern (one `SKILL.md` per capability with YAML frontmatter), packaged as a Claude Code plugin with multiple skills.

## Why This Exists

- Critical-infrastructure entities face a widening gap between cyber threats and the CISO capacity available to contain them (CISO Workforce and Headcount 2023 Report).
- GenAI is already being used by attackers. Defenders need symmetrical, auditable tooling that automates routine CISO work without removing human judgment.
- The NIS2 Directive and the AI Act push both for stronger cyber-risk management and for controlled, documented use of GenAI in high-risk functions. A CISO assistant must satisfy both at once.

## The Twelve CISO Functions (F1–F12)

| ID  | CISO function | Domain | Primary skill |
|-----|---------------|--------|---------------|
| F1  | Analyse security events and threat intelligence; predict risk scores; recommend preventive measures | Threat detection | `threat-intelligence-analysis` |
| F2  | Map existing policies, standards and procedures to industry and regulatory frameworks for compliance | Risk management & compliance | `regulatory-compliance-mapping` |
| F3  | Assess cyber-risk maturity; identify strategy gaps; generate improvement recommendations | Risk management & compliance | `cyber-risk-management` |
| F4  | Generate summarised reports or executive briefings on active threats from historic trends or OSINT | Threat detection | `executive-threat-briefing` |
| F5  | Correlate alert data with threat-intelligence reports to determine impact on infrastructure | Threat detection | `alert-correlation` |
| F6  | Incident response — triage alerts, correlate events, guide incident handlers | Incident response | `incident-response-triage` |
| F7  | Draft security-focused responses that guide analysts in remediation and recovery | Incident response | `remediation-guidance` |
| F8  | Detect threats and phishing attempts created by LLMs | Threat detection | `llm-threat-detection` |
| F9  | Create test cases / sample scenarios with expected outcomes and supporting documentation | Security testing | `security-test-scenarios` |
| F10 | Correlate vulnerability data (scans, external info, remediation plans) to prioritise action | Vulnerability management | `vulnerability-prioritization` |
| F11 | Control role assignments based on user attributes (identity, privilege) for adaptive access | Access management | `adaptive-access-control` |
| F12 | Create personalised, role-based threat and crisis response training scenarios | Cybersecurity awareness | `awareness-training` |

Full mappings to ISO/IEC 27002:2022 controls and EU regulations are in [references/ciso-functions.md](references/ciso-functions.md).

## Three Cross-Cutting Skills

- **`ciso-core-principles`** — the behavioural contract: identity, scope, hallucination controls, escalation triggers. Loaded first.
- **`prompt-engineering-ciso`** — the five-part prompt structure `[TASK] + [CONTEXT] + [ROLE] + [CONSTRAINTS] + [FORMAT]` from task T2.1 of GAISO, plus a library of templates per CISO function.
- **`output-verification`** — the Output Verification Block (OVB) schema that every CISO skill appends to its deliverable, implementing the output verification protocol from T3.2.

## Install

**Option A: Claude Code plugin (recommended)**

From within Claude Code, add the local plugin directory as a marketplace, then install the plugin:

```
/plugin marketplace add /path/to/CAISO/G-AI
/plugin install gaiso-ciso-skills@gaiso-skills
```

**Option B: drop-in `CLAUDE.md`**

Copy [`CLAUDE.md`](CLAUDE.md) into the root of the project where the CISO assistant will run. Copy the [`skills/`](skills/) tree and the [`references/`](references/) tree alongside it. The agent will read the CLAUDE.md on every run and invoke individual skills by name.

## Usage

```
User:  F5 — correlate this alert batch with TI.
       [CONTEXT]    Energy sector, NIS2 essential entity, EU, SIEM is Splunk.
       [FORMAT]     JSON list of {alert_id, ti_match, impact_score, action}.
       [alert batch pasted]
```

The agent:
1. Loads the `alert-correlation` skill (F5).
2. Applies the five-part prompt structure — filling [ROLE] and [CONSTRAINTS] from the CLAUDE.md defaults.
3. Produces the JSON list.
4. Appends an Output Verification Block naming ISO/IEC 27002:2022 controls O7, O25, T8, T15, T16, T23, regulations NIS2 Art. 21 + AI Act Art. 15, confidence level, assumptions, and the SOC Analyst + IR Lead as the human reviewers.

See [EXAMPLES.md](EXAMPLES.md) for worked examples per CISO function.

## Repository Layout

```
G-AI/
├── .claude-plugin/
│   ├── plugin.json
│   └── marketplace.json
├── CLAUDE.md                    Behavioural contract for the CISO agent
├── README.md                    This file
├── EXAMPLES.md                  Worked example per CISO function
├── skills/
│   ├── ciso-core-principles/
│   ├── prompt-engineering-ciso/
│   ├── output-verification/
│   ├── cyber-risk-management/
│   ├── regulatory-compliance-mapping/
│   ├── threat-intelligence-analysis/
│   ├── executive-threat-briefing/
│   ├── alert-correlation/
│   ├── incident-response-triage/
│   ├── remediation-guidance/
│   ├── llm-threat-detection/
│   ├── security-test-scenarios/
│   ├── vulnerability-prioritization/
│   ├── adaptive-access-control/
│   └── awareness-training/
└── references/
    ├── ciso-functions.md        F1–F12 with ISO and regulation mapping
    ├── iso27002-controls.md     Organisational (O1–O37) + technical (T1–T34)
    ├── eu-regulations.md        NIS2, AI Act, GDPR, CER, CRA, CSA digest
    └── prompt-templates.md      Five-part prompt templates per function
```

## Research Provenance

| GAISO task | Output contributed to this plugin |
|------------|-----------------------------------|
| O1 — generative AI models analysis | Model selection guidance in `ciso-core-principles` |
| T2.1 — LLM prompt engineering methodology | `prompt-engineering-ciso` |
| T3.1 — legal basis mapping | `references/eu-regulations.md` |
| T3.2 — prompting standards and output verification protocols | `output-verification`, OVB schema |
| T3.3 — standards in test environments | `security-test-scenarios`, `adaptive-access-control` |
| T3.4 — guidelines for CISO operations | All twelve function skills |
| O4 — prototype | This repository |

## Licence

Content: **CC-BY-NC-ND-4.0** in line with the GAISO Data Management Plan.
Citations must reference: *Grigaliūnas et al., GAISO Project, Vilnius University, Research Council of Lithuania P-ITP-24-13 (2024–2026).*

## Disclaimer

This prototype is intended for research and supervised pilot deployment. Outputs are drafts. A human CISO or the role named in each Output Verification Block must review every deliverable before it is acted on. The authors accept no liability for use of the assistant outside the supervised scope.
