# 00. Executive summary

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

## Purpose and scope

This summary gives the executive team of Fabrikam, Inc. (fictional) the Director of IT and Security's proposal for November 2026 to October 2027 and the decisions it needs. Linked documents and architecture decision records (ADRs) hold the detail; dates and targets are proposals ([01](01-scenario-and-assumptions.md)).

## The situation

Several thousand employers rely on Fabrikam to pay their workers on time and protect the Social Security numbers and bank details they hand over. On day 1, corporate information technology (IT) runs Microsoft 365 E3, lightly configured: sign-in mostly by push or text code, standing administrator rights, joiners and leavers by email, no night alerting, no backup beyond retention, and no dedicated security staff.

Three dates set the pace: Microsoft's own text and voice sign-in codes stop for most users on 2027-02-01; customer-facing changes freeze from mid-December through January; and the current SOC 2 review period (the attestation report customers ask for) closes in March 2027.

## The first 90 days and day 120

- **Day 30 (M1):** a listening report, inventories, key performance indicator (KPI) baselines, and draft top risks. Phase 1 changes little beyond emergency access, administrator multifactor authentication, after-hours alerting, and a restore check.
- **Day 60 (M2):** quick wins before the freeze, a risk register with executive owners, and the SOC 2 period on track.
- **Day 90 (M3):** on Thursday 2027-01-28 the executive team approves the 12-month plan, budget, policies, risk appetite, and National Institute of Standards and Technology (NIST) Cybersecurity Framework (CSF) 2.0 Profiles; no one relies only on text or voice codes.
- **Day 120 readout (D120, Friday 2027-02-26):** first results against the baselines ([02](02-first-90-days.md)).

**Progress:** 24 proposed KPIs, baselined at M1 with targets approved at M3, a one-page monthly scorecard from December, the Quarterly Risk Review, and no composite score ([12](12-metrics-and-executive-reporting.md)).

## Top five priorities

1. **Stop payroll and payment fraud (R-01, R-02):** phishing-resistant sign-in (every administrator by December 2026, most employees by M6 in July), email authentication enforced on every sending domain, and a call-back on every bank change; in the product, stronger customer administrator sign-in and bank-change safeguards, which the Chief Product Officer decides at M3 ([ADR-004](adr/ADR-004-phishing-resistant-authentication-rollout.md), [playbook](playbooks/payroll-diversion-and-email-compromise.md)).
2. **Detect and contain at any hour (R-10, R-03):** a managed detection and response (MDR) provider from the end of April 2027, because customer contracts set notification clocks ([ADR-003](adr/ADR-003-managed-detection-and-response.md)).
3. **Protect and widen SOC 2 (R-11):** no gap between periods, and for the acquired product line, which enterprise deals wait on, the proposed route is a Type 1 report on controls as of 2027-08-31, issued in the second half of 2027, then a Type II period to 2028-03-31; the executive team confirms it at M5 ([10](10-governance-and-compliance-program.md)).
4. **Let the human resources record drive access (R-05)** from M6, so new hires work on day one and leavers lose access on time ([ADR-002](adr/ADR-002-hr-system-of-record-drives-identity.md)).
5. **Make data and payroll recoverable (R-03, R-04):** tested backups and product recovery, because a product outage in a processing window means missed pay dates ([14](14-business-continuity-and-backup.md)).

## Decisions requested

**Before M3.** The chief financial officer approves backup for the most critical data, any Windows 10 bridge, and an incident response retainer, or pre-agreed emergency terms, before mid-December ([08](08-detection-and-incident-response.md), [14](14-business-continuity-and-backup.md)). Before mid-December, the chief technology officer (CTO), as R-04's owner, accepts the product recovery position through year-end on the evidence from 14.01, or asks Engineering for a limited recovery check that changes no production system. The vice president of People decides on-call pay or time off.

| At M3, by priority | Relative size | If declined |
|---|---|---|
| A Security Engineer and a governance, risk, and compliance (GRC) Analyst, from March 2027, or February if pre-approved at M2 ([04](04-operating-model-team-and-budget.md)) | Largest new recurring line | Interim cover continues; March work and M6 at risk ([03](03-twelve-month-roadmap.md)) |
| Microsoft Defender Suite (formerly Microsoft 365 E5 Security) and Microsoft Entra ID Governance ([ADR-001](adr/ADR-001-microsoft-365-security-licensing.md)) | Moderate per-user uplift | Without Defender Suite: no meaningful MDR service. Without Governance: M6 at risk, leaver removal partly manual |
| The MDR provider ([ADR-003](adr/ADR-003-managed-detection-and-response.md)) | Largest partner line | Interim on-call continues; R-10 stays with its owner |
| R-02 and R-08 (integration credential compromise) treatments ([11](11-risk-management.md)) | Engineering time, sized with the CTO before M3 | Each stays outside appetite; its owner and the chief executive officer (CEO) accept it for a set period |
| An isolated backup copy ([ADR-006](adr/ADR-006-microsoft-365-backup.md)) | Sized to the most critical data | The CEO accepts R-03's residual for a set period |
| A compliance automation platform ([ADR-007](adr/ADR-007-compliance-automation-platform.md)) | Small | A control matrix and evidence calendar |

**M5 and M7:** the acquired product line's route, Microsoft Copilot (formerly Microsoft 365 Copilot) expansion, and wider compliance licensing.

## Resourcing and dependencies

Roles, partners, licenses, and cost drivers are in [04](04-operating-model-team-and-budget.md).

## Risks and open questions

- Until both roles start, the Director and the Systems Engineer (Identity and Endpoint) carry most of the work, with FastTrack and contracted build help from February, while Phase 4 stacks the registration peak, the M4 close, MDR onboarding, and consolidation waves ([03](03-twelve-month-roadmap.md), [04](04-operating-model-team-and-budget.md)).
- Engineering's capacity decides R-02, R-04, R-08, and M5 ([04](04-operating-model-team-and-budget.md)).
- General Counsel confirms in Phase 1 whether California's cybersecurity audit regulations apply; if so, an audited period may start on 2027-01-01 ([10](10-governance-and-compliance-program.md)).

## Framework mapping

From the [crosswalk](crosswalk/csf2-soc2-crosswalk.md).

| Theme | NIST CSF 2.0 | SOC 2 (2017 Trust Services Criteria) |
|---|---|---|
| Oversight and decisions | GV.OV-01, GV.OV-02, GV.OV-03 | CC1.2, CC4.1, CC4.2 |
| Objectives and risk strategy | GV.OC-01, GV.RM-01, GV.RM-02 | CC3.1, CC5.1 |
| Roles and decision rights | GV.RR-01, GV.RR-02 | CC1.1, CC1.3 |

## Appendix: action index

Where the milestones, outcomes, and decisions above are delivered. Each ID points to the phase plan of the document its first two digits name; documents [02](02-first-90-days.md) and [03](03-twelve-month-roadmap.md) give the full sequence, and [04](04-operating-model-team-and-budget.md) names the partners: an MDR provider, the SOC 2 audit firm, a penetration testing firm, and an IT hardware partner.

| Item in this summary | Actions |
|---|---|
| Day 30 (M1) | 05.10, 05.11, 12.01 |
| Phase 1 urgent fixes and the restore check | 06.01, 06.03, 08.01, 08.02, 08.03, 14.01 |
| Day 60 (M2), with the Phase 2 quick wins and the first monthly scorecard | 06.09 to 06.11, 06.14 to 06.16, 06.18 to 06.20, 14.04, 14.05, 11.03, 10.09, 12.03 |
| Day 90 (M3), with no one relying only on text or voice codes | 01.02, 10.13, 10.14, 11.06, 12.05, 12.06, 06.21 |
| Day 120 readout (D120) | 12.07 |
| Progress: KPI baselines and targets, the monthly scorecard, and the Quarterly Risk Reviews | 05.10, 12.01, 12.03, 12.04, 12.05, 12.06, 12.10, 12.11, 12.12 |
| Phishing-resistant sign-in (administrators by December 2026, most employees by M6) and accounts driven by the human resources record from M6 | 06.09, 06.24, 06.32, 07.11 to 07.17 |
| Customer administrator sign-in and bank-change safeguards (R-02), decided at M3 | 11.07 |
| MDR provider live from the end of April 2027 | 08.06, 08.08, 08.10 |
| Tested backups and product recovery | 14.05, 14.12, 14.16, 14.17 |
| Email authentication enforced on every sending domain | 06.06, 06.16, 06.27 |
| No gap between SOC 2 periods; the acquired product line's proposed route, confirmed at M5 | 10.21, 10.23, 10.24 |
| Decisions before M3: backup spend, any Windows 10 bridge, the incident response retainer, and the CTO's product recovery position on the evidence from the Phase 1 restore check | 14.03, 06.07, 08.06, 14.01, 14.07 |
| Decisions at M3: licensing, the MDR provider, R-02 and R-08 treatments, the isolated copy, the compliance platform; the two roles are in the budget | 06.23, 07.08, 08.08, 11.07, 14.09, 10.15 |
| Help for February: FastTrack, requested in December; contracted build help from February and surge cover from Friday 2027-01-29, their terms agreed in January, with surge staff trained on 28 and 29 January, after the M3 approval | 06.23, 13.12, 13.14, 13.15 |
| Decisions at M5 and M7 (the first annual program review): the acquired product line's route and Microsoft Copilot expansion; wider compliance licensing follows [ADR-001](adr/ADR-001-microsoft-365-security-licensing.md)'s M7 revisit | 10.23, 16.14, 12.12 |

## Sources

- Plan documents relied on: [01](01-scenario-and-assumptions.md), [02](02-first-90-days.md), [03](03-twelve-month-roadmap.md), [04](04-operating-model-team-and-budget.md), [06](06-microsoft-365-security-baseline.md), [07](07-identity-lifecycle-joiners-movers-leavers.md), [08](08-detection-and-incident-response.md), [10](10-governance-and-compliance-program.md), [11](11-risk-management.md), [12](12-metrics-and-executive-reporting.md), [13](13-it-service-management.md), [14](14-business-continuity-and-backup.md), [16](16-ai-adoption-guardrails.md), [17](17-threat-profile.md), [ADR-001](adr/ADR-001-microsoft-365-security-licensing.md), [ADR-002](adr/ADR-002-hr-system-of-record-drives-identity.md), [ADR-003](adr/ADR-003-managed-detection-and-response.md), [ADR-004](adr/ADR-004-phishing-resistant-authentication-rollout.md), [ADR-006](adr/ADR-006-microsoft-365-backup.md), [ADR-007](adr/ADR-007-compliance-automation-platform.md), the [payroll diversion playbook](playbooks/payroll-diversion-and-email-compromise.md), and the [crosswalk](crosswalk/csf2-soc2-crosswalk.md).
- Passkeys by default and retirement of Microsoft-provided SMS and voice authentication. Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sms-voice-retirement . Checked 2026-10-13. Primary.
- Security Suites (Microsoft Licensing guidance; Microsoft Defender Suite, previously Microsoft 365 E5 Security). Microsoft. https://www.microsoft.com/licensing/guidance/Security-Suites . Checked 2026-10-13. Primary.
- Enterprise data protection in Microsoft Copilot and Microsoft Copilot Chat (product name change). Microsoft Learn. https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection . Checked 2026-10-13. Primary.
- CCPA Updates, Cybersecurity Audits, Risk Assessments, Automated Decisionmaking Technology (ADMT), and Insurance Regulations (rulemaking page). California Privacy Protection Agency. https://cppa.ca.gov/regulations/ccpa_updates.html . Checked 2026-10-13. Primary.
- Text of Regulations (CCPA Updates, Cyber, Risk, ADMT, and Insurance Regulations), section 7121 (timing of cybersecurity audits). California Privacy Protection Agency. https://cppa.ca.gov/regulations/pdf/ccpa_updates_cyber_risk_admt_appr_text.pdf . Checked 2026-10-13. Primary.
