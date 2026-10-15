# ADR-002: The HR system of record drives the identity lifecycle

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

## Status

Proposed. Date: 2026-10-13.

The Director of IT and Security proposes this decision; the executive team approves it with the 12-month plan and budget at M3.

## Context

Fabrikam (fictional) runs its own product as its HR system of record. Identity work today starts with an email from People to IT: accounts are created by hand, offboarding sometimes lags, access is never reviewed, and SaaS access is granted ad hoc (day-1 assumption A-03). Accounts from the acquisitions have unclear owners, and guests have accumulated (A-02).

The gap matters more at Fabrikam than at most companies of its size. Staff can reach sensitive company and employee data through corporate systems, so a leaver who keeps access is a direct exposure (R-05, R-07). SOC 2 criteria CC6.2 and CC6.3 cover issuing, changing, and removing access, so late removals become exceptions that slow enterprise sales (R-11). New hires lose their first day waiting for access (KPI-22), and a four-person IT team does all of it by hand (R-14). Because the HR record also triggers a new hire's first credential, a fraudulent remote hire who gets through onboarding would have the same reach (R-15), so document 07 puts an identity check against a government-issued photo ID before the first Temporary Access Pass is released. NIST CSF 2.0 frames the same link: "Cybersecurity is included in human resources practices" (GV.RR-04), and access is managed, enforced, and reviewed under least privilege and separation of duties (PR.AA-05).

Microsoft 365 E3 already includes Microsoft Entra ID P1, which covers API-driven inbound provisioning from any system of record, including an HR app. Lifecycle Workflows and automatic assignment of access packages need Microsoft Entra ID Governance, or Microsoft Entra Suite, which includes it; access reviews need Governance too, with some capabilities available on Entra ID P2. Milestone M6 (month 9) commits to identity lifecycle automation for all employees.

## Decision drivers

1. Leavers lose access on time, every time, with evidence (KPI-12, R-05, CC6.2).
2. New hires are productive on day one (KPI-22).
3. Access shrinks when people move, instead of only growing (R-06, KPI-13).
4. A small team can run it, and most access is granted without IT hands (R-14, KPI-23).
5. One authoritative record of who works at Fabrikam, with no second HR database.
6. Only identity attributes leave the HR system (R-12, POL-05).
7. Cost in proportion to a company of about 450 people, using what Fabrikam already pays for first ([ADR-001](ADR-001-microsoft-365-security-licensing.md)).
8. The process still works when the HR product or the automation is unavailable.

## Options considered

### Option 1: The HR system drives identity through inbound provisioning and Lifecycle Workflows (chosen)

An integration client reads Fabrikam's worker records through the product's public customer API and sends them to the inbound provisioning API of Microsoft Entra ID (Entra ID P1). Lifecycle Workflows run joiner, mover, and leaver tasks. Access packages give birthright access by department and job family and govern everything requested. Access reviews run by system and by population, SCIM provisions the SaaS apps that support it, and the ITSM tool handles the rest. The workflow, automatic assignment, and review features need Microsoft Entra ID Governance.

- **Pros.** Leavers are removed on a schedule, or on demand, with an audit trail. Birthright access is ready on day one, and moves remove old access automatically. Evidence comes from the system rather than from screenshots. No new platform is needed, and because the feed runs on P1, it can start before the Governance purchase.
- **Cons.** It adds a Governance license for every member user in scope. One capability of API-driven inbound provisioning, clearing attribute values, is still in preview (as of 2026-10-13); the feature itself has been generally available since March 2024. Scheduled workflows are evaluated on an interval (default three hours), so urgent cases need an on-demand path. The workflow account tasks cannot disable users who hold Microsoft Entra roles, so administrators need a manual step. Fabrikam must build and own a small integration client.

**Variant considered and rejected:** Microsoft Entra ID P2 without Governance, plus scripts. P2 covers access packages and basic reviews but not Lifecycle Workflows or automatic assignment, and Microsoft states that no new identity governance features will be added to P2. The scripts would become a key-person dependency (R-14).

### Option 2: IT creates accounts from HR tickets (status quo, improved)

People submits ITSM forms instead of emails, and IT works from checklists.

- **Pros.** No new licenses or build work. Simple to understand. Forms add the timestamps KPI-12 needs.
- **Cons.** Every event still waits on two handoffs, so timeliness depends on people remembering. There is no birthright model, so new hires wait and movers keep old access. Reviews and evidence stay manual, and the load grows with every hire and every acquisition.

**Rejected as the end state.** It remains the interim process in Phases 2 and 3 and the documented manual fallback.

### Option 3: A separate identity governance platform (category only)

- **Pros.** Deep governance features, many connectors, and possibly one process across corporate identity and the product cloud's own access controls.
- **Cons.** A second platform to buy, implement, secure, and staff, largely overlapping Microsoft Entra ID Governance for an estate built on Microsoft 365. Implementation would run past the M6 window, and it adds another privileged integration (R-08). The cost driver is large for Fabrikam's size.

**Rejected for now.** The revisit triggers below say when to reconsider it.

## Decision

Adopt Option 1.

- The HR system is authoritative for who works at Fabrikam, in which role, under which manager, and from when to when. Microsoft Entra ID is authoritative for the accounts and access derived from that.
- The feed creates cloud-only accounts in a disabled state. No on-premises directory is introduced.
- HR attributes grant birthright access only. Privileged and sensitive access is always requested, approved, time-limited, and reviewed.
- Automation runs alongside the ITSM checklist until the current SOC 2 period closes (M4) and becomes the control of record in April 2027.
- The ITSM checklist and the urgent-leaver runbook stay documented and rehearsed as the manual fallback.
- Governance capabilities are licensed for every member user in scope through the form ADR-001 chooses: Microsoft Entra ID Governance Step Up for Microsoft Entra ID P2, alongside Microsoft Defender Suite, from Phase 4; or, if the executive team does not approve Defender Suite at M3, the base Microsoft Entra ID Governance product on E3.

Service levels, the access model, and the phase plan are in document [07](../07-identity-lifecycle-joiners-movers-leavers.md).

## Consequences

### Positive

- Leaver removal is scheduled, available on demand for urgent cases, and measured every month (KPI-12).
- New hires get their license, birthright access, and a passwordless first sign-in on day one (KPI-22, [ADR-004](ADR-004-phishing-resistant-authentication-rollout.md)).
- Every move triggers an access review and drops old birthright access automatically (KPI-13).
- Most access grants need no IT hands (KPI-23), which frees the small team (R-14).
- Evidence for CC6.2 and CC6.3 comes from workflow history, review records, and audit logs.

### Negative

- **HR data quality becomes a security control.** A missing termination leaves access open, a wrong date can lock out the wrong person, and a wrong manager sends the day-one pass to the wrong inbox. People co-owns POL-14 and takes on entry deadlines (proposals: hires five business days ahead, terminations on the day notice is given). Required-field checks, a guard against mass leave-date changes, change alerts, and a daily reconciliation catch errors, and KPI-12 makes them visible.
- **License dependency.** Microsoft requires enough Governance licenses to cover every member user in scope of the features, in practice the whole workforce including contractors. The subscription also needs an active prerequisite that includes Entra ID P1 or P2, and guest governance uses monthly active user billing through an Azure subscription. If the subscription or its prerequisite expires, Microsoft warns that Governance scenarios might not function as expected, and it documents that eligible Privileged Identity Management assignments are removed when that license expires. Renewal dates are tracked in the risk register. The HR feed itself runs on P1 and would continue.
- **A manual fallback must be maintained.** The ITSM checklist and the urgent-leaver runbook must work without the HR product, the feed, or the workflows. They are rehearsed every six months and after major workflow changes (proposal), and they are always used for leavers who hold administrator roles.
- **Dependency on Fabrikam's own product.** An outage of the HR product pauses the feed, and a compromise could feed false records. Urgent leavers never depend on the feed, new accounts start disabled, and HR attributes never grant privileged access.
- **A new high-value credential.** The integration client can create users, so its credential is managed under document [06](../06-microsoft-365-security-baseline.md) and watched by the Systems Engineer (Identity and Endpoint), with the Director of IT and Security and the MDR provider once live if the chosen service triages Fabrikam's custom detections ([ADR-003](ADR-003-managed-detection-and-response.md); document [07](../07-identity-lifecycle-joiners-movers-leavers.md), R-08).

## Risks and mitigations

| Risk | Mitigation |
|---|---|
| Microsoft changes the status or behavior of inbound provisioning | Recheck the status before April 2027; the ITSM path can carry joiners and leavers at any time |
| Late or wrong HR entries | Entry deadlines in POL-14, required fields, a reconciliation each morning, the guard against mass leave dates |
| A scheduled run misses an urgent leaver | On-demand workflow plus runbook, with the one-hour target measured at Entra ID |
| Administrators fall outside the workflow account tasks | Privileged leaver steps in the checklists (L10 and U4), emergency access validation in document 06, and the daily reconciliation |
| Governance is not funded or lapses | Degraded mode: P1 feed, ITSM tickets, manual reviews; renewal tracked as a risk |
| Reviewers approve without reading | Small, targeted reviews; removal on no response for requested access; completion and removal rates reported |
| The integration credential is misused | Least privilege, storage and rotation under document 06; alerts watched by the Systems Engineer (Identity and Endpoint), with the Director of IT and Security and the MDR provider once live if it triages custom detections (ADR-003, document 07) |

## Revisit when

- Fabrikam acquires a company that brings its own HR system or Microsoft 365 tenant.
- KPI-12 misses its target for two consecutive months after M6.
- Microsoft changes the status, licensing, or limits of API-driven inbound provisioning or Lifecycle Workflows.
- Engineering needs one governance process across corporate identity and the product cloud's own access controls, the main case for Option 3.
- ADR-001 lands on a license set without Governance capabilities.
- A change to the HR product's customer API breaks the feed.

## Related documents

- [07. Identity lifecycle: joiners, movers, and leavers](../07-identity-lifecycle-joiners-movers-leavers.md)
- [Joiner, mover, and leaver checklists](../templates/joiner-mover-leaver-checklists.md)
- [06. Microsoft 365 security baseline](../06-microsoft-365-security-baseline.md)
- [10. Governance and compliance program](../10-governance-and-compliance-program.md)
- [13. IT service management](../13-it-service-management.md)
- [15. Enterprise systems and SaaS](../15-enterprise-systems-and-saas.md)
- [ADR-001: Microsoft 365 security licensing](ADR-001-microsoft-365-security-licensing.md)
- [ADR-003: Managed detection and response](ADR-003-managed-detection-and-response.md)
- [ADR-004: Phishing-resistant authentication rollout](ADR-004-phishing-resistant-authentication-rollout.md)
- [ADR-005: Acquired-company consolidation](ADR-005-acquired-company-consolidation.md)

## Sources

- API-driven inbound provisioning concepts. Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-concepts . Checked 2026-10-13. Primary.
- Archive for Microsoft Entra releases and announcements (March 2024, General Availability - API driven inbound provisioning). Microsoft Learn. https://learn.microsoft.com/en-us/entra/fundamentals/whats-new-archive . Checked 2026-10-13. Primary.
- Microsoft Entra ID Governance licensing fundamentals. Microsoft Learn. https://learn.microsoft.com/en-us/entra/id-governance/licensing-fundamentals . Checked 2026-10-13. Primary.
- Microsoft Entra service description. Microsoft Learn. https://learn.microsoft.com/en-us/office365/servicedescriptions/azure-active-directory . Checked 2026-10-13. Primary.
- Understanding lifecycle workflows. Microsoft Learn. https://learn.microsoft.com/en-us/entra/id-governance/understanding-lifecycle-workflows . Checked 2026-10-13. Primary.
- Lifecycle Workflows tasks and definitions. Microsoft Learn. https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-tasks . Checked 2026-10-13. Primary.
- What are access reviews? Microsoft Learn. https://learn.microsoft.com/en-us/entra/id-governance/access-reviews-overview . Checked 2026-10-13. Primary.
- Configure an automatic assignment policy for an access package in entitlement management. Microsoft Learn. https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-access-package-auto-assignment-policy . Checked 2026-10-13. Primary.
- The NIST Cybersecurity Framework (CSF) 2.0 (CSWP 29). NIST. https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf . Checked 2026-10-13. Primary.
- 2017 Trust Services Criteria (With Revised Points of Focus, 2022), download page. AICPA & CIMA. https://www.aicpa-cima.com/resources/download/2017-trust-services-criteria-with-revised-points-of-focus-2022 . Checked 2026-10-13. Primary.
