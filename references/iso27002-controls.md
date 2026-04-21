# ISO/IEC 27002:2022 Controls — Reference (Organisational O1–O37, Technical T1–T34)

This reference mirrors the control catalogue used by the GAISO T3.1 mapping. Only organisational (OpSec, O-prefix) and technical (TechSec, T-prefix) controls are in scope. Human-resources security and physical security controls are out of the GAISO scope and are not catalogued here.

For each control: short name, type(s), CISO functions that bind to it, and the EU acts that cite or equate to it (from the GAISO T3.1 table). `Y` means the act imposes a related obligation.

Legend — Type: P Preventive, D Detection, C Corrective.
Regulations — GDPR (Reg. 2016/679), CSA (Cybersecurity Act Reg. 2019/881), NIS2 (Dir. 2022/2555), AIA (AI Act Reg. 2024/1689), CER (Dir. 2022/2557), CRA (Cyber Resilience Act Reg. 2024/2847).

## Organisational controls (OpSec)

| ID  | Name | Type | CISO functions | GDPR | CSA | NIS2 | AIA | CER | CRA |
|-----|------|------|----------------|:----:|:---:|:----:|:---:|:---:|:---:|
| O1  | Policies for information security | P | F3 | Y | Y | Y | Y | Y | Y |
| O2  | Information security roles and responsibilities | P | — | Y | Y | Y | Y | Y |   |
| O3  | Segregation of duties | P | — |   |   |   |   |   |   |
| O4  | Management responsibilities | P | — | Y | Y |   | Y |   |   |
| O5  | Contact with authorities | P/C | — | Y | Y | Y | Y | Y | Y |
| O6  | Contact with special interest groups | P/C | F8 | Y | Y | Y |   |   |   |
| O7  | Threat intelligence | P/D/C | F1, F4, F5, F8, F10, F12 |   | Y | Y | Y | Y |   |
| O8  | Information security in project management | P | — |   |   |   | Y |   |   |
| O9  | Inventory of information and other assets | P | — |   | Y |   | Y |   |   |
| O10 | Acceptable use of information and other assets | P | — |   |   |   |   |   |   |
| O11 | Return of assets | P | — |   |   |   |   |   |   |
| O12 | Classification of information | P | — |   |   |   | Y |   |   |
| O13 | Labelling of information | P | — |   |   |   | Y |   |   |
| O14 | Information transfer | P | — |   |   |   | Y |   |   |
| O15 | Access control | P | F11 | Y | Y | Y | Y | Y | Y |
| O16 | Identity management | P | F11 | Y | Y | Y |   |   |   |
| O17 | Authentication information | P | — | Y | Y | Y |   |   |   |
| O18 | Access rights | P | F11 | Y | Y | Y | Y |   |   |
| O19 | Information security in supplier relationships | P | — | Y | Y | Y | Y | Y |   |
| O20 | Addressing information security within supplier agreements | P | — | Y |   |   | Y |   |   |
| O21 | Managing information security in the ICT supply chain | P | — |   | Y | Y | Y | Y |   |
| O22 | Monitoring, review and change management of supplier services | P | — |   | Y | Y | Y |   |   |
| O23 | Information security for use of cloud services | P | — |   |   |   | Y |   |   |
| O24 | Information security incident management planning and preparation | C | F6, F7, F9, F10, F12 | Y | Y | Y | Y |   |   |
| O25 | Assessment and decision on information security events | D | F1, F5, F6, F8 |   |   | Y |   |   |   |
| O26 | Response to information security incidents | C | F6, F7 | Y | Y | Y | Y | Y |   |
| O27 | Learning from information security incidents | P | F1, F10, F12 |   | Y |   | Y |   |   |
| O28 | Collection of evidence | C | — |   |   | Y | Y |   |   |
| O29 | Information security during disruption | P/C | — | Y | Y | Y | Y | Y |   |
| O30 | ICT readiness for business continuity | C | F7, F9, F12 |   |   | Y | Y | Y |   |
| O31 | Legal, statutory, regulatory and contractual requirements | P | F2 | Y | Y | Y | Y | Y |   |
| O32 | Intellectual property rights | P | — | Y |   | Y |   |   |   |
| O33 | Protection of records | P | — | Y | Y | Y | Y |   |   |
| O34 | Privacy and protection of PII | P | — | Y | Y | Y | Y |   |   |
| O35 | Independent review of information security | P/C | F3 |   |   | Y |   |   | Y |
| O36 | Compliance with policies, rules and standards for information security | P | F2, F3 |   | Y | Y | Y |   | Y |
| O37 | Documented operating procedures | P/C | F9 | Y | Y |   | Y | Y |   |

## Technical controls (TechSec)

| ID  | Name | Type | CISO functions | GDPR | CSA | NIS2 | AIA | CER | CRA |
|-----|------|------|----------------|:----:|:---:|:----:|:---:|:---:|:---:|
| T1  | User end-point devices | P | — |   | Y |   | Y |   |   |
| T2  | Privileged access rights | P | F11 | Y | Y | Y | Y |   |   |
| T3  | Information access restriction | P | F11 | Y |   |   | Y |   |   |
| T4  | Access to source code | P | — |   |   |   | Y |   |   |
| T5  | Secure authentication | P | — | Y | Y | Y | Y | Y |   |
| T6  | Capacity management | P/D | — |   |   |   | Y |   |   |
| T7  | Protection against malware | P/D/C | F6, F7 | Y | Y | Y | Y |   |   |
| T8  | Management of technical vulnerabilities | P | F1, F3, F5, F8, F10, F12 | Y | Y | Y | Y | Y | Y |
| T9  | Configuration management | P | F3 | Y | Y | Y | Y |   |   |
| T10 | Information deletion | P | — | Y | Y | Y |   |   |   |
| T11 | Data masking | P | — |   |   |   |   |   |   |
| T12 | Data leakage prevention | P/D | F6 | Y | Y | Y |   |   |   |
| T13 | Information backup | C | F7, F9 | Y | Y | Y |   |   |   |
| T14 | Redundancy of information processing facilities | P | F7, F9 | Y |   | Y |   |   |   |
| T15 | Logging | D | F1, F4, F5, F6, F8 | Y | Y | Y | Y | Y |   |
| T16 | Monitoring activities | D/C | F1, F4, F5, F6, F8, F12 | Y | Y | Y | Y | Y |   |
| T17 | Clock synchronization | D | — |   |   |   | Y |   |   |
| T18 | Use of privileged utility programs | P | — |   |   |   |   |   |   |
| T19 | Installation of software on operational systems | P | — |   |   |   |   |   |   |
| T20 | Networks security | P/D | F6, F8 | Y | Y | Y | Y | Y |   |
| T21 | Security of network services | P | — | Y |   |   | Y |   |   |
| T22 | Segregation of networks | P | — | Y | Y |   |   |   |   |
| T23 | Web filtering | P | F1, F5, F6, F8 |   |   |   |   |   |   |
| T24 | Use of cryptography | P | F2 | Y | Y | Y | Y |   |   |
| T25 | Secure development life cycle | P | — |   | Y |   | Y | Y |   |
| T26 | Application security requirements | P | — |   | Y |   | Y |   |   |
| T27 | Secure system architecture and engineering principles | P | — | Y | Y |   | Y |   |   |
| T28 | Secure coding | P | — |   | Y |   | Y |   |   |
| T29 | Security testing in development and acceptance | P | F3, F9, F10, F12 | Y | Y | Y | Y |   |   |
| T30 | Outsourced development | P/D | — |   | Y |   | Y |   |   |
| T31 | Separation of development, test and production environments | P | — |   | Y | Y | Y |   |   |
| T32 | Change management | P | F7 | Y | Y | Y | Y |   |   |
| T33 | Test information | P | — |   |   |   |   |   |   |
| T34 | Protection of information systems during audit testing | P | — |   | Y |   |   |   |   |

## Notes

- The mapping above reproduces the authors' interpretation from GAISO T3.1. It can be subjective; control context may extend citations beyond those shown.
- Sectoral acts (DORA, NIS2 Annex I/II sector-specific rules, ePrivacy, Data Act, Data Governance Act, Digital Services Act, Digital Markets Act, Chips Act, Product Liability Directive) are out of scope of this table. Sector-specific skills must add them explicitly.
- Alternative control catalogues (NIST SP 800-53 Rev. 5, CIS Controls v8.1) may refine or extend these controls for specific deployments.
