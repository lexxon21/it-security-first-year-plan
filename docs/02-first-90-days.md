# 02. The first 90 days

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

## Purpose and scope

This document assembles the Phase 1 to 3 actions into one sequence for the Director of IT and Security's first 90 days at Fabrikam, Inc. (fictional), from 2026-11-02 to the end of January 2027, with readouts at days 30, 60, and 90 and a closing Day 120 readout (D120, end of February 2027). Every cadence, target, and date is a proposal ([01](01-scenario-and-assumptions.md)).

**Terms.** SOC 2: the attestation report on Fabrikam's controls that customers ask for; the current review period ends on 2027-03-31 (M4). IT: information technology. MFA: multifactor authentication. KPI: key performance indicator. MDR: managed detection and response. GRC: governance, risk, and compliance. HR: human resources. AI: artificial intelligence. CFO and CTO: the chief financial and technology officers. ADR: architecture decision record. CSF: the National Institute of Standards and Technology (NIST) Cybersecurity Framework 2.0. DMARC (Domain-based Message Authentication, Reporting, and Conformance): the published policy for mail that fails Fabrikam's email authentication.

## Ground rules for all 90 days

- No change breaks or moves evidence for the current SOC 2 period without the audit firm's agreement ([10](10-governance-and-compliance-program.md), [ADR-007](adr/ADR-007-compliance-automation-platform.md)).
- Discovery stays read-only, adds no Global Administrator and no Conditional Access exclusion; the emergency access group stays the only one ([05](05-environment-discovery.md), [06](06-microsoft-365-security-baseline.md), [11](11-risk-management.md)).
- Signs of active harm go to the CTO and the accountable executive the same day, and the fix takes the emergency change path ([08](08-detection-and-incident-response.md), [13](13-it-service-management.md)).
- Baselines come before changes, so D120 can show what moved.
- Changes customers would notice land before mid-December or after January 31, and policies start in report-only mode, which records what a policy would block without blocking it; from mid-December through January, finance and payroll staff see no new sign-in or device enforcement and business teams no simulations or exercises ([06](06-microsoft-365-security-baseline.md), [08](08-detection-and-incident-response.md), [09](09-security-awareness-and-training.md), [13](13-it-service-management.md), [ADR-004](adr/ADR-004-phishing-resistant-authentication-rollout.md)).
- Before M3, spend beyond Microsoft 365 E3 is limited to class A backup (data whose loss stops Fabrikam's own payroll or payments, or incident response) and any Windows 10 bridge the CFO approves; an incident response retainer, or pre-agreed emergency terms, before mid-December with the CFO's approval; and the small items listed under Resourcing and dependencies ([ADR-001](adr/ADR-001-microsoft-365-security-licensing.md), [08](08-detection-and-incident-response.md), [14](14-business-continuity-and-backup.md)).
- No Microsoft Copilot (formerly Microsoft 365 Copilot) license comes before the oversharing work ([16](16-ai-adoption-guardrails.md)).
- The Director never accepts risk or approves exceptions on Fabrikam's behalf, and product security and product disaster recovery stay with Engineering ([04](04-operating-model-team-and-budget.md), [11](11-risk-management.md)).

## Phase 1: Listen and learn (days 1 to 30, November 2026)

### Week 1: meet, agree, and prepare

- **Executives.** Conversations start with the [stakeholder conversation guide](templates/stakeholder-conversation-guide.md), recording each executive's risk tolerance and proposed risk ownership.
- **Exports.** Microsoft Entra keeps sign-in and audit logs for only 30 days on Microsoft Entra ID P1, which E3 includes, so dated exports start at once through read-only reporting access (the admin centers' report and export views, opened from the IT team's existing administrator accounts, with each export logged in the findings log) until the week-2 Change Advisory Board approves end-dated discovery roles.
- **The SOC 2 audit firm.** With the finance manager who coordinates SOC 2, the Director agrees how in-period changes are proposed and evidenced; the CTO agrees the discovery rules.
- **Urgent fixes** are prepared and disclosed to the audit firm in week 1 and applied at the first Change Advisory Board in week 2: two emergency access accounts whose every sign-in pages the on-call; MFA on every administrator, and fewer than five Global Administrators; on-call alert routing; and the Microsoft Entra log archive. The one week-1 exception is a sample restore with today's tools, which changes no control.

### Weeks 2 to 4: discovery, early decisions, and M1

Discovery maps people, processes, technology, data, vendors, and internet-facing assets, including the product's data paths with Engineering. Every SMTP AUTH sender (scanners and applications that sign in to send mail) gets a fix and an owner ahead of Microsoft's announced end-of-December 2026 default change, and each remaining Windows 10 device a dated path. The weekly Change Advisory Board, an after-hours urgent line, and the first IT and Security Steering Group start; the service desk verifies every caller before a password or MFA reset, a control that takes no exception ([11](11-risk-management.md)); and every KPI gets a first value or a dated "no data yet".

### Day 30 readout (M1)

The executive team receives the listening report, the environment baseline with inventories v1 and verified day-1 assumptions, a top risks draft with a proposed executive owner for each risk, and the KPI baselines.

## Phase 2: Stabilize (days 31 to 60, December 2026)

Before the mid-December freeze, three changes are visible: impersonation warnings for payment approvers and executives; view-only "Anyone" links that expire after 7 days, once the Chief Customer Officer's team has warned the customers who receive them; and phishing-resistant sign-in for administrators, while the wave 2 group (finance, payroll, People, Support staff with customer data access, executives, and IT staff daily accounts) registers. Also before the freeze: external forwarding off, sender signing, the parked brand domain (06.16), legacy protocols and device code sign-in blocked for everyone, one MFA baseline for everyone but finance and payroll, class A backup, the incident response retainer, and year-end sessions and coverage. Finance and payroll join the MFA and endpoint baselines in February, keeping today's MFA through year-end so payroll runs without new prompts, while the legacy and device code blocks apply to them now.

The rest of December brings office network fixes, the readiness consultant's draft of the policy set for the Director's review, the current CSF Profile at Category level, vendor reviews, the MDR evaluation, the FastTrack request, and the interim AI notice, which says which AI tools staff may use until POL-02 is approved.

### Day 60 readout (M2)

Quick wins are in place, every risk in register v1 has an owner, and the SOC 2 period is on track; the December scorecard showed baselines.

## Phase 3: Commit (days 61 to 90, January 2027)

January brings internal changes: app consent is limited before the HR integration credential is issued, guest access is bounded, and the endpoint baseline reaches everyone except finance and payroll.

### Off text and voice codes before 2027-02-01

From that date Microsoft stops sending its own text and voice codes for most users, and anyone left on them meets a blocking prompt to register a passkey. Fabrikam confirms every user has another method, staffs the service desk, and removes text and voice from its methods policy ([ADR-004](adr/ADR-004-phishing-resistant-authentication-rollout.md)). New hires onboard with a Temporary Access Pass (a time-limited code) and a passkey (a sign-in a fake website cannot capture); each new account stays disabled and each pass unreleased until a trained People verifier checks the new hire on video against a government-issued ID and the HR record, so no first credential goes out without a recorded identity check (R-15).

### Building for February

The HR feed is built and tested, data loss prevention for payroll identifiers runs in simulation, class B data goes under backup, and consolidation is rehearsed; compliance platforms are evaluated for the M3 budget. The Director personally covers the GRC and SOC 2 program work with the readiness consultant, kept at least through M4, and the finance manager supports SOC 2 through M4.

### The M3 package

On Thursday 2027-01-28, alongside the first Quarterly Risk Review, the executive team approves the 12-month plan, the budget ([04](04-operating-model-team-and-budget.md)), and the items in the appendix, including both CSF Profiles: the current Profile, where Fabrikam's practice stands (at Category level, with Subcategory detail by M7), and the target, where the plan commits to take it. Policy co-owners and the IT and Security Steering Group clear the policies and KPI targets in January, so they reach the executive team as one consent item; the meeting spends its time on the budget, the appetite, and the R-08 decision.

### Day 90 readout (M3)

Beyond the approvals ([10](10-governance-and-compliance-program.md), [11](11-risk-management.md)), day-90 success means every user holds a sign-in method other than text or voice codes before 2027-02-01; every administrator uses phishing-resistant methods, with fewer than five Global Administrators and fewer than 10 standing privileged assignments (KPI-08, KPI-09); every in-period SOC 2 change is agreed and recorded; class A data is restorable, SMTP AUTH is fixed, and mail protections went live before the freeze; and a high-severity alert pages a person at any hour, with best-effort response until the MDR provider is live ([08](08-detection-and-incident-response.md)).

## Day 120: first results

The Day 120 readout on Friday 2027-02-26 covers what has measurably changed since day 1, the February actions under way (appendix), and what is at risk.

### What will have measurably changed

| KPI | Phase 1 baseline | Expected at D120 |
|---|---|---|
| KPI-08 Phishing-resistant MFA coverage | Mostly push or text codes | Administrators 100 percent; the wave 2 group enforced; no user relying only on text or voice codes |
| KPI-09 Standing privileged assignments | All standing | Fewer than five Global Administrators and fewer than 10 standing privileged assignments; 2, the emergency access accounts only, by the end of Phase 4 |
| KPI-12 Leaver access removed on time | Six-month lookback | Checked daily against the HR feed; no known leaver enabled |
| KPI-20 Tickets resolved within target | Few service levels | 85 percent (the target from Phase 3), through the February surge |
| KPI-01 Top risks with owners and approved plans; KPI-02 Policies reviewed in cycle | No register; stale policies | 100 percent since M3 |
| KPI-03 SOC 2 controls without exceptions; KPI-04 Open audit exceptions | Last report's open exceptions | No new exceptions caused by the Director's changes; open exceptions owned and dated, median age under 60 days (from Phase 4) |
| KPI-05 Third parties with a current review | Reviews on file at M1 | Full reviews of vendors holding customer workforce data |
| KPI-19 Restore tests meeting target | None documented for Microsoft 365 | Class A restore tested; reported monthly |

Baselines come from 05.10, and full KPI names and targets from [12](12-metrics-and-executive-reporting.md) and the [KPI catalog](../data/kpi-catalog.csv). KPI-15 starts with the March simulation (09.11); KPI-16 stays interim until the MDR provider is live (08.10).

### What D120 flags as at risk

- Anything funded only through the fallback ([ADR-001](adr/ADR-001-microsoft-365-security-licensing.md)), and R-10's gap until the MDR provider is live ([11](11-risk-management.md)).
- Service desk load after 2027-02-01; the next consolidation wave waits if service KPIs slip ([15](15-enterprise-systems-and-saas.md)).
- The audit firm's agreement on MDR monitoring evidence ([08](08-detection-and-incident-response.md)).
- The main domain may hold DMARC at quarantine into early Phase 5 ([06](06-microsoft-365-security-baseline.md)).

## Resourcing and dependencies

- **Roles.** The Director leads, the IT team runs exports and changes, and document [04](04-operating-model-team-and-budget.md) sets executive time and each role's monthly load.
- **Partners.** The SOC 2 audit firm, the readiness consultant, an incident response firm, the IT hardware partner, and the penetration testing firm's past reports ([05](05-environment-discovery.md), [06](06-microsoft-365-security-baseline.md), [08](08-detection-and-incident-response.md), [10](10-governance-and-compliance-program.md)).
- **Licenses and spend.** Microsoft 365 E3 only before M3 ([ADR-001](adr/ADR-001-microsoft-365-security-licensing.md)), plus security keys, administrators' phones, log storage and alerting, a DMARC report processor, vaults, on-call paging, class A backup consumption, the incident response retainer, and any Windows 10 bridge ([06](06-microsoft-365-security-baseline.md), [08](08-detection-and-incident-response.md), [14](14-business-continuity-and-backup.md)).
- **Depends on** documents 01 and 05 to 17 and the ADRs; feeds [00](00-executive-summary.md) and [03](03-twelve-month-roadmap.md).

## Risks and open questions

- Thirty days is short, so some baselines are proxies ([05](05-environment-discovery.md)).
- Urgent fixes wait for the audit firm's agreement and the week-2 Change Advisory Board ([13](13-it-service-management.md)).
- December load falls on the same finance, payroll, People, and executive time ([11](11-risk-management.md)).
- The SMTP AUTH date comes from a secondary source and is rechecked before acting ([06](06-microsoft-365-security-baseline.md)).
- The current SOC 2 report may still carry exceptions inherited from before day 1; the readiness consultant forecasts them, and the CFO and the Sales leader are briefed before the report issues ([10](10-governance-and-compliance-program.md)).

## Framework mapping

By identifier only, consistent with the [crosswalk](crosswalk/csf2-soc2-crosswalk.md).

| Theme | NIST CSF 2.0 | SOC 2 (2017 Trust Services Criteria) |
|---|---|---|
| Context, discovery, and inventories | GV.OC-01, GV.OC-03, ID.AM-01, ID.AM-02, ID.AM-07 | CC2.1, CC3.1 |
| Risk identification and the register | ID.RA-03, ID.RA-04, ID.RA-05, GV.RM-06 | CC3.2 |
| In-period change control for SOC 2 | ID.RA-07 | CC3.4 |
| Policy set approved at M3 | GV.PO-01, GV.PO-02 | CC5.3 |
| Readouts at days 30, 60, 90, and 120 | GV.OV-03 | CC4.1 |

## Appendix: action index

Actions by period, in the order of the sections above. Each ID points to the phase plan of the document its first two digits name (06.04 is in document 06).

### Phase 1, week 1

| What happens | Actions |
|---|---|
| Executive conversations, with each executive's risk tolerance and proposed risk ownership | 05.03, 11.02 |
| Exports, each recording its date range, through read-only reporting access from the IT team's existing administrator accounts, each logged in the findings log, until the week-2 Change Advisory Board approves end-dated discovery roles | 05.02 |
| In-period change rules, urgent changes included, agreed with the SOC 2 audit firm through the finance manager; discovery rules agreed with the CTO | 05.01, 10.02 |
| Urgent fixes, prepared and disclosed in week 1 and applied at the week-2 board: two emergency access accounts; MFA on every administrator and fewer than five Global Administrators; alerts routed to an on-call alias, with a phone page for high-severity alerts, an interim rotation, and an incident register; the Microsoft Entra log archive, with alerts that page the on-call for every emergency access sign-in and, before the wave 2 group registers, flag every Temporary Access Pass and method change | 06.01, 06.03, 08.01, 08.02, 08.03 |
| A sample restore with today's tools, run in week 1 because it changes no control | 14.01 |

### Phase 1, weeks 2 to 4

| What happens | Actions |
|---|---|
| Remaining conversations and process observation, with business impact, AI, and training questions | 05.03, 14.02, 16.01, 09.01 |
| Weekly Change Advisory Board, an after-hours urgent line, and no reset on a caller's word (not open to exception, [11](11-risk-management.md)) | 13.02, 13.04, 13.03 |
| SOC 2 report, policies, control owners, the evidence calendar the readiness consultant drafts, and the forecast of exceptions inherited from before day 1; lifecycle descriptions; contract clauses and legal questions with General Counsel | 05.04, 10.01, 07.03, 08.04, 10.05 |
| Identity state and leaver timings; every account matched to an owner, confirmed leavers disabled; HR data owners; report-only Conditional Access baseline | 05.05, 06.02, 07.01, 07.02, 07.04, 06.04 |
| One device inventory and asset register; current settings recorded | 05.06, 13.05, 06.08 |
| DMARC aggregate reporting on every sending domain, including a first DMARC record on the older brand domain that still sends (no delivery change); a fix and an owner for every SMTP AUTH sender, customer-facing first, ahead of Microsoft's announced end-of-December 2026 default change | 05.07, 06.06, 06.05 |
| Each remaining Windows 10 device upgraded, replaced, or bridged with Extended Security Updates Year 2 if the CFO approves (Year 1 ended 2026-10-13) | 06.07 |
| Application, internet-facing asset, acquisition, domain, and vendor inventories; new vendors paid only after intake | 05.08, 15.01, 15.02, 15.03, 10.04 |
| Product data paths and recovery status with Engineering; class A backup spend requested from the CFO | 05.09, 14.03 |
| Forum charters and the first IT and Security Steering Group; reporting calendar; CSF Profile scope; risk method; threat profile | 10.03, 12.02, 10.06, 11.01, 17.01 |
| A first value, or a dated "no data yet", for every KPI | 05.10, 12.01, 13.01 |
| Learning plan and November module; interim AI notice drafted | 09.02, 16.02 |
| The Day 30 readout (M1): listening report, environment baseline, verified day-1 assumptions, and top risks draft | 01.01, 05.11 |

### Phase 2, before the mid-December freeze

| What happens | Actions |
|---|---|
| Mail protections, including impersonation protection for executives and payment approvers; external forwarding off; sender signing and parked-domain records on the older brand domain that no longer sends; SMTP AUTH switched off once fixed | 06.14, 06.16, 06.15 |
| Administrators on phishing-resistant methods; legacy protocols and device code sign-in blocked for everyone, finance and payroll included; one MFA baseline for everyone except finance and payroll, who join in February with the wave 2 enforcement; the wave 2 group registers first; a service desk script with a second approver | 06.09, 06.10, 06.11, 13.07, 09.04 |
| "Anyone" sharing links limited to view-only with a 7-day expiry, after the Chief Customer Officer's team warns customers who receive them | 06.18 |
| Class A data under Microsoft 365 Backup with a first timed restore; continuity kit; Fabrikam's own payroll fallback | 14.04, 14.05, 14.06 |
| The incident response retainer or pre-agreed emergency terms, with the CFO's approval; the MDR evaluation: Microsoft's Defender Experts MDR Plan 1 against at least two independent providers | 08.06 |
| Business impact sessions with each function leader, and POL-09 drafted | 14.07 |
| Finance, payroll, and People sessions with a payroll diversion desk check; named year-end coverage, with the incident response firm's contact; R-01 and R-03 reviewed with their owners; freeze calendar, with Remote Help confirmed; fourth-quarter SOC 2 controls finished | 09.03, 08.05, 08.07, 11.04, 13.09, 10.09 |
| Service levels and portal; investigation logging confirmed | 13.06, 06.19 |

### Phase 2, the rest of December

| What happens | Actions |
|---|---|
| First guest clean-up round; first manual access reviews; service desk forms for joiners and leavers replace email | 07.07, 07.06, 07.05 |
| Office network fixes | 06.20 |
| Day-one readiness; lifecycle clauses for POL-04 | 13.11, 13.10 |
| Current CSF Profile at Category level; POL-01 to POL-15 drafted by the readiness consultant for the Director's review; full reviews of vendors holding customer workforce data; bridge letters; an automated decisionmaking position before 2027-01-01; discovery closed | 10.07, 10.08, 10.10, 10.11, 10.12, 05.12 |
| Risk register v1 with owners; exception process; first monthly scorecard | 11.03, 11.05, 12.03, 12.04 |
| AI questions in intake; surviving tools chosen, with no cutovers; two-owner report for teams and sites | 15.04, 16.04, 15.06, 15.08 |
| The Report button; interim AI notice approved and issued | 09.05, 16.03 |
| FastTrack for Microsoft 365 requested, so its help is in place for February | 06.23 |

### Phase 3

| What happens | Actions |
|---|---|
| Every user confirmed on another method before 2027-02-01; the service desk staffed, with surge cover booked from Friday 2027-01-29 once M3 approves it; the January module | 06.21, 13.12, 09.06 |
| New hires on a Temporary Access Pass and a passkey, each account disabled and each pass unreleased until the identity check is recorded (R-15) | 07.10 |
| In the first half of January, before the HR integration credential is issued: app consent limited, existing grants reviewed, orphaned application access revoked, and integration credentials vaulted; then guests bounded, and inherited file servers scanned with their "Anyone" links removed | 06.12, 15.05, 06.13, 15.07 |
| Endpoint baseline, with Quick Assist removed and a Microsoft Store restriction against reinstalling it, and the elevation service for everyone except finance and payroll, who join in February, weeks 2 to 3 (06.24) | 06.17, 13.08 |
| HR feed built and tested; data loss prevention for payroll identifiers in simulation; class B backup; the IT service management tool behind single sign-on, automation guardrails set, domain paths approved, and consolidation rehearsed | 07.09, 06.22, 14.08, 15.10 to 15.13 |
| SOC 2 coordination covered by the Director with the readiness consultant, kept at least through M4, management responses to inherited exceptions drafted, and control owners confirming next-period design; platforms evaluated for the M3 budget; contract templates approved; evidence refreshed for the current Profile; security champions recruited | 10.16, 10.15, 10.17, 05.13, 09.08 |
| The build partner's scope for February to April and the surge support terms agreed in January, and surge staff trained on the caller verification script on 28 and 29 January, after the M3 approval, so help is in place for the first week of February | 06.23, 13.14 |

### The M3 package

| The executive team approves | Actions |
|---|---|
| The 12-month plan, on verified facts and a validated threat profile | 01.02, 17.02 |
| The budget ([04](04-operating-model-team-and-budget.md)): Microsoft Defender Suite and Microsoft Entra ID Governance, or the fallback; the MDR provider; backup and an isolated copy; the compliance platform; single sign-on and consolidation upgrades; AI discovery and a Microsoft Copilot pilot; surge support and hiring triggers | 06.23, 07.08, 08.08, 14.09, 10.15, 15.09, 16.06, 13.14 |
| POL-01 to POL-15 with the AI section, the AI security standard under POL-01, and the lifecycle and training clauses, cleared beforehand by policy co-owners and the IT and Security Steering Group; the incident response plan; the risk appetite | 10.14, 16.05, 16.16, 09.07, 07.08, 13.13, 08.08, 14.09, 11.06 |
| Both CSF Profiles: the current one at Category level and the target | 10.13 |
| KPI targets, and treatment plans for every Critical and High risk, R-08 included, at the first Quarterly Risk Review | 12.05, 11.07, 12.06 |
| Settled alongside: General Counsel's approval of the holding statements and notification path | 08.08 |

### Day 120 readout

| Under way in February | Actions |
|---|---|
| In order: wave 2 MFA enforcement and finance and payroll's identity changes in week 1, their endpoint baseline in weeks 2 to 3, then device rings | 06.24 |
| Microsoft Defender Suite controls, such as just-in-time administration, by the Systems Engineer (Identity and Endpoint) with partner help | 06.25 |
| MDR onboarding and the ransomware playbook draft; alerts on backup administration changes to the on-call, and to the MDR provider if it triages custom detections | 08.10, 14.11 |
| DMARC enforcement, domain by domain, and lookalike domain monitoring | 06.27, 15.19 |
| The HR feed and access catalog | 07.11, 07.12 |
| Service desk surge cover and self-service | 13.15, 13.16 |
| Finance single sign-on, after finance and payroll's identity and endpoint changes, and the first consolidation waves | 15.14, 15.16 |
| Class C backup | 14.10 |
| Simulation setup, the executive briefing, and the first tabletop, scoped by the Director | 09.09, 09.10, 08.09, 17.03 |
| Next-period SOC 2 planning and the compliance platform | 10.18, 10.20 |
| Monthly risk status at the IT and Security Steering Group, with R-01 and R-06 re-rated for the readout | 11.08 |
| The readout itself, on Friday 2027-02-26 | 12.07 |

## Sources

- Plan documents relied on (internal cross-references, not external sources): [01. Scenario and assumptions](01-scenario-and-assumptions.md); [03. Twelve-month roadmap](03-twelve-month-roadmap.md); [04. Operating model, team, and budget](04-operating-model-team-and-budget.md); [05. Environment discovery](05-environment-discovery.md) and the [stakeholder conversation guide](templates/stakeholder-conversation-guide.md); [06. Microsoft 365 security baseline](06-microsoft-365-security-baseline.md); [07. Identity lifecycle: joiners, movers, and leavers](07-identity-lifecycle-joiners-movers-leavers.md); [08. Detection and incident response](08-detection-and-incident-response.md); [09. Security awareness and training](09-security-awareness-and-training.md); [10. Governance and compliance program](10-governance-and-compliance-program.md); [11. Risk management](11-risk-management.md); [12. Metrics and executive reporting](12-metrics-and-executive-reporting.md) and the [KPI catalog](../data/kpi-catalog.csv); [13. IT service management](13-it-service-management.md); [14. Business continuity and backup](14-business-continuity-and-backup.md); [15. Enterprise systems and SaaS](15-enterprise-systems-and-saas.md); [16. AI security and adoption guardrails](16-ai-adoption-guardrails.md); [17. Threat profile](17-threat-profile.md); [ADR-001](adr/ADR-001-microsoft-365-security-licensing.md), [ADR-004](adr/ADR-004-phishing-resistant-authentication-rollout.md), and [ADR-007](adr/ADR-007-compliance-automation-platform.md); and the [CSF 2.0 and SOC 2 crosswalk](crosswalk/csf2-soc2-crosswalk.md).
- Passkeys by default and retirement of Microsoft-provided SMS and voice authentication. Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sms-voice-retirement . Checked 2026-10-13. Primary.
- Microsoft Entra data retention. Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/monitoring-health/reference-reports-data-retention . Checked 2026-10-13. Primary.
- Enterprise data protection in Microsoft Copilot and Microsoft Copilot Chat (product name change). Microsoft Learn. https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection . Checked 2026-10-13. Primary.
- Product Lifecycle FAQ, Extended Security Updates. Microsoft Learn. https://learn.microsoft.com/en-us/lifecycle/faq/extended-security-updates . Checked 2026-10-13. Primary.
- Deprecation of Basic authentication in Exchange Online. Microsoft Learn. https://learn.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/deprecation-of-basic-authentication-exchange-online . Checked 2026-10-13. Primary.
- MC786329, Exchange Online to retire Basic Auth for Client Submission (SMTP AUTH). mc.merill.net, a community mirror of Microsoft 365 Message Center posts. https://mc.merill.net/message/MC786329 . Checked 2026-10-13. Secondary.
