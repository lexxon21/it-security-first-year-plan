# 01. Scenario and assumptions

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

## Purpose and scope

This document describes Fabrikam, Inc. (fictional), the company this plan serves, and what the plan assumes about it on the incoming Director of IT and Security's first day. Every other document builds on it. Document [05](05-environment-discovery.md) verifies each assumption in the first 30 days, and the plan changes wherever one proves wrong.

## Proposals, not prescriptions

All cadences, targets, thresholds, and timelines in this repository are proposals for Fabrikam to tune after discovery. This statement covers every document and is not repeated. Microsoft facts are as checked on 2026-10-13.

## Company

Fabrikam is a privately held US software company.

- **What it sells.** A cloud workforce platform for employers with hourly workforces at client sites (security services, commercial cleaning, and staffing agencies). The platform covers recruiting and onboarding, core HR, payroll, benefits administration, and time tracking with GPS location at clock-in. Product has proposed voice verification for customers' administrators who call Fabrikam's support line. The proposal is held at the privacy review gate (document [10](10-governance-and-compliance-program.md)) and is not live.
- **Customers.** Several thousand small and mid-sized employers. Their HR and payroll staff use the web application. Their hourly workers use the mobile app on their own phones or on shared phones and tablets at work sites, which customers buy and manage. Customers depend on Fabrikam to run payroll on time.
- **Size and shape.** About 450 employees: roughly a third in Engineering and Product, then Customer Support and Success, Sales and Marketing, and General and Administrative. Remote-first, with two small offices inherited from acquisitions.
- **History.** Fabrikam grew through two acquisitions of smaller workforce-software companies. The products now sell as one platform. The acquired companies' email domains already run in Fabrikam's primary Microsoft 365 tenant. Some file storage, device management, identities, and software as a service (SaaS) applications from the acquisitions are still separate or duplicated.

## Product platform and data

The platform is multi-tenant SaaS hosted with one public cloud provider (deliberately unnamed). Engineering runs it, under the CTO. It integrates with customers' ERP and accounting systems (API and connectors), benefits carriers, and background screening providers, and it offers a public customer API. Product runs a customer status page, hosted apart from Microsoft 365 and the product platform. The Director's scope is corporate IT plus company-wide security governance, risk, and compliance. Product cloud security engineering is shared with Engineering under the RACI (responsible, accountable, consulted, informed) matrix in document [04](04-operating-model-team-and-budget.md). The SOC 2 scope covers both.

For its customers, Fabrikam processes applicant data, Form I-9 and E-Verify data, Social Security numbers, tax withholding forms, and direct-deposit bank details; benefits enrollment data, including dependents; background check results from screening partners; GPS location captured at clock-in; and payroll registers. Fabrikam is a service provider to its customers (the employers), and contracts set its notification duties.

## Corporate IT and people on day 1

- **Licensing.** Microsoft 365 E3 for all employees, including Exchange Online, Teams, SharePoint, OneDrive, Microsoft Entra ID P1, and Microsoft Defender for Endpoint Plan 1. Microsoft's July 2026 packaging update added Defender for Office 365 Plan 1, Intune Plan 2, Remote Help, and Intune Advanced Analytics to E3 (rollout stated as complete by August 1, 2026). Fabrikam has not configured these beyond defaults.
- **Identity and devices.** Cloud-only Microsoft Entra ID. Windows laptops for most staff, Macs for Engineering and Design, and personal iPhone and Android phones for email and Teams.
- **Corporate SaaS.** CRM, customer support platform, marketing automation, finance and accounting system, IT service management tool, and code hosting and CI/CD for Engineering. Fabrikam's own product is its HR system of record.
- **People.** An IT Operations Manager and three IT generalists run the service desk, devices, and Microsoft 365 administration. There are no dedicated security staff; senior engineers handle product security informally. A finance manager coordinates SOC 2 part time with an outside audit-readiness consultant.

## Compliance on day 1

- A SOC 2 Type II report covers the core HR and payroll product for the Security, Availability, and Confidentiality categories. The current review period ends in month 5 of the Director's tenure, at the end of March 2027.
- An acquired product line is not yet in SOC 2 scope, and enterprise customers are asking for it.
- Payroll and tax funds move through a banking partner, which is a subservice organization for SOC purposes. The executive team decides by M7 whether Fabrikam also needs a SOC 1 report or the Processing Integrity category (document [10](10-governance-and-compliance-program.md)).
- NIST CSF 2.0 is the chosen hub framework, with no Organizational Profile yet. There is no formal risk register, and the policies written for the first audit are out of date.

## Reporting line and decision rights

The Director reports to the CTO and joins the extended leadership team. The executive team is the CEO, CFO, CTO, Chief Product Officer, Chief Customer Officer, VP of People, and General Counsel. The CEO decides what goes to the investor board; the Director prepares material, but the Director's audience is the executive team.

Throughout the plan, the Director proposes the plan and the budget and owns execution; the executive team approves the plan, the budget, and policies; and named executives own and accept business risks. Document 04 describes the forums.

## Business calendar and day 1

Day 1 is Monday, 2026-11-02, so the plan runs from November 2026 to October 2027, starting with Phase 1, Listen and learn (days 1 to 30).

- Customers run payroll weekly or every two weeks.
- Benefits open enrollment runs from October to December.
- Year-end payroll and tax form season, mid-December through January, is the busiest and most sensitive period.
- Fabrikam freezes customer-facing changes from mid-December through January 31. Internal IT changes can continue with care.

## Day-1 assumptions

Working assumptions, not findings. The M1 listening report (day 30) records whether each held.

| ID | Area | Assumed state on day 1 | Verified in document 05 by |
|---|---|---|---|
| A-01 | Identity | Conditional Access requires multifactor authentication (MFA) for most users, mostly by push or SMS. Microsoft-provided SMS and voice MFA retire on 2027-02-01 (2027-07-01 for Global Administrators and external users). Several standing Global Administrators. No Privileged Identity Management, which needs Entra ID P2 or Microsoft Entra ID Governance | Policy, sign-in method, and role assignment review |
| A-02 | Identity | Some acquisition accounts have unclear owners. Guest accounts have accumulated. Users can consent to third-party apps | Owner check with People; guest and consent review |
| A-03 | Lifecycle | People emails IT to onboard and offboard; accounts are created by hand; offboarding sometimes lags. No access reviews. SaaS access is granted ad hoc | Sample of recent joiners and leavers against HR dates |
| A-04 | Devices | Windows laptops are in Intune with inconsistent compliance policies; Macs are partly managed. Local admin rights are common, with no Windows LAPS. A few Windows 10 devices remain, with unknown commercial Extended Security Updates (ESU) coverage; Year 1 ended 2026-10-13 | Reconciled device inventory; Windows 10 list |
| A-05 | Email | Defender for Office 365 Plan 1 (in E3 since the July 2026 update) runs on default policies. The main domain publishes DMARC at p=none, and its aggregate reports go to a mailbox nobody reviews. Of the two older brand domains from the acquisitions, one no longer sends mail but publishes no SPF or DMARC record, and the other sends only through a marketing service and has no DMARC record. Third-party services in four categories (CRM, support desk, marketing automation, transactional email) send as Fabrikam's domains, and some of them do not sign with a Fabrikam domain. Some devices and business applications may still send mail through SMTP AUTH with Basic authentication, which Exchange Online disables by default at the end of December 2026 (a secondary source) | Per-domain records and where their reports go; sender list; SMTP AUTH clients report |
| A-06 | Data | Teams and SharePoint sprawl. "Anyone" sharing links are allowed. No sensitivity labels. Customer payroll exports are sometimes emailed or kept in OneDrive during support cases | Sharing settings; support case walk-through |
| A-07 | Detection | Defender for Endpoint alerts go to a shared mailbox. No after-hours coverage. Audit logging is on at standard retention | Alert routing trace; retention settings |
| A-08 | SaaS | Duplicate tools from the acquisitions. No application inventory. Single sign-on covers some apps | Application inventory v1 |
| A-09 | Resilience | No Microsoft 365 backup beyond retention settings. The corporate continuity plan is out of date. Engineering owns product disaster recovery; the last test date is unknown | Retention settings; plan review; SRE lead |
| A-10 | Governance | SOC 2 evidence is gathered by hand near audit time. Control owners are unclear. Policies are stale. Vendor reviews are ad hoc | SOC 2 report and readiness tracker review |
| A-11 | People | Annual training video only. No phishing simulation | Training records |
| A-12 | AI | Employees use public AI tools without guidance. Leadership is interested in Microsoft Copilot (formerly Microsoft 365 Copilot). Product teams are building AI features | Stakeholder conversations; product review |

## Out of scope

- **Product cloud architecture.** Engineering owns the platform's design and operation; the plan covers only the shared security duties in the RACI.
- **Legal advice.** The plan names questions for the General Counsel and does not answer them.
- **Prices and detailed costs.** Licenses and cost drivers are named with their relative size, never with prices.
- **Physical security beyond the two offices.** Data center security sits with the cloud provider and with Microsoft.
- **Customer-side configuration,** except where Fabrikam's SOC 2 report relies on it as a complementary user entity control (a control that Fabrikam's system design assumes each customer operates).

## Phase plan

| Phase | Action ID | Action | Outcome | KPI | Owner role | Workstream |
|---|---|---|---|---|---|---|
| Phase 1 | 01.01 | Verify A-01 to A-12 with the methods in document 05 and record which held, which changed, and why | Assumptions confirmed or corrected in the M1 listening report | None (context document) | Director of IT and Security | WS-5 |
| Phase 3 | 01.02 | Update this document with the verified facts before the 12-month plan goes for approval | The plan and the NIST CSF 2.0 current Profile rest on verified facts at M3 | None (context document) | Director of IT and Security | WS-5 |
| Phase 5 | 01.03 | Revisit the scenario at the annual program review: new products, acquisitions, or regulation | The next-year plan starts from current facts at M7 | None (context document) | Director of IT and Security | WS-5 |

## Resourcing and dependencies

- **Roles.** The Director of IT and Security owns this document. In Phase 1 the IT Operations Manager, the Engineering Manager, and the Site Reliability Engineering (SRE) lead supply the verifying facts.
- **Partners and licenses.** None beyond the Microsoft 365 E3 tools and partners named in document 05.
- **Depends on.** Documents 04 (RACI and forums) and 05 (verification). Every other document depends on this one.

## Risks and open questions

- These assumptions are typical for a company of this size and history, not facts; the plan follows what discovery finds.
- The July 2026 E3 additions must be confirmed in Fabrikam's tenant before any plan step relies on them.
- The SMTP AUTH date comes from a Microsoft Message Center notice read through a community mirror, because Microsoft's own post could not be retrieved; recheck it before acting.

## Framework mapping

By identifier only, consistent with the [crosswalk](crosswalk/csf2-soc2-crosswalk.md).

| Theme | NIST CSF 2.0 | SOC 2 (2017 TSC) |
|---|---|---|
| Mission, stakeholders, and dependencies | GV.OC-01, GV.OC-02, GV.OC-04, GV.OC-05 | CC2.1, CC3.1 |
| Legal, regulatory, and contractual requirements | GV.OC-03 | CC2.3 |
| Reporting line and decision rights | GV.RR-01, GV.RR-02 | CC1.3 |

## Sources

- The NIST Cybersecurity Framework (CSF) 2.0 (CSWP 29). NIST. https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf . Checked 2026-10-13. Primary.
- 2017 Trust Services Criteria (With Revised Points of Focus, 2022), download page. AICPA & CIMA. https://www.aicpa-cima.com/resources/download/2017-trust-services-criteria-with-revised-points-of-focus-2022 . Checked 2026-10-13. Primary.
- SOC 2 guide, Chapter 1 excerpt (2018 edition), on complementary user entity controls and subservice organizations. AICPA, excerpt hosted by Wiley. https://catalogimages.wiley.com/images/db/pdf/9781945498602.excerpt.pdf . Checked 2026-10-13. Primary (AICPA text on a third-party host).
- Microsoft 365 Pricing and Packaging Updates, and its Public FAQ. Microsoft. https://www.microsoft.com/en-us/licensing/news/2026-m365-packaging-pricing-updates and https://www.microsoft.com/en-us/licensing/news/2026-m365-packaging-pricing-updates-faq . Checked 2026-10-13. Primary.
- Microsoft Entra service description, and Microsoft Entra ID Governance licensing fundamentals. Microsoft Learn. https://learn.microsoft.com/en-us/office365/servicedescriptions/azure-active-directory and https://learn.microsoft.com/en-us/entra/id-governance/licensing-fundamentals . Checked 2026-10-13. Primary.
- Overview of Microsoft Defender for Endpoint Plan 1. Microsoft Learn. https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-plan-1 . Checked 2026-10-13. Primary.
- Passkeys by default and retirement of Microsoft-provided SMS and voice authentication. Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sms-voice-retirement . Checked 2026-10-13. Primary.
- Product Lifecycle FAQ, Extended Security Updates. Microsoft Learn. https://learn.microsoft.com/en-us/lifecycle/faq/extended-security-updates . Checked 2026-10-13. Primary.
- Deprecation of Basic authentication in Exchange Online. Microsoft Learn. https://learn.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/deprecation-of-basic-authentication-exchange-online . Checked 2026-10-13. Primary.
- MC786329, Exchange Online to retire Basic Auth for Client Submission (SMTP AUTH). mc.merill.net, a community mirror of Microsoft 365 Message Center posts. https://mc.merill.net/message/MC786329 . Checked 2026-10-13. Secondary.
- Enterprise data protection in Microsoft Copilot and Microsoft Copilot Chat (product name change). Microsoft Learn. https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection . Checked 2026-10-13. Primary.
- Shared responsibility in the cloud. Microsoft Learn. https://learn.microsoft.com/en-us/azure/security/fundamentals/shared-responsibility . Checked 2026-10-13. Primary.
