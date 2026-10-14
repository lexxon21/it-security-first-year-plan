# Quarterly Risk Review: illustrative sample for month 6 (April 2027)

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

**Illustrative sample. Fabrikam is fictional, and every number, rating, status, event date, and finding about Fabrikam in this document is invented to show the format of a Quarterly Risk Review at month 6 of the plan. None of it is a measured result.** The two Microsoft dates mentioned (2027-02-01 and 2027-07-01, the retirement of Microsoft-provided SMS and voice MFA) are real and sourced. Definitions, targets, and status rules are in document [12](../12-metrics-and-executive-reporting.md) and the [KPI catalog](../../data/kpi-catalog.csv); the monthly page is the [scorecard template](monthly-executive-scorecard.md).

**Table A (illustrative; all values fictional). Meeting details.**

| Field | Value |
|---|---|
| Forum | Quarterly Risk Review: the executive team reviews the risk register and the key performance indicators (KPIs) |
| Meeting | Thursday, 2027-04-29, 75 minutes |
| Quarter reviewed | Phase 4, Build: 2027-02-01 to the data cut-off on Friday, 2027-04-23. State measures are as of the cut-off; event measures cover the quarter to date |
| Chair | CEO (proposal; forum roles are in document [04](../04-operating-model-team-and-budget.md)) |
| Presenter | Director of IT and Security |
| Attendees | CEO, CFO, CTO, Chief Product Officer, Chief Customer Officer, VP of People, General Counsel; the GRC Analyst keeps the minutes |
| Pre-read sent | Monday, 2027-04-26 |

## At a glance (illustrative)

- **Phase 4 delivered its main protections.** Managed detection and response (MDR) monitoring at all hours has run since 2027-04-19, standing admin access is down to the two emergency access accounts, and phishing-resistant sign-in is enforced for the highest-risk business roles. M4 was met by management's tracking; the SOC 2 audit firm's report is expected in June.
- **Risk moved mostly down.** Both Critical risks fell (R-02 to High, R-06 to Medium), three High risks fell to Medium, and one rose from Medium to High (R-12).
- **Three items need attention:** one of three restore tests missed its recovery time (KPI-19), leavers entered late in the HR system (KPI-12), and third-party reviews behind plan (KPI-05).
- **KPIs:** of 24, 17 are on track, 4 at risk, 1 off track, 1 on its first month of a new source, and 1 not rated because it has no count target.
- **Budget, in words:** spend is on plan in every category; offsets from duplicate tools come later, as those contracts end (WS-7); every capability bought at M3 is switched on.
- **Three decisions are requested** (section 6); the route for the acquired product line (decision 1) is previewed now and taken at M5.

## 1. Agenda

**Table 1 (illustrative; all values fictional). Agenda.**

| # | Item | Time | Lead |
|---|---|---|---|
| 1 | Opening, and a preview of the three decisions | 5 minutes | CEO |
| 2 | Risk summary and movement of the top risks | 20 minutes | Director, with each risk owner |
| 3 | KPI summary: what is off track or at risk | 15 minutes | GRC Analyst |
| 4 | Program status by workstream against milestones | 15 minutes | Director |
| 5 | Decisions requested | 15 minutes | Each decision owner |
| 6 | Look-ahead to July 2027, and actions | 5 minutes | Director |

## 2. Risk summary

Residual ratings use the scale in document [11](../11-risk-management.md) and the [risk register](../../data/risk-register.csv). Ratings are assessments, not measures; the KPIs in section 4 show whether the treatments behind them work. Every top risk has a named executive owner and an approved treatment plan (KPI-01: 100 percent).

**Table 2 (illustrative; all values fictional). Top risks by residual rating.**

| Residual rating | January review (M3) | This review | What changed |
|---|---|---|---|
| Critical | 2 | 0 | Both fell: R-02 to High, R-06 to Medium |
| High | 11 | 10 | One arrived from Critical (R-02) and one from Medium (R-12); three fell to Medium (R-01, R-10, R-15) |
| Medium | 2 | 5 | Four arrived (R-01, R-06, R-10, R-15); one rose to High (R-12) |
| Total | 15 | 15 | No risks added or closed |

## 3. Movement of the top risks

**Table 3 (illustrative; all ratings and values fictional). Risks that moved or are flagged.**

| Risk | Owner | January (M3) | Now | Movement | Why | Next step |
|---|---|---|---|---|---|---|
| R-02 Takeover of a customer administrator account in the product, leading to unauthorized payroll or bank-detail changes (shared with Engineering) | Chief Product Officer | Critical | High | Down | Support caller verification and the interim escalation card in use, with the full playbook in Phase 5 (document [08](../08-detection-and-incident-response.md)); both older brand domains at a DMARC (Domain-based Message Authentication, Reporting, and Conformance) policy of reject and the main domain at quarantine, cutting spoofed mail to customers (supporting check: the sending brand domain at reject; the main domain still at quarantine) | The product sign-in and bank-change safeguards in the treatment plan approved at M3 stay on Engineering's roadmap; re-rated with the Engineering Manager in July |
| R-06 Excessive, stale, or standing privileged access | CTO | Critical | Medium | Down | Privileged Identity Management live since March; standing assignments down to the two emergency access accounts (KPI-09); every administrator on phishing-resistant sign-in since December (KPI-08) | Admin role reviews move from monthly to quarterly (document [07](../07-identity-lifecycle-joiners-movers-leavers.md)) |
| R-01 Payroll diversion or payment fraud against Fabrikam's own finance and HR through business email compromise | CFO | High | Medium | Down | Phishing-resistant sign-in enforced for the wave 2 group since February (KPI-08); strict mail protection for finance and payroll; every sampled bank-detail change had a recorded call-back (supporting check); executive tabletop held in late February | Close the two late tabletop actions by 2027-05-31; lookalike domains still depend on calling back to verify bank changes |
| R-10 Not enough logging or response capacity to investigate an incident in time to meet customer notification commitments | General Counsel | High | Medium | Down | Monitoring at all hours through the MDR provider; Microsoft Entra log archive running since Phase 1; contract clause inventory covers the standard terms and the largest customers | Fix the holding statement approval gap found in the April notification drill (owner: Chief Customer Officer) |
| R-15 A fraudulent remote hire passes onboarding and receives credentials | VP of People | High | Medium | Down | Identity verification before first credentials (document 07) applied to all 33 new hires this quarter, with no failed checks | Keep the check in the quarterly re-performance sample (document [12](../12-metrics-and-executive-reporting.md)) |
| R-12 Privacy non-compliance for location or employee data under state law, or a proposed product feature (such as voice verification) launched without privacy review | General Counsel | Medium | High | Up | General Counsel found that the state of one Fabrikam office requires an employee monitoring notice that POL-02's first sign-in acceptance does not yet include (document [10](../10-governance-and-compliance-program.md), section 6.3) | Decision 2 |
| R-03 Ransomware or destructive attack on corporate endpoints and Microsoft 365 data | CEO | High | High | Flagged | Endpoint detection and response with automatic attack disruption since March; MDR live since 2027-04-19 (KPI-16); but one of three restore tests missed its recovery time (KPI-19) | Fix and rerun the OneDrive bulk restore test in May (document [14](../14-business-continuity-and-backup.md)) |
| R-05 Former employees or contractors keep access after they leave | VP of People | High | High | Flagged | Lifecycle automation became the control of record in April, but two of 21 leavers this quarter were disabled late because their terminations reached the HR system after their last day (KPI-12) | Decision 3 |
| R-11 A SOC 2 exception, a qualified opinion, or the uncovered acquired product slows enterprise sales | CFO | High | High | Flagged | The review period closed at M4 with no new exceptions caused by the Director's changes, by management's tracking; the audit firm's report is due in June and may still carry the inherited exceptions forecast in November. The acquired product line's route goes to the executive team at M5 | Brief the CFO and the Sales leader on the forecast exceptions in May (document [10](../10-governance-and-compliance-program.md)); decision 1, taken at M5 |

## 4. KPI summary

Status follows the rules in document 12. "Baseline" is the Phase 1 value recorded at M1; "January" is the value at the January review.

**Table 4 (illustrative; all values fictional). Scorecard KPIs.**

| KPI | Baseline | January | Now | Target (proposal) | Status | Note |
|---|---|---|---|---|---|---|
| KPI-01 Top risks with an owner and an approved treatment plan (%) | 0 percent (no register yet) | 100 percent | 100 percent | 100 percent by M3 and every month after | On track | R-12's treatment plan revised and re-approved by its owner |
| KPI-03 SOC 2 controls operating without exceptions (%) | 96 percent (audit firm, prior report) | 96 percent (audit firm, prior report) | 97 percent (management testing, February to April) | No new exceptions caused by the Director's changes (period closing at M4); management testing 95 percent from Phase 4, 98 by M7 | On track | Audit firm results for the period that closed at M4 are due in June |
| KPI-04 Open audit exceptions and their median age | 2 open; median 201 days | 2 open; median 253 days | 3 open; median 41 days | Owner and committed date within 10 business days; median age under 60 days from Phase 4 | On track | One prior-report exception closed in March by the leaver workflow; the oldest (product change approval evidence, Engineering) is committed for June |
| KPI-08 Phishing-resistant MFA coverage, admins and all users (%) | Admins 0 percent; all employees 0 percent | Admins 100 percent; all employees 0 percent (registered: 64 percent) | Admins 100 percent; all employees 29 percent (registered: 83 percent) | Admins 100 percent by the end of Phase 2; all employees 90 percent by M6, 95 by M7; nobody on SMS or voice alone after 2027-02-01 | On track | Wave 2 group enforced in February; all-employee rings start in May; nobody has relied only on SMS or voice since 2027-02-01 |
| KPI-09 Standing privileged role assignments (count) | All admin assignments standing (no Privileged Identity Management) | Below 10, with fewer than five Global Administrators | 2 (the emergency access accounts only) | Fewer than five Global Administrators, emergency access accounts included (end of Phase 1); fewer than 10 standing assignments (end of Phase 2); only the 2 emergency access accounts (end of Phase 4) | On track | Privileged Identity Management live since March |
| KPI-12 Leaver access removed within target (%) | 64 percent (six-month lookback) | 83 percent | 90 percent (19 of 21); urgent leavers 3 of 3 within one hour | At least 98 percent from M6; every urgent leaver within one hour | At risk | Both misses were terminations entered in the HR system after the last day (decision 3) |
| KPI-16 Mean time to acknowledge and to contain high-severity incidents | Interim: about 9 hours to first human action (low confidence) | Interim, internal on-call: 47 minutes and 5 hours 10 minutes (n = 2) | 11 minutes and 2 hours 35 minutes (n = 3, all SEV-2) | From MDR go-live: acknowledge within 15 minutes, contain within 4 hours | On track | Two of the three fell in the MDR parallel run; small sample, each incident listed in the register |
| KPI-19 Restore tests meeting target recovery times (%) | No documented restore tests in the prior 12 months | 100 percent (1 of 1, the early December class A restore test) | 67 percent (2 of 3) | Every scheduled test run; 90 percent meet their recovery time objective from Phase 4 | Off track | The OneDrive bulk restore missed the recovery time objective of its recovery class; product disaster recovery test with the SRE lead in June |
| KPI-20 Service desk tickets resolved within target (%) | No service levels yet | 81 percent | 88 percent | 85 percent from Phase 3; 90 by M7 | On track | February dipped to 79 percent during the first acquired-device migration wave |
| KPI-21 Employee satisfaction with IT support (CSAT) | 74 percent (pulse survey, n = 61) | 79 percent (n = 118) | 86 percent (n = 286; response rate 21 percent) | 90 percent by M7 | On track | Comments cite faster access requests |
| KPI-22 New hires fully productive on day one (%) | Interim: 41 percent (six-month lookback) | Interim: 63 percent | 82 percent (27 of 33) | 90 percent by M6; 95 by M7 | On track | Four of the six misses were hires entered late in the HR system |

**Table 5 (illustrative; all values fictional). Other catalog KPIs.**

| KPI | Baseline | January | Now | Target (proposal) | Status | Note |
|---|---|---|---|---|---|---|
| KPI-02 Policies reviewed within their cycle (%) | 13 percent | 100 percent (policy set approved at M3) | 100 percent | 100 percent from M3; none overdue by more than 30 days | On track | POL-03 rewritten and approved for the April automation cutover (document 10); next due: POL-02's six-month rewrite in July |
| KPI-05 Third parties handling customer or employee data with a current review (%) | 31 percent | 48 percent | 71 percent of all in scope; 80 percent of those with customer data access | 100 percent of third parties with customer data access by month 9 (July 2027); 90 percent of all in-scope third parties by M7 | At risk | Two benefits carriers and one background screening provider have not sent current assurance reports |
| KPI-06 Devices managed in Intune out of devices known (%) | 78 percent | 84 percent | 91 percent | 90 percent by the end of Phase 4; 98 by M7 | On track | Second acquired-device wave in May |
| KPI-07 SaaS applications behind single sign-on (%) | 41 percent of all; 55 percent of those holding customer or employee data | 47 percent; 63 percent | 58 percent; 79 percent | By M7, 90 percent of those holding customer or employee data and 70 percent of all | On track | Order set in document [15](../15-enterprise-systems-and-saas.md) |
| KPI-10 Compliant devices (%) | 84 percent (overstated by the default setting) | 76 percent (setting corrected in December) | 87 percent | 90 percent by the end of Phase 4; 97 by M7 | At risk | Remaining corporate Macs enroll in May (document [06](../06-microsoft-365-security-baseline.md)) |
| KPI-11 Critical and high vulnerabilities fixed within target (%) | Interim: 82 percent of Windows devices on current updates | Interim: 88 percent | 71 percent within deadline (first month of Defender for Endpoint Plan 2 data) | 90 percent within the patch policy's deadlines (14 days for critical, 30 for high) by M6; 95 by M7 | Baseline only | New source; the product line from Engineering starts in May |
| KPI-13 Access reviews completed on time (%) | No reviews run | 100 percent (manual reviews) | 89 percent (8 of 9) | 95 percent from the second automated review cycle | On track | First automated cycle started in April; one finance application review closed four days late |
| KPI-14 Security training completion (%) | 72 percent (annual video) | 91 percent (December and January modules) | 96 percent | 95 percent by due date; new hires in their first week | On track | Monthly modules since November; the People, Customer Support, and Engineering tracks and the first simulation in March (document [09](../09-security-awareness-and-training.md)) |
| KPI-15 Phishing simulation report rate and click rate | No simulation run | No simulation run | March: report 22 percent, click 12 percent. April (targeted round): report 29 percent, click 9 percent | By M7, against the first campaign at comparable difficulty: report rate up by at least half, click rate down by at least half | On track | Against the March campaign, the target means a report rate of 33 percent or more and a click rate of 6 percent or less; difficulty rated with the NIST Phish Scale and held comparable; no individual results reported |
| KPI-17 Security incidents by severity and cause (count) | 7 in the prior 12 months, rebuilt from tickets (low confidence) | Quarter to date: SEV-1 0, SEV-2 2, SEV-3 4, SEV-4 12 | Quarter to date: SEV-1 0, SEV-2 3, SEV-3 9, SEV-4 41 | No count target; every incident classified within 5 business days of closure | Not rated (no count target) | Two SEV-2s from credential phishing; four business email compromise (BEC) attempts stopped before any bank change |
| KPI-18 Exercise and post-incident actions closed on time (%) | No exercises on record | No actions due | 88 percent (15 of 17) | 90 percent from Phase 4 | At risk | Two tabletop actions late, with new dates approved by the CFO |
| KPI-23 Access requests fulfilled automatically (%) | 0 percent (accounts created by hand) | 3 percent | 36 percent | 60 percent by M6; 75 by M7 | On track | Birthright access packages since February |
| KPI-24 Corporate IT changes completed without incident or rollback (%) | No change records (December, the first full month of Change Advisory Board records: 89 percent) | 93 percent | 97 percent (56 of 58) | 95 percent from Phase 3; 97 by M7 | On track | Emergency changes shown separately in the register |

## 5. Program status by workstream against milestones

**Table 6 (illustrative; all statuses and event dates fictional). Milestones.**

| Milestone | When | Status | Evidence |
|---|---|---|---|
| M1 Listening report and environment baseline | Day 30 | Met | Listening report, inventories v1, and KPI baselines issued on 2026-12-01 |
| M2 Stabilization quick wins; risk register v1; current SOC 2 period on track | Day 60 | Met | Risk register v1 accepted by its owners on 2026-12-18 |
| M3 12-month plan, budget proposal, policy set, and NIST CSF 2.0 current and target Profiles approved | Day 90 | Met | Approved by the executive team on 2027-01-28, including Microsoft Defender Suite and Microsoft Entra ID Governance ([ADR-001](../adr/ADR-001-microsoft-365-security-licensing.md)) |
| D120 Day 120 readout (end of February 2027): first results | Day 120 (Friday 2027-02-26) | Held | Readout held on 2027-02-26 |
| M4 Current SOC 2 review period closes with no new exceptions caused by the Director's changes | Month 5 (March 2027) | Met, by management's tracking | Period closed 2027-03-31; audit firm report due in June |
| M5 The acquired product line's controls assessed, with a dated path into SOC 2 Type II scope | Month 9 (July 2027) | At risk | Assessment about two thirds complete; route goes to the executive team for confirmation at M5 (decision 1) |
| M6 Identity lifecycle automation live for all employees; phishing-resistant MFA for all admins and most users | Month 9 (July 2027) | On track | Automation is the control of record since April; admins complete; all-employee rings May to July |
| M7 First annual program review | Month 12 (October 2027) | On track | Scheduled for late October 2027 |

**Table 7 (illustrative; all statuses fictional). Workstreams.**

| Workstream | Status | Delivered this quarter | Next | KPIs |
|---|---|---|---|---|
| WS-1 Identity and access | On track | HR-driven account provisioning for employees (February); Privileged Identity Management (March); phishing-resistant sign-in enforced for the wave 2 group (February); lifecycle automation became the control of record (April) | All-employee phishing-resistant rings, May to July, toward M6 | KPI-08, KPI-09, KPI-12, KPI-13, KPI-22, KPI-23 |
| WS-2 Devices and endpoints | At risk | Defender for Endpoint Plan 2 on every enrolled computer (March); last Windows 10 devices replaced (April) | Remaining corporate Macs through automated device enrollment, three weeks late and now due in May | KPI-06, KPI-10, KPI-11 |
| WS-3 Email, collaboration, and data protection | On track | Older brand domains at a DMARC (Domain-based Message Authentication, Reporting, and Conformance) policy of reject; main domain at quarantine; "Anyone" sharing links turned off; Support's secure exchange path live | Main domain to reject in May, once the last marketing automation sender is aligned | KPI-17, KPI-24 |
| WS-4 Detection and response | On track | MDR parallel run from February and go-live on 2027-04-19; first executive tabletop (late February); first notification drill (April); ransomware playbook drafted | First technical exercise with the MDR provider in May | KPI-16, KPI-17, KPI-18 |
| WS-5 Governance, risk, and compliance | At risk | M3 approvals; M4 met by management's tracking; compliance automation platform in use ([ADR-007](../adr/ADR-007-compliance-automation-platform.md)); third-party reviews under way | Route for the acquired product line (decision 1), confirmed at M5 | KPI-01 to KPI-05 |
| WS-6 IT service and employee experience | On track | Service levels by priority in use since December (13.06), measured against the 85 percent target from Phase 3; the February dip recovered | Second acquired-device wave in May, sized to service desk capacity ([ADR-008](../adr/ADR-008-endpoint-management-standard.md)) | KPI-20, KPI-21, KPI-24 |
| WS-7 Enterprise systems, SaaS, and acquisition integration | On track | Single sign-on added for several applications that hold customer data; duplicate tools from the acquisitions scheduled for retirement at their contract end dates | Automatic provisioning for the next applications in document 15's order | KPI-07, KPI-23 |
| WS-8 Resilience | Off track | Microsoft 365 backup in place ([ADR-006](../adr/ADR-006-microsoft-365-backup.md)); three restore tests run, one missed its recovery time | OneDrive bulk restore rerun in May; product disaster recovery test with the SRE lead in June | KPI-19 |
| WS-9 Security culture and AI adoption | On track | People, Customer Support, and Engineering tracks launched (March); two phishing simulations; AI acceptable use rules in POL-02 approved at M3 | Oversharing clean-up before any Microsoft Copilot (formerly Microsoft 365 Copilot) pilot, in Phase 5 | KPI-14, KPI-15 |

## 6. Decisions requested

The Director proposes; the executive team or the named executive decides, and risk owners accept any residual risk. Decision 1 is previewed at this review so that Engineering and the audit firm can plan; the executive team takes it at M5, as document 10 sets.

**Table 8 (illustrative; all options and dates fictional). Decisions requested.**

| # | Decision | Options | Recommendation | Decision owner | Needed by |
|---|---|---|---|---|---|
| 1 | Route for the acquired product line into SOC 2 (M5) | A: the proposed route, a Type 1 report on controls as of 2027-08-31 (design at a point in time), issued in the second half of 2027, then a Type II period to 2028-03-31 (operating effectiveness over a period). B: go straight to a Type II period, with no Type 1. C: defer to year two | A, the route proposed in document [10](../10-governance-and-compliance-program.md): enterprise customers get a report sooner, and the core product's next report does not carry an unready product. Before M5, the Sales leader and the Chief Customer Officer confirm which waiting deals accept a Type 1, and how much business is waiting | The executive team confirms it at M5, with the CFO for the added audit cost and the Chief Customer Officer for customer commitments | M5: the month-9 Quarterly Risk Review (late July 2027) |
| 2 | R-12: an employee monitoring notice missing from POL-02 for one office's staff | A: add the notice to POL-02 and collect new acknowledgments from that office's staff by a set date. B: accept the residual for a set period, which at High also needs the CEO (document [11](../11-risk-management.md)). C: limit the monitoring that triggers the notice for that office's staff until the notice is in place | A (the POL-02 change follows the decision rights in document [10](../10-governance-and-compliance-program.md)) | General Counsel (risk owner), with the VP of People consulted as POL-02 co-owner | May IT and Security Steering Group |
| 3 | R-05: terminations reaching the HR system after the person's last day | A: People enters every termination on the day notice is given, including during month-end payroll close, as POL-14 sets, and checks the leaver queue daily. B: accept the late-entry risk for standard leavers (urgent leavers already go by phone) | A | VP of People (risk owner); option B, accepting a High residual, also needs the CEO (document [11](../11-risk-management.md)) | 2027-05-07 |

## 7. Look-ahead to July 2027

- **M5 and M6, month 9.** The executive team confirms the route for the acquired product line at M5 (decision 1). All-employee phishing-resistant rings run from May to July. Microsoft retires its own SMS and voice MFA for Global Administrators and external users on 2027-07-01 (a real Microsoft date), so guests are prepared first.
- **Exercises.** The first technical exercise with the MDR provider is in May, and the second executive tabletop is around June (document [08](../08-detection-and-incident-response.md)).
- **Recovery.** The OneDrive restore rerun is in May and the product disaster recovery test with the SRE lead is in June.
- **Email.** The main domain moves from quarantine to reject once its last third-party sender is aligned.
- **Next review.** Late July 2027, with the M5 and M6 checks.

Abbreviations: CEO, chief executive officer; CFO, chief financial officer; CTO, chief technology officer; VP, vice president; HR, human resources; MFA, multifactor authentication; CSAT, customer satisfaction score; SaaS, software as a service; SRE, Site Reliability Engineering; GRC, governance, risk, and compliance; SEV-1 to SEV-4, the incident severity levels in document 08. SOC 2 is the attestation report on Fabrikam's controls that customers ask for. Milestones M1 to M7 and the Day 120 readout (D120) are defined in document [03](../03-twelve-month-roadmap.md).

## Sources

- Measurement Guide for Information Security: Volume 1, Identifying and Selecting Measures (NIST SP 800-55v1, December 2024), Sec. 2.2 (assessments are not measures). NIST. https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-55v1.pdf . Checked 2026-10-13. Primary.
- The NIST Cybersecurity Framework (CSF) 2.0 (CSWP 29), Sec. 3.1 (current and target Organizational Profiles). NIST. https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf . Checked 2026-10-13. Primary.
- SOC 2 guide, Chapter 1 excerpt (2018 edition), on type 1 and type 2 examinations. AICPA, excerpt hosted by Wiley. https://catalogimages.wiley.com/images/db/pdf/9781945498602.excerpt.pdf . Checked 2026-10-13. Primary (AICPA text on a third-party host).
- SOC 2 Reporting on an Examination of Controls at a Service Organization Relevant to Security, Availability, Processing Integrity, Confidentiality, or Privacy (guide updated as of October 15, 2022), product page; the current edition of the guide excerpted above. AICPA & CIMA. https://www.aicpa-cima.com/cpe-learning/publication/soc-2-reporting-on-an-examination-of-controls-at-a-service-organization-relevant-to-security-availability-processing-integrity-confidentiality-or-privacy . Checked 2026-10-13. Primary.
- Passkeys by default and retirement of Microsoft-provided SMS and voice authentication. Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sms-voice-retirement . Checked 2026-10-13. Primary.
- Set up DMARC to validate email in Microsoft 365. Microsoft Learn. https://learn.microsoft.com/en-us/defender-office-365/email-authentication-dmarc-configure . Checked 2026-10-13. Primary.
