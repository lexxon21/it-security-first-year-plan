# 04. Operating model, team, and budget

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

## Purpose and scope

This document sets out how Fabrikam, Inc. (fictional) organizes IT and security for the plan year: the team and hiring sequence, partners, who does what, forums, the budget proposal, and what the Director of IT and Security needs from each executive. Costs appear as categories, cost drivers, and relative size, never as dollar figures, and every cadence is a proposal ([01](01-scenario-and-assumptions.md)).

**Terms.** IT: information technology. KPI: key performance indicator. MDR: managed detection and response. MFA: multifactor authentication. GRC: governance, risk, and compliance. RACI: responsible, accountable, consulted, informed. SRE: Site Reliability Engineering. CEO, CFO, and CTO: the chief executive, financial, and technology officers. VP: vice president. HR: human resources. AI: artificial intelligence. ADR: architecture decision record. CSF: the National Institute of Standards and Technology (NIST) Cybersecurity Framework 2.0. SOC 2 is the attestation report on Fabrikam's controls that customers ask for; a Type 1 report covers control design at one date, and a Type II report also covers operation over a period ([10](10-governance-and-compliance-program.md)). Class A data is the data whose loss stops support for customers' payroll, Fabrikam's own payroll or payments, or incident response ([14](14-business-continuity-and-backup.md)). A Temporary Access Pass is a time-limited code that lets a person set up a sign-in method. Phases and milestones (M1 to M7) follow document [03](03-twelve-month-roadmap.md).

## Decision rights

The Director proposes the plan, budget, and policies, owns execution, and is accountable for the program; the executive team approves them; named executives own and accept business risks within document [11](11-risk-management.md)'s limits, and the Director never accepts risk on Fabrikam's behalf (full decision rights: [10](10-governance-and-compliance-program.md)).

## The team today and at month 12

| Role | Day 1 | Month 12 | Main work |
|---|---|---|---|
| Director of IT and Security | Starts, reporting to the CTO | In post | Plan, budget, and policies; execution; incident command; chairs the IT and Security Steering Group; covers the new roles until each starts |
| IT Operations Manager | In post | In post | Service desk, Change Advisory Board, lifecycle, consolidation waves, on-call lead, backups |
| Service Desk Analyst | Two of the three IT generalists | Same | The queue, caller verification, Temporary Access Passes, identity reconciliation |
| Systems Engineer (Identity and Endpoint) | The third IT generalist | Same | Conditional Access, Intune, single sign-on, provisioning, automation; most early build work, and the Security Engineer's hands-on work until that role starts |
| Security Engineer | None | From March 2027 in the base case | Privileged Identity Management, MDR liaison, detections, simulations, data loss prevention |
| GRC Analyst | None; a finance manager coordinates SOC 2 part time with an outside readiness consultant | From March 2027 in the base case | SOC 2, the risk register, vendor reviews, KPIs, the compliance platform |
| Product security | Senior engineers, informally | The Engineering Manager and the SRE lead | Production access, vulnerabilities, recovery, incidents (see the RACI) |

Primary on-call rotates weekly among the IT team and, once in post, the Security Engineer, with the Director as escalation.

## Hiring sequence

Recruiting is prepared in Phase 3. Offers go out after the executive team approves the budget at M3 (Thursday 2027-01-28), so in the base case the GRC Analyst and the Security Engineer start in March 2027. As an option, the executive team can pre-approve both roles at M2 so offers go out in January and both start in February.

Until each role starts, the interim owners in document [03](03-twelve-month-roadmap.md) carry its duties, and the appendix counts each role's actions by month. Interim owners cover each new role's March actions until it starts and pair with it through its first month; if either role starts after March, its March and April actions stay with the interim owners, and the next Quarterly Risk Review reports the effect on M6. Implementation help comes first from FastTrack for Microsoft 365, Microsoft's deployment assistance benefit, requested in December (06.23); the M3 budget then carries contracted build help for February to April and surge support for the February peak and the consolidation waves ([13](13-it-service-management.md)). The build partner's scope and the surge support terms are agreed in January, so contracted help starts right after M3.

## Partners

Four partners support the plan (appendix): the MDR provider, the SOC 2 audit firm, a penetration testing firm, and the IT hardware partner. Other third parties enter through intake, reviewed in proportion to the data they can reach ([10](10-governance-and-compliance-program.md), [15](15-enterprise-systems-and-saas.md)).

## Who does what: the RACI

The appendix RACI names one accountable party per activity, including the shared product security split: Engineering for the product platform, incidents, and disaster recovery, and the Chief Product Officer for customer administrator protection (R-02).

## Forums and cadence

The executive time ask: each executive gives one Phase 1 conversation, about 30 minutes per owned risk at M2 (December), the M3 meeting, the Day 120 readout (end of February 2027), the M7 review, and each Quarterly Risk Review (late January, April, July, and October). Policy co-owners and the IT and Security Steering Group clear the policies and KPI targets in January, so they reach the executive team as one consent item. The appendix lists each forum's members, cadence, and purpose ([10](10-governance-and-compliance-program.md), [11](11-risk-management.md), [12](12-metrics-and-executive-reporting.md), [13](13-it-service-management.md)).

## Budget proposal

The executive team approves the budget at M3 on current quotes ([ADR-001](adr/ADR-001-microsoft-365-security-licensing.md), [ADR-003](adr/ADR-003-managed-detection-and-response.md)). Since Microsoft's July 2026 update, Microsoft 365 E3 includes Defender for Office 365 Plan 1, Intune Plan 2, Remote Help, and Intune Advanced Analytics, so Phases 1 to 3 configure what Fabrikam already pays for ([06](06-microsoft-365-security-baseline.md)).

| Category | What it pays for | Cost drivers | Relative size (proposed order, confirmed by quotes at M3) |
|---|---|---|---|
| People | The two new roles; contracted build help and surge support; on-call pay or time off; training | Headcount and start dates; build and surge hours; the on-call policy; built or bought training content (M3) | Largest new recurring line |
| Licensing ([ADR-001](adr/ADR-001-microsoft-365-security-licensing.md)) | From Phase 4: Microsoft Defender Suite (formerly Microsoft 365 E5 Security) for all users (endpoint detection and response, risk-based sign-in, phishing simulation, and the data an MDR provider needs) and Microsoft Entra ID Governance (automated joiners and leavers, just-in-time administration); the fallback is in ADR-001. Conditional: a small certificate add-on for office Wi-Fi. Phase 5: Microsoft Copilot (formerly Microsoft 365 Copilot) pilot licenses after the readiness gate | About 450 seats, contract staff included for Governance; renewal dates | Second: a moderate per-user uplift (ADR-001), with Governance seats the largest identity cost (07) |
| Partners and services | The MDR service; the incident response retainer or pre-agreed emergency terms; SOC 2 audit fees; the readiness consultant until the GRC Analyst starts and at least through M4; one external penetration test, June to August 2027 (08); outside counsel if needed | MDR pricing basis; retainer terms; audit scope (two products, an added Type 1); test scope | The MDR service is the largest partner line; audit fees rise with the second product |
| Tooling ([ADR-006](adr/ADR-006-microsoft-365-backup.md), [ADR-007](adr/ADR-007-compliance-automation-platform.md)) | Microsoft 365 Backup; an isolated copy of class A data, if funded; the compliance platform, contracted in February 2027 and in use from April; small tools for on-call paging, log storage and alerting (08), vaults, email authentication reporting, lookalike domain monitoring from Phase 4 (15.19), out-of-band messaging and a phone bridge (14), a lab tenant (08), and Wi-Fi authentication; security keys and administrators' phones | Protected data volume (Microsoft 365 Backup is pay-as-you-go, billed through Azure); log volume; class A size; platform scope | Small next to the lines above, except backup, which grows with data |
| Internal time (no new spend) | Engineering time for the acquired product line, the product recovery test, the R-02 and R-08 treatments, and product KPI data; People time for new-hire identity checks; Finance and People time for call-backs; executive time for risk sessions | Engineering scope agreed with the Engineering Manager; hires and bank-detail changes per month | Engineering time is the largest internal cost, sized by quarter with the Engineering Manager before M3 |
| Contingency | A Windows 10 update bridge; single sign-on and provisioning upgrades; cross-tenant migration add-ons (sold to Enterprise Agreement customers; ADR-005 records the SharePoint site tool as private preview, as of 2026-10-13); Private Access for one surviving application (ADR-001); an independent cybersecurity audit, if General Counsel confirms the thresholds apply (10); extra incident response hours; and a costed simulation option if Defender Suite is declined | What discovery finds | Only if triggered; sized at M3 |

Most new recurring lines start between February and April 2027, so year one carries part of a year of each; the M3 proposal shows the year-one amount and the full-year run rate. Duplicate contracts from the acquisitions end at their notice dates and offset part of the cost ([15](15-enterprise-systems-and-saas.md), [ADR-005](adr/ADR-005-acquired-company-consolidation.md), [ADR-008](adr/ADR-008-endpoint-management-standard.md)).

**If a line is declined.** Without the two roles, the interim cover continues and the build stays with two people. Without Governance, the M6 lifecycle milestone is at risk and leaver removal stays partly manual. Without Defender Suite, the fallback keeps just-in-time administration and lifecycle automation, but the MDR service cannot work meaningfully, so the interim on-call model continues and R-10's residual risk goes to its owner ([ADR-001](adr/ADR-001-microsoft-365-security-licensing.md), [ADR-003](adr/ADR-003-managed-detection-and-response.md)). Without the platform, a control matrix and evidence calendar take its place ([ADR-007](adr/ADR-007-compliance-automation-platform.md)). If the isolated copy is declined, the CEO, as owner of R-03, accepts the residual risk for a set period within document [11](11-risk-management.md)'s limits ([ADR-006](adr/ADR-006-microsoft-365-backup.md)).

## What the Director needs from each executive

| Executive | Risks owned (proposed) | What the Director needs |
|---|---|---|
| CEO | R-03 | Chair the Quarterly Risk Review (proposal); approve the incident response plan; decide what reaches the investor board; accept R-03's residual if the isolated copy is declined, and join any acceptance of R-02 or R-08 |
| CFO | R-01, R-09, R-11 | Approve any Windows 10 bridge, and before mid-December class A backup spend and an incident response retainer, or pre-agreed emergency terms; agree that finance and payroll join the MFA and endpoint baselines in February; set the loss threshold that raises incident severity; have Finance call back on every vendor bank-detail change and track Governance and Entra ID P2 renewals, so administrator access stays time-bound ([06](06-microsoft-365-security-baseline.md)) |
| CTO | R-04, R-06, R-08, R-14 | Agree the discovery rules; before mid-December, as R-04's owner, accept the product recovery position through year-end on the evidence from 14.01, or ask Engineering for a limited recovery check that changes no production system; size Engineering time by quarter before M3; decide the R-08 engineering asks: single sign-on and MFA on code hosting, secret scanning that blocks credentials at commit, protected branches, pipeline secrets in a vault, and dependency alerts; approve customer-facing changes during the freeze with the Chief Customer Officer |
| Chief Product Officer | R-02 | At M3, decide the Director's R-02 proposal, which Engineering builds: MFA by default for customer administrators and payroll approvers, with passkeys and federation to the customer's identity provider where offered; step-up authentication on bank-detail changes, with notice to the worker and the administrator; a hold or verification before the first payment to a new bank account; and detection of a destination account that recurs across workers or customers ([11](11-risk-management.md)). If declined, R-02 stays outside appetite, and the Chief Product Officer and the CEO accept it for a set period; while its current rating stays Critical, only the executive team can accept it, 30 days at a time. Decide customer payroll contingency guidance with the Chief Customer Officer |
| Chief Customer Officer | R-07 | Time customer-facing changes such as sharing limits, and approve the email authentication enforcement calendar; own how Support handles customer payroll files; send approved customer notices |
| VP of People | R-05, R-13, R-15 | Decide on-call pay or time off before the rotation starts in November; staff the new-hire identity check and enter terminations on the day notice is given; call back on every employee direct-deposit change; phone urgent leavers in; issue the interim AI notice; lead employee communication in incidents and consolidation waves |
| General Counsel | R-10, R-12 | Build the contract clause inventory; answer the legal questions log, including the automated decisionmaking position before 2027-01-01 and, in Phase 1, whether California's cybersecurity audit regulations apply, which would add an independent cybersecurity audit; approve the holding statements and contract templates |

## Resourcing and dependencies

Budget lines come from [ADR-001](adr/ADR-001-microsoft-365-security-licensing.md), [ADR-003](adr/ADR-003-managed-detection-and-response.md), [ADR-006](adr/ADR-006-microsoft-365-backup.md), and [ADR-007](adr/ADR-007-compliance-automation-platform.md), and duties from documents 10, 11, 13, and 14; this document feeds [00](00-executive-summary.md), [02](02-first-90-days.md), and [03](03-twelve-month-roadmap.md).

## Risks and open questions

- **Hiring timing.** In the base case the interim owners carry the February registration peak and MDR onboarding; pre-approval at M2 brings both starts to February.
- **A small team.** On-call fatigue and key-person dependency (R-14) stay high until the MDR service is live ([08](08-detection-and-incident-response.md), [11](11-risk-management.md)).
- **Engineering capacity.** R-02 (customer administrator takeover), R-04 (product outage in payroll processing windows), and R-08 (integration credential compromise) depend on Engineering's roadmap and partners' controls ([11](11-risk-management.md)).

## Framework mapping

By identifier only, consistent with the [crosswalk](crosswalk/csf2-soc2-crosswalk.md).

| Theme | NIST CSF 2.0 | SOC 2 (2017 Trust Services Criteria) |
|---|---|---|
| Roles, structure, and the RACI | GV.RR-01, GV.RR-02 | CC1.1, CC1.3 |
| Team, hiring, and resources | GV.RR-03, GV.RR-04 | CC1.4 |
| Accountability for assigned duties | GV.RR-02, GV.RR-04 | CC1.5 |
| Forums and oversight | GV.OV-01, GV.OV-02, GV.OV-03 | CC1.2, CC4.1, CC4.2 |
| Partners and shared responsibilities | GV.SC-02, GV.SC-05 | CC2.3, CC9.2 |

## Appendix: partners

| Partner | Role, timing, and governance |
|---|---|
| MDR provider | Round-the-clock triage and pre-approved containment in Microsoft Defender; Microsoft's Defender Experts MDR Plan 1 is scored against at least two independent providers, chosen at M3, and live by the end of April. Microsoft states that neither Defender Experts plan is an incident response engagement, so an incident response retainer, or pre-agreed emergency terms with an incident response firm, is in place before mid-December with the CFO's approval; it folds into the MDR contract only if the chosen provider includes incident response, and otherwise stays beside it. Response authority is approved with POL-08 |
| SOC 2 audit firm | Agrees in-period changes before M4; tests both periods and the acquired product line's Type 1 and Type II; does not design or run Fabrikam's controls, and discloses any arrangement with the compliance platform's vendor |
| Penetration testing firm | One external test in year one, June to August 2027, after the Phase 4 controls land and before the Type 1 date, scoped with Engineering to the corporate tenant and identity, the customer administrator sign-in and bank-change paths, and integrations (documents 08 and 17); findings feed KPI-18 and the R-02 and R-08 ratings; no recurring cadence is set |
| IT hardware partner | Enrollment at purchase, home delivery, spares, returns, sanitization certificates, security keys, and administrators' phones; a deeper POL-10 review, because its devices may hold Restricted data |

## Appendix: RACI

R does the work, A answers for the outcome (one per row), C is consulted, and I is informed. Engineering includes the CTO, the Engineering Manager, the SRE lead, and the Chief Product Officer where named. Policy owners and co-owners are in document 10. The last five rows are the shared product security split with Engineering; the SOC 2 scope covers both sides.

| Activity | Corporate IT | Engineering | People | Legal | Finance |
|---|---|---|---|---|---|
| Microsoft 365 security baseline | A, R | C | I | C | C |
| HR records that drive accounts | R (daily reconciliation) | I | A, R | I | I |
| Joiner, mover, and leaver automation | A, R | C | R | C | R |
| Access reviews | A, R | R (production) | R (HR and payroll) | I | R (finance systems) |
| Corporate detection and response with the MDR provider | A, R | C | C | C | C |
| Notifying customers, individuals, or regulators | C | C | C | A, R | I |
| Vendor payment and bank-detail changes | C | I | I | C | A, R |
| Employee direct-deposit changes | C | I | A, R | C | C |
| Microsoft 365 backup and corporate continuity | A, R | I | R | R | R |
| SOC 2 program, including the acquired product line's route | A, R | R (product controls and gaps) | R (HR records) | C | R until M4, then C |
| Third-party risk and application intake | A, R | C | I | R (contracts) | R (payment after intake) |
| Acquisition consolidation | A, R | C | R | C | R |
| Product platform security | C | A, R | I | I | I |
| Product incidents | R (security investigation) | A, R (technical response) | I | C | I |
| Product disaster recovery and its yearly test | C | A, R | I | C | I |
| Customer administrator protection (R-02) | C | A (Chief Product Officer), R | I | C | I |
| Review gate for product changes, AI features included | R | A (Chief Product Officer), R | I | R | I |

Rows come from documents 01, 06 to 16, ADR-002, ADR-005, ADR-006, and the [payroll diversion playbook](playbooks/payroll-diversion-and-email-compromise.md).

## Appendix: forums

| Forum | Members | Cadence (proposal) | Purpose |
|---|---|---|---|
| Executive team | CEO, CFO, CTO, Chief Product Officer, Chief Customer Officer, VP of People, General Counsel | Its normal schedule, plus M3 (Thursday 2027-01-28), the Day 120 readout (end of February 2027), and M7 | Approves the plan, budget, policies, CSF Profiles, and SOC 2 scope changes; named executives accept risk |
| Quarterly Risk Review | The executive team; the CEO chairs (proposal) | Late January (M3), April, July, and October (M7) | Re-rates risks with their owners, reviews every KPI and open exception, decides on risks outside appetite; the Director drafts a board summary afterward if the CEO asks, and the CEO decides its use |
| IT and Security Steering Group | The Director (chair), CTO, CFO, VP of People, and leaders from Customer and Product | Monthly from November 2026 | The monthly scorecard, serious incidents, Critical and High risks, and exceptions; priorities inside the approved plan; clears policies and KPI targets in January before M3 |
| Change Advisory Board | The IT Operations Manager (chair) and the IT and security team; Engineering for shared changes | Weekly from week 2 | Corporate IT changes, flagging any that touch a SOC 2 control |

## Appendix: capacity by role and month

How many phase-plan actions each role owns in each month from November 2026 to April 2027, counted from the phase plans of documents 01 and 05 to 17. An action counts once in each month it runs, under the first role its Owner cell names, so 08.13 counts under the GRC Analyst although the Director runs its April notification drill. Phase 1, 2, and 3 actions count in November, December, and January; 06.23, a Phase 3 action, also counts in December, when the Director requests FastTrack. A Phase 4 action counts in the months its row names: one month, a range, or from a month to the end of April; a Phase 4 row that names no month counts in each Phase 4 month its owner is in post. Action 10.20 counts under the Director in February and the GRC Analyst in March, as its Owner cell sets. Every action weighs the same, so the counts show where work concentrates, not hours. Recurring duties are not counted: on-call weeks, the service desk queue, the Change Advisory Board, monthly reviews, and incident command.

| Role | November 2026 | December 2026 | January 2027 | February 2027 | March 2027 | April 2027 |
|---|---|---|---|---|---|---|
| Director of IT and Security | 29 | 20 | 24 | 11 | 7 | 6 |
| IT Operations Manager | 17 | 14 | 2 | 6 | 6 | 5 |
| Service Desk Analyst (two people) | 1 | 3 | 4 | 2 | 1 | 1 |
| Systems Engineer (Identity and Endpoint) | 7 | 8 | 11 | 14 | 11 | 8 |
| Security Engineer (from March 2027 in the base case) | Not in post | Not in post | Not in post | Not in post | 10 | 9 |
| GRC Analyst (from March 2027 in the base case) | Not in post | Not in post | Not in post | Not in post | 2 | 8 |
| All roles | 54 | 45 | 41 | 33 | 37 | 37 |

**What the counts show.**

- **Phases 1 to 3 rest on the Director:** 72 actions in 90 days (06.23 counted in both December and January), while the Director covers both unfilled roles and commands SEV-1 and SEV-2 incidents (document 08). The readiness consultant drafts the policy set and the evidence calendar for the Director's review, and the finance manager supports SOC 2 through M4 (document 10).
- **The Systems Engineer carries the build.** December holds 8 actions. Consent and guest limits, file server scans, and the endpoint baseline with its elevation service sit in January (06.12, 06.13, 15.05, 15.07, 06.17, 13.08), so January holds 11, and finance and payroll join the endpoint baseline in February, in weeks 2 to 3 after their identity changes in week 1 (06.24). February is the peak at 14 actions, beside the service desk's registration surge after 2027-02-01. FastTrack, requested in December, and contracted build help, scoped in January (06.23), are in place for February to April.
- **March changes the shape.** In the base case the Security Engineer takes 10 actions in March, and the GRC Analyst 2 in March and 8 in April. Interim owners cover each role's March actions until it starts and pair with it through its first month (hiring sequence), and when Phase 4 work collides, the IT and Security Steering Group sets the order and consolidation waves yield first (document 15).

**Actions behind the counts.** Each ID points to the phase plan of the document its first two digits name.

- **Director of IT and Security.** November: 01.01, 05.01, 05.03, 05.04, 05.09 to 05.11, 06.03, 07.03, 07.04, 08.02, 08.04, 09.01, 09.02, 10.01 to 10.06, 11.01, 11.02, 12.01, 12.02, 14.02, 14.03, 16.01, 16.02, 17.01. December: 06.23, 07.06, 08.05, 08.06, 09.03, 10.07 to 10.12, 11.03 to 11.05, 12.03, 12.04, 14.07, 15.04, 16.03, 16.04. January: 01.02, 05.13, 06.23, 07.08, 08.08, 09.07, 09.08, 10.13 to 10.17, 11.06, 11.07, 12.05, 12.06, 13.13, 13.14, 14.09, 15.09, 16.05 to 16.07, 17.02. February: 05.14, 08.09, 08.10, 09.10, 10.18 to 10.20, 11.08, 12.07, 14.13, 17.03. March: 05.14, 08.10, 09.12, 10.19, 10.21, 11.08, 14.13. April: 05.14, 08.10, 09.12, 10.19, 12.10, 14.13.
- **IT Operations Manager.** November: 05.02, 05.05 to 05.08, 06.05, 06.07, 06.08, 07.01, 07.02, 08.01, 13.01 to 13.04, 14.01, 15.01. December: 05.12, 06.15, 06.20, 07.05, 08.07, 09.04, 13.06, 13.07, 13.09 to 13.11, 14.05, 14.06, 15.06. January: 07.09, 15.10. February: 06.31, 07.11, 14.10, 15.16, 15.17, 15.21. March: 06.31, 13.18, 14.12, 15.16, 15.17, 15.21. April: 06.31, 14.14, 15.16, 15.17, 15.21.
- **Service Desk Analyst.** November: 13.05. December: 06.11, 07.07, 15.08. January: 06.21, 07.10, 09.06, 13.12. February: 13.15, 13.20. March and April: 13.20.
- **Systems Engineer (Identity and Endpoint).** November: 06.01, 06.02, 06.04, 06.06, 08.03, 15.02, 15.03. December: 06.09, 06.10, 06.14, 06.16, 06.18, 06.19, 09.05, 14.04. January: 06.12, 06.13, 06.17, 06.22, 13.08, 14.08, 15.05, 15.07, 15.11 to 15.13. February: 06.24 to 06.27, 06.29, 07.12, 07.15, 08.11, 09.09, 13.16, 13.17, 14.11, 15.14, 15.19. March: 06.25 to 06.27, 06.29, 07.13, 07.15, 08.11, 13.16, 13.17, 15.14, 15.19. April: 06.26, 06.27, 06.29, 07.15, 08.11, 13.17, 15.14, 15.19.
- **Security Engineer.** March: 06.28, 06.30, 08.12, 09.11, 15.15, 15.18, 15.20, 16.08 to 16.10. April: the same, except 09.11.
- **GRC Analyst.** March: 10.20, 12.08. April: 07.14, 08.13, 09.13, 10.22, 11.09, 12.08, 12.09, 13.19.

## Appendix: action index

The actions behind this document's hiring, budget, and forum lines. Each ID points to the phase plan of the document its first two digits name.

| Line in this document | Actions |
|---|---|
| SOC 2 coordination until the GRC Analyst starts, with the readiness consultant kept until then and at least through M4 | 10.16 |
| Actions before March 2027 that name an interim owner until a new role starts | 06.25, 08.10, 09.09, 10.19, 10.20, 14.11, 17.03 |
| FastTrack requested in December; the build partner's scope and the surge support terms agreed in January, and surge staff trained on the caller verification script on 28 and 29 January, after the M3 approval | 06.23, 13.14 |
| Surge support, the spare pool, partner terms, and the hiring triggers in the M3 budget; the triggers checked at month 9 | 13.14, 13.23 |
| Licensing: Microsoft Defender Suite or the fallback, and Microsoft Entra ID Governance | 06.23, 07.08 |
| Conditional licensing lines: the certificate add-on for office Wi-Fi; Private Access for a surviving application | 06.26, 06.31 |
| Copilot pilot line in the M3 budget; pilot licenses after the readiness gate | 16.06, 16.11 |
| MDR provider and the incident response retainer: evaluation and retainer before mid-December, selection at M3, and live by the end of April | 08.06, 08.08, 08.10 |
| The product recovery position before mid-December, on the Phase 1 evidence | 14.01, 14.07, 11.04 |
| Finance and payroll on the MFA and endpoint baselines in February, the timing the CFO agrees | 06.10, 06.17, 06.24 |
| On-call paging, and alerts on emergency access sign-ins, Temporary Access Passes, and method changes | 08.01, 08.03 |
| Lookalike domain monitoring from Phase 4 | 15.19 |
| One external penetration test, June to August 2027 | 08.14 |
| Microsoft 365 Backup and the isolated copy | 14.03, 14.04, 14.09, 14.15 |
| Compliance platform: evaluation, contract, and connection | 10.15, 10.18, 10.20 |
| Single sign-on and provisioning upgrades, and cross-tenant add-ons | 15.09 |
| Windows 10 bridge | 06.07 |
| Forums: charters and the first Steering Group; the Change Advisory Board from week 2; the Day 120 readout; the Quarterly Risk Reviews; the annual program review | 10.03, 13.02, 12.07, 12.06, 12.10, 12.11, 12.12 |

## Sources

- Plan documents relied on (internal cross-references, not external sources): [01. Scenario and assumptions](01-scenario-and-assumptions.md); [02. The first 90 days](02-first-90-days.md); [03. Twelve-month roadmap](03-twelve-month-roadmap.md); [05. Environment discovery](05-environment-discovery.md); [06. Microsoft 365 security baseline](06-microsoft-365-security-baseline.md); [07. Identity lifecycle: joiners, movers, and leavers](07-identity-lifecycle-joiners-movers-leavers.md); [08. Detection and incident response](08-detection-and-incident-response.md); [09. Security awareness and training](09-security-awareness-and-training.md); [10. Governance and compliance program](10-governance-and-compliance-program.md); [11. Risk management](11-risk-management.md); [12. Metrics and executive reporting](12-metrics-and-executive-reporting.md); [13. IT service management](13-it-service-management.md); [14. Business continuity and backup](14-business-continuity-and-backup.md); [15. Enterprise systems and SaaS](15-enterprise-systems-and-saas.md); [16. AI adoption guardrails](16-ai-adoption-guardrails.md); [17. Threat profile](17-threat-profile.md); [ADR-001](adr/ADR-001-microsoft-365-security-licensing.md), [ADR-002](adr/ADR-002-hr-system-of-record-drives-identity.md), [ADR-003](adr/ADR-003-managed-detection-and-response.md), [ADR-005](adr/ADR-005-acquired-company-consolidation.md), [ADR-006](adr/ADR-006-microsoft-365-backup.md), [ADR-007](adr/ADR-007-compliance-automation-platform.md), and [ADR-008](adr/ADR-008-endpoint-management-standard.md); the [payroll diversion and email compromise playbook](playbooks/payroll-diversion-and-email-compromise.md); and the [CSF 2.0 and SOC 2 crosswalk](crosswalk/csf2-soc2-crosswalk.md).
- Microsoft 365 Pricing and Packaging Updates. Microsoft (Licensing news). https://www.microsoft.com/en-us/licensing/news/2026-m365-packaging-pricing-updates . Checked 2026-10-13. Primary.
- Microsoft 365 Packaging and Pricing Updates Public FAQ. Microsoft (Licensing news). https://www.microsoft.com/en-us/licensing/news/2026-m365-packaging-pricing-updates-faq . Checked 2026-10-13. Primary.
- FastTrack for Microsoft 365 Benefit (Request for Assistance; scope varies by workload). Microsoft Learn. https://learn.microsoft.com/en-us/microsoft-365/fasttrack/introduction . Checked 2026-10-14. Primary.
- Eligibility (FastTrack for Microsoft 365). Microsoft Learn. https://learn.microsoft.com/en-us/microsoft-365/fasttrack/eligibility . Checked 2026-10-13. Primary.
- Security Suites (Microsoft Licensing guidance; Microsoft Defender Suite, previously Microsoft 365 E5 Security). Microsoft. https://www.microsoft.com/licensing/guidance/Security-Suites . Checked 2026-10-13. Primary.
- Microsoft Entra service description (Microsoft Entra ID P2 with the Defender Suite add-on). Microsoft Learn. https://learn.microsoft.com/en-us/office365/servicedescriptions/azure-active-directory . Checked 2026-10-13. Primary.
- Microsoft Entra ID Governance licensing fundamentals (Governance products, Privileged Identity Management licensing, and license expiry). Microsoft Learn. https://learn.microsoft.com/en-us/entra/id-governance/licensing-fundamentals . Checked 2026-10-13. Primary.
- Microsoft Cloud PKI for Microsoft Intune (sold as an add-on to Intune Plan 1 or Plan 2; the certificate add-on ADR-001 relies on). Microsoft Learn. https://learn.microsoft.com/en-us/intune/cloud-pki/ . Checked 2026-10-13. Primary.
- Cross-tenant OneDrive migration overview (Cross Tenant User Data Migration, an add-on for Enterprise Agreement customers). Microsoft Learn. https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-onedrive-migration . Checked 2026-10-13. Primary.
- Cross-tenant SharePoint site migration overview (Cross-Tenant Shared Data Migration, available only to Enterprise Agreement customers). Microsoft Learn. https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration . Checked 2026-10-13. Primary.
- What is Microsoft Defender Experts MDR? Microsoft Learn. https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-overview . Checked 2026-10-13. Primary.
- Overview of Microsoft 365 Backup (pay-as-you-go billing). Microsoft Learn. https://learn.microsoft.com/en-us/microsoft-365/backup/backup-overview . Checked 2026-10-13. Primary.
- Enterprise data protection in Microsoft Copilot and Microsoft Copilot Chat (product name change). Microsoft Learn. https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection . Checked 2026-10-13. Primary.
