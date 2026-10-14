# 12. Metrics and executive reporting

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

## Purpose and scope

This document sets how the information technology (IT) and security program at Fabrikam (fictional) is measured and how results reach the executive team: 24 key performance indicators (KPIs), a one-page monthly scorecard, the Quarterly Risk Review, the Day 120 readout (end of February 2027), and the annual program review. Together with [`data/kpi-catalog.csv`](../data/kpi-catalog.csv), which holds every definition, formula, data source, and cadence, it is the single authority for the plan's KPIs; Engineering reports product platform figures under the shared RACI (who is responsible, accountable, consulted, and informed) in document [04](04-operating-model-team-and-budget.md). Every target is a proposal that the Director of IT and Security brings to the executive team at M3 (day 90).

## Principles

- **Measure what drives decisions.** A KPI stays only if it shows whether a control works or whether a top risk (R-01 to R-15, document [11](11-risk-management.md)) is moving. The test comes from the National Institute of Standards and Technology (NIST): keep a data point if it "directly illustrates the performance of a valid control or tracks the presence of a material risk to the organization's objective" (Special Publication (SP) 800-55, Volume 1, Sec. 2.4).
- **Few, stable measures.** 24 in the catalog and 11 on the monthly page. Definitions and targets change only at a Quarterly Risk Review or the annual review, with a recorded reason.
- **Baselines first.** Every KPI gets a first value, or "no data yet" with a date, by M1 (day 30; document [05](05-environment-discovery.md)); targets with monthly interim steps follow for approval at M3.
- **Ratings are not measures.** SP 800-55 Volume 1 states that "qualitative and semi-quantitative assessments are not considered measurements" (Sec. 2.2). Document 11's risk ratings are assessments; the KPIs show whether the treatments behind them work.

## Reporting cadence and audiences

Every report below goes to the executive team (document [04](04-operating-model-team-and-budget.md)) except the board summary, which goes to the chief executive officer (CEO). SOC 2 is the attestation report on Fabrikam's controls, under American Institute of Certified Public Accountants (AICPA) criteria, that customers ask for.

| Report | When (proposal) | Content |
|---|---|---|
| Monthly executive scorecard | Monthly from December 2026 at the IT and Security Steering Group, with a pre-read three business days ahead | One page: 11 KPIs in three sections, movement of the top risks, decisions needed ([template](templates/monthly-executive-scorecard.md)) |
| Quarterly Risk Review | Late January, April, and July 2027, with each named risk owner; in October 2027 it is held as part of the annual program review (M7) | Risk register, all 24 KPIs, the supporting checks below, workstream status against milestones, budget status in words (spend against the approved budget by category, offsets realized from ended duplicate contracts, and purchased capabilities not yet in use: on plan, under, or over, with the reason), decisions ([illustrative sample](templates/quarterly-risk-review-sample.md)) |
| Day 120 readout (D120) | End of February 2027: Friday 2027-02-26, the last business day of the month | KPIs against their Phase 1 baselines, early Phase 4 actions under way, and what is at risk |
| Annual program review (M7) | Late October 2027 | KPIs against targets, re-baselined risks, catalog changes, next-year plan |
| Board summary | After a Quarterly Risk Review, if the CEO asks | Two pages at most: top risks, KPI-01, KPI-03, KPI-08, KPI-16, and KPI-19, SOC 2 status, serious incidents. The CEO decides what goes to the investor board |

The Director prepares each report, with the governance, risk, and compliance (GRC) Analyst for the Quarterly Risk Review once that role starts (March 2027 in the base case). Milestones M1 to M7 and D120 are defined in document [03](03-twelve-month-roadmap.md).

## Scorecard design

One page, three sections, the same KPIs every month. Each row shows the current value, the last three months with a one-word trend (better, worse, or steady), the headline target from Appendix: KPI catalog, a status, and a one-line note. There is no overall score.

| Section | KPIs | The questions they answer |
|---|---|---|
| Risk and compliance | KPI-01, KPI-03, KPI-04 | Are the top risks owned and treated? Is SOC 2 healthy? Are audit findings being fixed? |
| Protection | KPI-08, KPI-09, KPI-12, KPI-16, KPI-19 | Could a fake sign-in page still capture a working sign-in? Who holds standing admin power? Do leavers lose access on time? How fast are serious incidents contained? Can Fabrikam restore what it backs up? |
| IT service | KPI-20, KPI-21, KPI-22 | Do employees get help on time? Are they satisfied? Are new hires ready on day one? |

Three blocks follow: **So what** (up to three sentences from the Director), **Top risks: movement** (only risks whose rating, owner, or treatment changed, or flagged by a KPI or supporting check), and **Decisions needed** (options, a recommendation, the deciding executive, and a date). A watch line names any other KPI that is Off track.

**Supporting checks.** Three checks are not KPIs and have no KPI IDs. They are reported in the risk movement rows and at the Quarterly Risk Review, not as scorecard rows: bank-detail and direct-deposit changes with a recorded call-back, from Finance's and People's monthly sample, which those teams add to the monthly pull set up in 12.04 (R-01); sending domains at p=reject, meaning Fabrikam asks receiving mail systems to reject mail that fails its email authentication (R-01, R-02); and open links to sensitive content, from query [q08](../queries/q08-anonymous-sharing-links.kql) (R-07).

Each status (On track, At risk, Off track, Baseline only, or No data yet) is written in words, not color alone, by rules approved at M3 (Appendix: Scorecard status rules). Small monthly counts (leavers, incidents, restore tests, survey responses) use three-month rolling values and show the count (n).

## KPI catalog

The 24 KPIs follow the NIST Cybersecurity Framework (CSF) 2.0 Functions (KPI-01 to KPI-05 Govern, KPI-06 and KPI-07 Identify, KPI-08 to KPI-15 Protect, KPI-16 Detect and Respond, KPI-17 and KPI-18 Respond, KPI-19 Recover) plus IT service (KPI-20 to KPI-24), and every one goes to each Quarterly Risk Review. Appendix: KPI catalog lists owners and headline targets, which the scorecard template uses word for word; the catalog file holds full definitions, formulas, sources, cadences, and target wording.

## Producing trustworthy numbers

Each month, owners pull their sources (business days 1 to 3), the GRC Analyst computes the values and re-checks large swings (day 4), owners confirm (day 5), and the Director interprets (day 6); until the GRC Analyst starts (March 2027 in the base case, or February if the role is pre-approved at M2), the Director compiles with the IT Operations Manager. Appendix: Data quality and known limits sets the checks on the numbers and the limits of the sources.

## Phase plan

| Phase | Action ID | Action | Outcome | KPI | Owner role | Workstream |
|---|---|---|---|---|---|---|
| Phase 1 | 12.01 | Agree each KPI's definition, data source, and owner; record a first value or "no data yet" for every KPI (with 05.10) | KPI baselines at M1 | KPI-01 to KPI-24 | Director of IT and Security | WS-5 |
| Phase 1 | 12.02 | Agree the reporting calendar and any board summary with the chief technology officer (CTO) and the CEO | Dates set before the first scorecard | KPI-01 | Director of IT and Security | WS-5 |
| Phase 2 | 12.03 | Issue the first monthly scorecard in December 2026, targets marked "to be proposed at M3" | Starting point seen before the year-end freeze | KPI-08, KPI-09, KPI-12 | Director of IT and Security | WS-5 |
| Phase 2 | 12.04 | Set up monthly production: pull checklists for the KPIs and the supporting checks, versioned formulas, restricted inputs, and swing checks | Numbers that can be reproduced | KPI-01 to KPI-24 | Director of IT and Security | WS-5 |
| Phase 3 | 12.05 | Propose targets, due dates, interim targets, and tolerances for every KPI, for executive team approval at M3 | Approved targets and status rules (M3) | KPI-01 to KPI-24 | Director of IT and Security | WS-5 |
| Phase 3 | 12.06 | Hold the first Quarterly Risk Review with the M3 approval: every top risk's owner and treatment plan, and the full catalog | Every top risk owned, with an approved treatment plan | KPI-01 | Director of IT and Security | WS-5 |
| Phase 4 | 12.07 | Present the Day 120 readout (end of February 2027) on Friday 2027-02-26 | First measured results (D120) | KPI-08, KPI-09, KPI-12, KPI-20 | Director of IT and Security | WS-5 |
| Phase 4 | 12.08 | Hand collection to the GRC Analyst once that role starts; move pulls to repeatable reports and the queries in `queries/` as Phase 4 licenses arrive, marking each changed source | Lower effort; source changes visible | KPI-09, KPI-11, KPI-15, KPI-16 | GRC Analyst | WS-5 |
| Phase 4 | 12.09 | April: run the first quarterly re-performance: recompute two KPIs and trace leavers and new hires end to end | Errors fixed before the review | KPI-12, KPI-22 | GRC Analyst | WS-5 |
| Phase 4 | 12.10 | Hold the month-6 Quarterly Risk Review in late April 2027 ([illustrative sample](templates/quarterly-risk-review-sample.md)) | Risks re-rated; decisions recorded | KPI-01, KPI-03 | Director of IT and Security | WS-5 |
| Phase 5 | 12.11 | Hold the month-9 Quarterly Risk Review in late July 2027 with the M5 and M6 checks | M5 and M6 confirmed against their KPIs | KPI-03, KPI-08, KPI-12, KPI-22 | Director of IT and Security | WS-5 |
| Phase 5 | 12.12 | Run the first annual program review (M7): KPIs against targets, re-baselined risks, catalog changes, year-two targets; draft the board summary for the CEO | M7 met; year-two targets proposed | KPI-01 to KPI-24 | Director of IT and Security | WS-5 |

## Resourcing and dependencies

- **Roles.** The Director of IT and Security owns executive reporting. The IT Operations Manager compiles with the Director until the GRC Analyst starts (March 2027 in the base case) and takes over; until the Security Engineer and the GRC Analyst start (document 04), the Director holds their KPIs. The Engineering Manager and the Site Reliability Engineering (SRE) lead supply the product lines of KPI-11 and KPI-19, the vice president (VP) of People's team human resources (HR) data, and the chief financial officer's (CFO's) team vendor data and the budget status.
- **Partners.** The managed detection and response (MDR) provider (KPI-16), the SOC 2 audit firm (KPI-03 and KPI-04), and the IT hardware partner (the KPI-06 denominator).
- **Licenses.** Microsoft 365 E3 in Phases 1 to 3; from Phase 4, Microsoft Defender Suite and Microsoft Entra ID Governance (architecture decision record [ADR-001](adr/ADR-001-microsoft-365-security-licensing.md); detail in Appendix: Data quality and known limits). Without Defender Suite, KPI-11, KPI-15, and KPI-16 stay on interim sources and their targets are proposed again.
- **Cost drivers.** No new reporting tool: the work runs on the existing IT service management tool, the HR system of record, the training platform, and the compliance automation platform ([ADR-007](adr/ADR-007-compliance-automation-platform.md), category only). The main cost is people time, about one working day a month once routine.
- **Depends on.** Documents 03 to 11, 13 (service levels, published in Phase 2 under 13.06), 14, and 15; [ADR-003](adr/ADR-003-managed-detection-and-response.md) and [ADR-006](adr/ADR-006-microsoft-365-backup.md); and the [KPI catalog](../data/kpi-catalog.csv) with the queries it names.

## Risks and open questions

- **Measurement effort (R-14).** NIST says data collection should be light enough "to ensure that available resources are primarily used to correct problems rather than collect data" (SP 800-55 Vol. 1, Sec. 3.1.3). If production takes more than about a day a month once routine, the catalog shrinks.
- **Early values are proxies.** M3 targets rest on one or two months of baselines and some interim sources, so the month-6 review may adjust them, with recorded reasons; a slipped M3 licensing decision delays the series that depend on it.
- **No blame.** No individual phishing results reach executive reports; NIST SP 800-50 Rev. 1 says simulation activities "should not be punitive, nor should any employee be called out for their response."
- **Engineering data.** If the product lines of KPI-11 and KPI-19 are missing, the scorecard says so rather than presenting corporate figures as the whole picture.
- **Open question for the SOC 2 audit firm.** Whether it will use any KPI data in its testing; the default assumption is that it will not.

## Framework mapping

By identifier only, consistent with the [crosswalk](crosswalk/csf2-soc2-crosswalk.md). SOC 2 identifiers are from the AICPA's 2017 Trust Services Criteria (TSC).

| Theme | NIST CSF 2.0 | SOC 2 (2017 TSC) |
|---|---|---|
| Executive oversight of performance and strategy: monthly scorecard, Quarterly Risk Review, annual program review | GV.OV-01, GV.OV-02, GV.OV-03 | CC4.1, CC4.2 |
| Accountability, reporting lines, and communication of cybersecurity risk to executives and, through the CEO, the board | GV.RR-01, GV.RR-02, GV.RM-05 | CC1.2, CC1.3, CC2.2 |
| Defined, checked information for decisions: catalog definitions, sources, and data checks | GV.OV-03 | CC2.1 |
| Risk responses tracked and reported (KPI-01, movement of the top risks) | ID.RA-06 | CC3.2 |
| Improvement from evaluations, exercises, and operations (KPI-18, re-performance, annual review) | ID.IM-01, ID.IM-02, ID.IM-03 | CC4.2 |

## Appendix: KPI catalog

Every KPI goes to each Quarterly Risk Review; the last column shows where else it appears. Headline targets are proposals; for the 11 scorecard KPIs they are the short forms the scorecard template uses word for word, and the catalog file holds the full wording. M4 is month 5 (March 2027), M5 and M6 are month 9 (July 2027), and M7 is month 12 (October 2027).

Terms: **MFA** is multifactor authentication; a phishing-resistant method, such as a passkey, cannot be captured and replayed by a fake website. A **standing privileged assignment** is a permanent assignment to a Microsoft Entra role that Microsoft labels privileged (label in preview, as of 2026-10-13). **Intune** is Microsoft's device management service, **SaaS** is software as a service, and **SCIM** is the standard that creates and removes SaaS accounts automatically. **MDR** is the managed detection and response provider ([ADR-003](adr/ADR-003-managed-detection-and-response.md), an architecture decision record). **SEV-1 and SEV-2** are the most serious incident levels (document [08](08-detection-and-incident-response.md)), **CSAT** is a customer satisfaction score, and a **recovery time objective** is the longest acceptable restore time (document [14](14-business-continuity-and-backup.md)).

| KPI | Owner | Headline target (proposal) | Also reported in |
|---|---|---|---|
| KPI-01 Top risks with an owner and an approved treatment plan (%) | Director of IT and Security | 100 percent by M3 and every month after | Scorecard; board summary |
| KPI-02 Policies reviewed within their cycle (%) | GRC Analyst | 100 percent from M3; none overdue by more than 30 days | Steering Group when a policy is overdue |
| KPI-03 SOC 2 controls operating without exceptions (%) | GRC Analyst | No new exceptions caused by the Director's changes (period closing at M4); management testing 95 percent from Phase 4, 98 by M7 | Scorecard; board summary |
| KPI-04 Open audit exceptions and their median age | GRC Analyst | Owner and committed date within 10 business days; median age under 60 days from Phase 4 | Scorecard |
| KPI-05 Third parties handling customer or employee data with a current review (%) | GRC Analyst | 100 percent of third parties with customer data access by month 9 (July 2027); 90 percent of all in-scope third parties by M7 | None |
| KPI-06 Devices managed in Intune out of devices known (%) | IT Operations Manager | 90 percent by the end of Phase 4; 98 by M7 | None |
| KPI-07 SaaS applications behind single sign-on (%) | Systems Engineer (Identity and Endpoint) | By M7, 90 percent of those holding customer or employee data and 70 percent of all | None |
| KPI-08 Phishing-resistant MFA coverage, admins and all users (%) | Systems Engineer (Identity and Endpoint) | Admins 100 percent by the end of Phase 2; all employees 90 percent by M6, 95 by M7; nobody on SMS or voice alone after 2027-02-01 | Scorecard; board summary |
| KPI-09 Standing privileged role assignments (count) | Director of IT and Security | Fewer than five Global Administrators, emergency access accounts included (end of Phase 1); fewer than 10 standing assignments (end of Phase 2); only the 2 emergency access accounts (end of Phase 4) | Scorecard |
| KPI-10 Compliant devices (%) | Systems Engineer (Identity and Endpoint) | 90 percent by the end of Phase 4; 97 by M7 | None |
| KPI-11 Critical and high vulnerabilities fixed within target (%) | Security Engineer | 90 percent within the patch policy's deadlines (14 days for critical, 30 for high) by M6; 95 by M7 | None |
| KPI-12 Leaver access removed within target (%) | IT Operations Manager | At least 98 percent from M6; every urgent leaver within one hour | Scorecard |
| KPI-13 Access reviews completed on time (%) | GRC Analyst | 95 percent from the second automated review cycle | None |
| KPI-14 Security training completion (%) | GRC Analyst | 95 percent by due date; new hires in their first week | None |
| KPI-15 Phishing simulation report rate and click rate | Security Engineer | By M7, against the first campaign at comparable difficulty: report rate up by at least half, click rate down by at least half | None |
| KPI-16 Mean time to acknowledge and to contain high-severity incidents | Security Engineer | From MDR go-live: acknowledge within 15 minutes, contain within 4 hours | Scorecard; board summary |
| KPI-17 Security incidents by severity and cause (count) | Security Engineer | No count target; every incident classified within 5 business days of closure | SEV-1 and SEV-2 counts in the scorecard note |
| KPI-18 Exercise and post-incident actions closed on time (%) | GRC Analyst | 90 percent from Phase 4 | Steering Group pre-read |
| KPI-19 Restore tests meeting target recovery times (%) | IT Operations Manager | Every scheduled test run; 90 percent meet their recovery time objective from Phase 4 | Scorecard; board summary |
| KPI-20 Service desk tickets resolved within target (%) | IT Operations Manager | 85 percent from Phase 3; 90 by M7 | Scorecard |
| KPI-21 Employee satisfaction with IT support (CSAT) | IT Operations Manager | 90 percent by M7 | Scorecard |
| KPI-22 New hires fully productive on day one (%) | IT Operations Manager | 90 percent by M6; 95 by M7 | Scorecard |
| KPI-23 Access requests fulfilled automatically (%) | Systems Engineer (Identity and Endpoint) | 60 percent by M6; 75 by M7 | None |
| KPI-24 Corporate IT changes completed without incident or rollback (%) | IT Operations Manager | 95 percent from Phase 3; 97 by M7 | None |

## Appendix: Scorecard status rules

Proposal, approved with the targets at M3. Statuses are written in words, not color alone; a Director override is explained in the note.

| Status | Rule |
|---|---|
| On track | At or better than the target, or than this month's interim target |
| At risk | Below the interim target by no more than the KPI's tolerance (default: 5 percentage points for percentages, 20 percent for times and counts), or worse two months running |
| Off track | Below the interim target by more than the tolerance, or a milestone (M4 to M7) will be missed without a decision |
| Baseline only | No approved target yet (before M3), or the first month on a new data source |
| No data yet | Not measurable yet; the note gives the date of the first value |

Where more than one rule applies, the less favorable status applies.

## Appendix: Data quality and known limits

**Checks on the numbers.**

- **One versioned definition per KPI,** in the catalog. KPI-08, for example, comes from Microsoft Entra's Authentication methods activity report, which Microsoft says needs Entra ID P1 or P2, and from Conditional Access state. Query [q01](../queries/q01-sign-ins-without-strong-auth.kql), which counts successful sign-ins that did not require MFA, is only a cross-check.
- **Reconciled denominators.** Device, application, vendor, and people counts are checked monthly against the document 05 inventories, so no KPI improves because its denominator shrank.
- **Separation where practical.** The GRC Analyst collects and the owner explains; the Director reviews the GRC Analyst's own KPIs. Each quarter, two KPIs are recomputed from raw data.
- **Restricted inputs.** Inputs hold names and incident detail, so they stay restricted for 13 months; the scorecard shows aggregates only.

**Licenses behind the sources.** Phases 1 to 3: Microsoft 365 E3, including Microsoft Entra ID P1 reports and logs, Intune, Defender for Endpoint Plan 1, Defender for Office 365 Plan 1 (in E3 since the July 2026 update), and Microsoft Purview Audit (Standard). From Phase 4 ([ADR-001](adr/ADR-001-microsoft-365-security-licensing.md)): Microsoft Defender Suite, which includes Microsoft Entra ID P2, Defender for Endpoint Plan 2, Defender for Office 365 Plan 2, and Defender for Cloud Apps, and Microsoft Entra ID Governance.

**Known limits.**

- **Log windows.** Microsoft Entra keeps sign-in and audit logs for 30 days on Entra ID P1, and Microsoft Purview Audit (Standard) keeps 180 days. Entra logs are archived from Phase 1 (document 08); older history for KPI-12 and KPI-16 cannot be rebuilt.
- **License-dependent sources.** KPI-09, KPI-11, KPI-13, KPI-15, KPI-16, and KPI-22 carry labeled interim values until the Phase 4 licenses arrive (ADR-001).
- **Reports that overstate.** Microsoft's "passwordless capable" group includes phone sign-in with Microsoft Authenticator, which the built-in phishing-resistant authentication strength excludes, so KPI-08 counts methods one by one. Intune marks devices with no compliance policy as Compliant by default until document 06 changes the setting (KPI-10).
- **Inventories and behavior.** Phase 1 inventories are incomplete (KPI-05 to KPI-07), and more incident reports can mean better reporting rather than more attacks (KPI-15, KPI-17).

## Sources

These sources also cover the [KPI catalog file](../data/kpi-catalog.csv).

- Measurement Guide for Information Security: Volume 1, Identifying and Selecting Measures (NIST SP 800-55v1, December 2024), publication record and PDF; with Volume 2, it supersedes SP 800-55 Rev. 1 (2008). NIST. https://csrc.nist.gov/pubs/sp/800/55/v1/final and https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-55v1.pdf . Checked 2026-10-13 (PDF read in full). Primary.
- Measurement Guide for Information Security: Volume 2, Developing an Information Security Measurement Program (NIST SP 800-55v2, December 2024), publication record. NIST. https://csrc.nist.gov/pubs/sp/800/55/v2/final . Checked 2026-10-13 (record only; content not summarized here). Primary.
- The NIST Cybersecurity Framework (CSF) 2.0 (CSWP 29). NIST. https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf . Checked 2026-10-13 (PDF read in full). Primary.
- Building a Cybersecurity and Privacy Learning Program (NIST SP 800-50 Rev. 1), publication record and PDF. NIST. https://csrc.nist.gov/pubs/sp/800/50/r1/final and https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-50r1.pdf . Checked 2026-10-13. Primary.
- 2017 Trust Services Criteria (With Revised Points of Focus, 2022), download page. AICPA & CIMA. https://www.aicpa-cima.com/resources/download/2017-trust-services-criteria-with-revised-points-of-focus-2022 . Checked 2026-10-13. Primary.
- Authentication Methods Activity (ms.date 2025-10-22). Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-methods-activity . Checked 2026-10-13. Primary.
- Overview of Conditional Access Authentication Strengths (ms.date 2025-03-04). Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-strengths . Checked 2026-10-13. Primary.
- Passkeys by default and retirement of Microsoft-provided SMS and voice authentication. Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sms-voice-retirement . Checked 2026-10-13. Primary.
- Privileged roles and permissions in Microsoft Entra ID (preview). Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/privileged-roles-permissions . Checked 2026-10-13. Primary.
- Best practices for Microsoft Entra roles (ms.date 2026-06-01), best practices 5 and 6. Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/best-practices . Checked 2026-10-13. Primary.
- Microsoft Entra data retention (ms.date 2026-01-06). Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/monitoring-health/reference-reports-data-retention . Checked 2026-10-13. Primary.
- Microsoft Entra ID Governance licensing fundamentals. Microsoft Learn. https://learn.microsoft.com/en-us/entra/id-governance/licensing-fundamentals . Checked 2026-10-13. Primary.
- Learn about auditing solutions in Microsoft Purview (ms.date 2026-05-18). Microsoft Learn. https://learn.microsoft.com/en-us/purview/audit-solutions-overview . Checked 2026-10-13. Primary.
- Device compliance policies in Microsoft Intune (ms.date 2026-07-02). Microsoft Learn. https://learn.microsoft.com/en-us/intune/device-security/compliance/overview . Checked 2026-10-13. Primary.
- Microsoft Defender service description (its Defender for Office 365 Plan 1 rights list does not yet show the July 2026 E3 change; the two packaging pages below do). Microsoft Learn (Service Descriptions). https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-defender-service-description . Checked 2026-10-13. Primary.
- Security Suites (Microsoft Licensing guidance). Microsoft. https://www.microsoft.com/licensing/guidance/Security-Suites . Checked 2026-10-13. Primary.
- Get started using Attack simulation training. Microsoft Learn. https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-get-started . Checked 2026-10-13. Primary.
- Microsoft 365 Pricing and Packaging Updates (February 16, 2026), Microsoft 365 E3 additions, including Defender for Office Plan 1 and Intune Plan 2. Microsoft (Licensing Resources). https://www.microsoft.com/en-us/licensing/news/2026-m365-packaging-pricing-updates . Checked 2026-10-13. Primary.
- Microsoft 365 Packaging and Pricing Updates Public FAQ (March 24, 2026), rollout complete by August 1, 2026. Microsoft (Licensing Resources). https://www.microsoft.com/en-us/licensing/news/2026-m365-packaging-pricing-updates-faq . Checked 2026-10-13. Primary.
- Microsoft Intune Licensing Plans and Options (ms.date 2026-05-13). Microsoft Learn. https://learn.microsoft.com/en-us/intune/fundamentals/licensing . Checked 2026-10-13. Primary.
- Microsoft Entra service description (ms.date 2026-03-24), plan availability. Microsoft Learn. https://learn.microsoft.com/en-us/office365/servicedescriptions/azure-active-directory . Checked 2026-10-13. Primary.
- Microsoft Defender XDR prerequisites (ms.date 2025-04-03), licensing requirements. Microsoft Learn. https://learn.microsoft.com/en-us/defender-xdr/prerequisites . Checked 2026-10-13. Primary.
- Guide to Enterprise Patch Management Planning: Preventive Maintenance for Technology (SP 800-40 Rev. 4, April 2022). NIST. https://csrc.nist.gov/pubs/sp/800/40/r4/final . Checked 2026-10-13. Primary.
