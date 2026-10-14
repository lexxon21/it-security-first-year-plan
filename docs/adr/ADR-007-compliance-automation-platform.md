# ADR-007: Compliance automation platform

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

## Status

Proposed. Date: 2026-10-13.

The Director of IT and Security proposes this decision; the executive team approves the subscription as a line in the budget proposal at M3. Risks addressed: R-11 (primary) and R-14.

## Context

At day 1, Fabrikam (fictional) gathers SOC 2 evidence by hand near audit time, control owners are unclear, and a finance manager coordinates SOC 2 part time with an outside audit-readiness consultant (assumption A-10). The current review period for the core HR and payroll product ends on 2027-03-31 (M4), and the next one should start on 2027-04-01 with no gap. Document [10](../10-governance-and-compliance-program.md) brings the acquired product line into scope: readiness from February 2027, a dated path at M5, a Type 1 report as of 2027-08-31, and a first Type II period that ends with the core product's period on 2028-03-31. AICPA's SOC 2 guide says a service auditor is engaged for either a type 1 or a type 2 examination, not a mix of the two, so for several months Fabrikam runs two products and two report types at once. Several controls of record also change when the next period starts: the HR-driven identity lifecycle ([ADR-002](ADR-002-hr-system-of-record-drives-identity.md)) and MDR monitoring ([ADR-003](ADR-003-managed-detection-and-response.md)).

Evidence lives in many systems: Microsoft Entra ID, Intune, and Defender in Microsoft 365; the public cloud provider that hosts the product; the HR system of record, which is Fabrikam's own product; the IT service management (ITSM) tool, which holds joiner, leaver, change, incident, and vendor intake records; and code hosting and CI/CD for product changes. Some of it expires. Microsoft Entra keeps sign-in and audit logs for 30 days on Entra ID P1, and Microsoft Purview Audit (Standard), included in Microsoft 365 E3, keeps unified audit log records for 180 days. Document [06](../06-microsoft-365-security-baseline.md) archives logs for investigations; this decision is about control evidence, which has to be captured on a schedule rather than rebuilt months later.

The team is small: the Director, a GRC Analyst (hiring sequence in document [04](../04-operating-model-team-and-budget.md)), and an IT team of about five. NIST CSF 2.0 is the hub framework, and the [crosswalk](../crosswalk/csf2-soc2-crosswalk.md) relates it to the SOC 2 criteria. The SOC 2 audit firm needs evidence that shows its source and when it was collected, and Fabrikam needs to be able to leave any tool with its records intact. AICPA's ethics staff noted in April 2026 that business arrangements between CPA firms and SOC tool providers can raise significant threats to compliance with the AICPA Code of Professional Conduct, so the tool choice and the audit firm relationship stay separate.

## Decision drivers

1. Two products in SOC 2 scope within the plan year, with shared corporate controls tested once and used for both.
2. A lean team (R-14): collecting evidence and reminding control owners must not depend on one person's memory.
3. Evidence produced as work happens, so a failing control is found and fixed months before the audit firm samples it (KPI-03, KPI-04).
4. Integrations with Microsoft 365 (Entra ID, Intune, Defender), the cloud provider, the HR system of record, the ITSM tool, and code hosting.
5. Auditor access to evidence where it lives, with its source and timestamp, instead of files sent by email.
6. Exportability: controls, mappings, evidence, and history leave in open formats at any time, and in full at exit.
7. CSF 2.0 as the hub: a custom framework and the crosswalk mapping, with room for more criteria later (Processing Integrity, Privacy, or a CCPA cybersecurity audit if General Counsel says one applies).
8. The tool's own security and data minimization: it will hold configuration data and workforce user lists, but no customer workforce data.
9. Cost in proportion to a company of about 450 people.
10. No disruption to the current review period (M4).

## Options considered

### Option A: A compliance automation platform (category; no vendor named)

Software as a service that connects to identity, device, cloud, HR, ticketing, and code systems through their APIs, runs scheduled control tests, collects evidence with its source and collection time, tracks policies, vendor reviews, and exceptions, and gives the audit firm its own view of the evidence.

Pros:
- Evidence arrives on a schedule from the systems that run the controls, which ends the near-audit scramble (A-10).
- Scheduled tests show drift between examinations, for example an administrator without phishing-resistant MFA or a laptop without disk encryption, while there is still time to fix it.
- Shared corporate controls can be scoped once to both products, which suits the acquired product line's Type 1 and Type II.
- Policy reviews, vendor reviews, and exceptions sit in one place with reminders (KPI-02, KPI-04, KPI-05).
- An auditor workspace shortens the request-and-response cycles of fieldwork.
- Custom frameworks, where a product offers them, let the CSF 2.0 Core and the crosswalk load directly (confirmed during selection, not assumed).

Cons:
- A subscription, usually priced on headcount, frameworks, and products in scope.
- Another third party with broad read access to configuration data and user lists. It must pass the full POL-10 review, and its connectors are integration credentials to govern (R-08).
- Automated tests check settings, not judgment. A passing test does not show that an access review was thoughtful or that a vendor review read the report, so manual controls still need human evidence.
- Connectors may not cover Fabrikam's own HR product or Engineering's custom tooling, so some evidence stays manual.
- Lock-in, if export is weak.
- Setup and mapping work in February and March (the Director, then the GRC Analyst), while the current period closes.

### Option B: Spreadsheets and shared folders (not chosen; kept as the fallback)

A control matrix in an Excel workbook, evidence folders in SharePoint with version history, and calendar reminders, all included in Microsoft 365 E3.

Pros:
- No new spend and no new vendor with access to Fabrikam data.
- Full control of the structure, in tools the team already knows.
- Works for the current period, which is why the current period's evidence stays in its existing form until M4.

Cons:
- Evidence is still gathered by people, late, from many systems: the day-1 problem (A-10).
- Showing that populations are complete (every leaver, every change) is manual and easy to get wrong.
- Nothing watches controls between examinations, so failures surface when the audit firm samples them (KPI-03, KPI-04).
- A second product and a second report type double the manual work, and knowledge concentrates in one person (R-14).
- Auditor access means sharing folders or sending files, and the audit trail is whatever SharePoint records.

Not chosen as the main approach because it keeps the failure mode the plan is trying to fix. It remains the documented fallback if the subscription is not approved at M3.

### Option C: A general GRC suite (rejected)

An enterprise governance, risk, and compliance suite with configurable modules for risk, policy, audit, vendor, and issue management.

Pros:
- Broad and highly configurable; can support enterprise risk management, internal audit, and many frameworks and business units.
- Strong workflow and reporting for large programs.

Cons:
- Built for organizations with dedicated GRC administrators; Fabrikam would need configuration work and administration it does not have.
- Evidence connectors for Fabrikam's specific SaaS and cloud systems would have to be confirmed one by one, and any gap becomes custom integration work.
- Time to value would likely miss the start of the next period in April 2027 and the acquired product line's Type 1.
- Cost and administration out of proportion to a company of about 450 people with one GRC Analyst.

Rejected because its administration and time to value do not fit the plan year or the team. It comes back into consideration if Fabrikam later needs enterprise risk management or internal audit modules.

## Decision

Fabrikam will adopt a compliance automation platform (category) for SOC 2 evidence and control monitoring. The Director of IT and Security, with the outside audit-readiness consultant, evaluates products in Phase 3 against the criteria below (action 10.15), because the GRC Analyst starts in March 2027 in the base case; the executive team approves the subscription with the budget at M3; the contract is signed in February 2027 after the audit firm walks through sample evidence (10.18); and the platform goes live for the review period that starts on 2027-04-01 (10.20). The current period's evidence stays in its existing form until it closes (M4), so nothing moves mid-period.

Guardrails:

1. **Systems of record stay the source of truth.** Entra ID, Intune, the ITSM tool, the cloud provider, and code hosting run the controls; the platform reads and records.
2. **No customer workforce data in the platform.** Evidence is configuration, metadata, and samples with personal data kept to a minimum; a record that holds customer data is referenced, not uploaded.
3. **Narrow connectors.** Each connector gets the narrowest permissions its vendor documents. The Security Engineer (until that role starts, March 2027 in the base case, the Director of IT and Security with the Systems Engineer (Identity and Endpoint)) reviews them before connection and with the other integration credentials afterward, and platform administrators sign in through Microsoft Entra single sign-on with phishing-resistant MFA, enforced by a Conditional Access authentication strength (Microsoft Entra ID P1, included in Microsoft 365 E3).
4. **No Secure Score as evidence.** Microsoft Secure Score is not audit evidence. Microsoft says it "isn't an absolute measurement of how likely your system or data could be breached", and document 06 treats it as a tracking input only.
5. **Separate from the audit firm.** The platform and the audit firm are chosen separately, with no bundled audit-and-platform deal, and Fabrikam asks the audit firm to disclose any business arrangement with the chosen vendor.
6. **A passing test is not the same as an effective control.** Manual and judgment controls (access reviews, vendor reviews, risk acceptance) keep their human evidence, and the GRC Analyst samples automated results each quarter (proposal).

If the subscription is not approved at M3, Option B applies with a structured control matrix, a monthly evidence calendar, and the same evidence rules (document 10, section 3.5), and the Director records the effect on R-11 and R-14 for their owners.

### Selection criteria for Phase 3

Weights are proposals. A product that cannot export everything in open formats, cannot use Microsoft Entra single sign-on, or cannot show its own current SOC 2 Type II report is out regardless of score.

| Criterion | Weight | What good looks like |
|---|---|---|
| Integrations | 25% | Working connectors for Microsoft Entra ID, Intune, and Defender, the cloud provider that hosts the products, the ITSM tool, and code hosting, plus a supported path for the HR system of record (API or scheduled file), shown in a trial against Fabrikam's own tenant rather than a demonstration environment |
| Two products and two report types | 15% | Controls scoped per system, shared corporate controls tested once, and a Type 1 and a Type II period running side by side |
| Auditor access | 15% | An auditor workspace with named accounts and MFA, sample requests handled in the tool, evidence showing its source and collection time, and access that ends with fieldwork |
| Exportability and exit | 15% | Full export of controls, mappings, evidence, test history, policies, and vendor records in open formats; an API; deletion confirmed in writing at exit |
| Frameworks and mapping | 10% | Custom frameworks, tested by loading the CSF 2.0 Core and the [crosswalk data](../../data/csf2-soc2-crosswalk.csv); room to add criteria later |
| Vendor security | 10% | Its own current SOC 2 Type II report, data location, subprocessor list, breach notice terms that fit Fabrikam's shortest customer clock (document [08](../08-detection-and-incident-response.md)), and least-privilege connectors |
| Effort and cost drivers | 10% | Live before 2027-04-01, administration one GRC Analyst can carry, and cost drivers stated plainly (headcount, products, frameworks, integrations) |

Because the HR system of record feeds Microsoft Entra ID (ADR-002), the platform can read worker status from Entra. A direct HR connection is needed only for fields Entra does not hold, such as screening completion dates under POL-14, which keeps the least data leaving the HR system.

## Consequences

Positive:
- Evidence is collected as work happens, and control failures are found early (KPI-03, KPI-04).
- Policy reviews (KPI-02), vendor reviews (KPI-05), and exceptions are tracked in one place.
- Shared controls serve both products and the CSF 2.0 Profile, mapped once through the crosswalk.
- Less dependence on any one person (R-14); the finance manager's part-time SOC 2 role ends cleanly at M4.
- Fieldwork takes less of the audit firm's and the control owners' time.

Negative:
- A recurring subscription; document 04 sizes the cost drivers.
- A new integration with broad read access to govern (R-08).
- Setup work in Phase 4, alongside the close of the current period and the acquired product line's readiness assessment.
- The risk of false confidence if people stop looking behind a passing test.

## Risks and mitigations

| Risk | Mitigation |
|---|---|
| Connector credentials are stolen or misused | Narrow permissions; single sign-on with phishing-resistant MFA for administrators; connector credentials reviewed with the other integration credentials (documents 06 and 07); full POL-10 review of the vendor |
| The audit firm will not rely on platform evidence | An evidence walkthrough with the audit firm in February 2027 (10.18), before go-live |
| The platform vendor has a breach or fails | Breach notice and exit terms in the contract; a full export kept in Fabrikam's SharePoint each quarter (proposal); Option B as the fallback |
| Lock-in | Export tested before purchase and again each year |
| Automated tests mistaken for assurance | Quarterly sampling by the GRC Analyst; human evidence for manual controls; the audit firm tests independently |
| Independence concerns | Separate selection, a disclosure question to the audit firm, and no bundled deals |
| Customer data ends up in the tool | Evidence rules in POL-05 and document 10; the GRC Analyst checks uploads during sampling |
| The subscription is not approved at M3 | Option B fallback; the effect on R-11 and R-14 goes to their owners |

## Revisit when

- The audit firm cannot rely on platform evidence for a material share of controls in the first period.
- Fabrikam adds criteria or a framework the platform cannot model: Processing Integrity, Privacy, a SOC 1 report, or a CCPA cybersecurity audit.
- The platform vendor has a security incident, loses a clean SOC 2 opinion, or changes ownership.
- An acquisition adds another product or another Microsoft 365 tenant.
- The contract comes up for renewal, or at the first annual program review (M7).
- Fabrikam grows to need enterprise risk management or internal audit modules, which reopens Option C.

## Related documents

- [10. Governance and compliance program](../10-governance-and-compliance-program.md): the SOC 2 program, the evidence rules, and actions 10.15, 10.18, and 10.20.
- [CSF 2.0 and SOC 2 crosswalk](../crosswalk/csf2-soc2-crosswalk.md) and its [data file](../../data/csf2-soc2-crosswalk.csv).
- Documents [04](../04-operating-model-team-and-budget.md) (team and cost drivers), [05](../05-environment-discovery.md) (discovery), [06](../06-microsoft-365-security-baseline.md) (logging and Secure Score), [07](../07-identity-lifecycle-joiners-movers-leavers.md) (identity evidence), [08](../08-detection-and-incident-response.md) (MDR evidence and notification clocks), [11](../11-risk-management.md) (R-11 and R-14), [12](../12-metrics-and-executive-reporting.md) (KPI-03 and KPI-04), [13](../13-it-service-management.md) (change records), and [15](../15-enterprise-systems-and-saas.md) (application inventory).
- [ADR-001](ADR-001-microsoft-365-security-licensing.md), [ADR-002](ADR-002-hr-system-of-record-drives-identity.md), and [ADR-003](ADR-003-managed-detection-and-response.md).

## Sources

- Ethics Staff Insights: Business arrangements with SOC tool providers (April 13, 2026). AICPA & CIMA. https://www.aicpa-cima.com/resources/article/esi-soc . Checked 2026-10-13. Primary.
- SOC 2 Reporting on Controls at a Service Organization, Chapter 1 (2018 edition: type 1 and type 2 engagements, specified parties). AICPA, excerpt hosted by Wiley. https://catalogimages.wiley.com/images/db/pdf/9781945498602.excerpt.pdf . Checked 2026-10-13. Primary (AICPA text on a third-party host).
- SOC 2 Reporting on an Examination of Controls at a Service Organization Relevant to Security, Availability, Processing Integrity, Confidentiality, or Privacy (guide updated as of October 15, 2022), product page. AICPA & CIMA. https://www.aicpa-cima.com/cpe-learning/publication/soc-2-reporting-on-an-examination-of-controls-at-a-service-organization-relevant-to-security-availability-processing-integrity-confidentiality-or-privacy . Checked 2026-10-13. Primary.
- The NIST Cybersecurity Framework (CSF) 2.0 (CSWP 29, February 26, 2024), Appendix A (the Core and the Reference Tool's human- and machine-readable exports). NIST. https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf . Checked 2026-10-13. Primary.
- CSF 2.0 Reference Tool. NIST. https://csrc.nist.gov/Projects/Cybersecurity-Framework/Filters#/csf/filters . Checked 2026-10-13. Primary.
- Microsoft Entra data retention (ms.date 2026-01-06). Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/monitoring-health/reference-reports-data-retention . Checked 2026-10-13. Primary.
- Learn about auditing solutions in Microsoft Purview. Microsoft Learn. https://learn.microsoft.com/en-us/purview/audit-solutions-overview . Checked 2026-10-13. Primary.
- Microsoft Purview service description (Audit (Standard) in Microsoft 365 E3). Microsoft Learn. https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description . Checked 2026-10-13. Primary.
- Microsoft Secure Score. Microsoft Learn. https://learn.microsoft.com/en-us/defender-xdr/microsoft-secure-score . Checked 2026-10-13. Primary.
- Overview of Conditional Access Authentication Strengths (ms.date 2025-03-04), prerequisites. Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-strengths . Checked 2026-10-13. Primary.
