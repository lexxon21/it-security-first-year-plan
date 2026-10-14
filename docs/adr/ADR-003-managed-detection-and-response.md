# ADR-003: Managed detection and response

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

## Status

Proposed. Date: 2026-10-13.

The Director of IT and Security proposes this decision; the executive team approves it with the plan and budget at M3. Risks addressed: R-10 (primary), R-01, R-03, R-14.

## Context

At day 1, Defender for Endpoint alerts go to a shared mailbox and nobody covers nights or weekends (assumption A-07). Fabrikam (fictional) has an IT Operations Manager and three IT generalists and no dedicated security staff; document [04](../04-operating-model-team-and-budget.md) adds a Security Engineer, but no realistic hiring plan for a company of about 450 people staffs every hour of the week. The threats that matter most (document [17](../17-threat-profile.md)) move fast: a stolen session token can become mailbox rules and a fraudulent payment request within hours, and attacks do not wait for business hours. Customer contracts set notification clocks (document [08](../08-detection-and-incident-response.md)), and a thin, slow investigation makes them hard to meet. That is risk R-10.

Microsoft offers "Microsoft Defender Experts MDR", "a managed detection and response service", in two plans. Plan 1, the service previously called Defender Experts for XDR, covers Microsoft Defender workloads. Plan 2 adds selected non-Microsoft telemetry collected in Microsoft Sentinel; it requires Microsoft Sentinel and "a minimum of 1,500 licensed seats", well above Fabrikam's size, so it is not an option. Independent MDR providers also operate on top of Microsoft Defender XDR.

Any MDR needs telemetry worth investigating. Microsoft 365 E3 has no endpoint detection and response (EDR) and only Plan 1 email protection; Defender Experts covers Defender for Endpoint P2, Defender for Office 365 P2, Defender for Identity, Defender for Cloud Apps, and Entra ID P2, and needs Entra ID P2 for identity coverage. This decision therefore depends on [ADR-001](ADR-001-microsoft-365-security-licensing.md).

NIST SP 800-61 Rev. 3 treats incident response as work across all six CSF 2.0 Functions. An MDR covers much of Detect and part of Respond; governance, business decisions, communication, and recovery stay with Fabrikam.

## Decision drivers

1. Round-the-clock detection and containment for identity, email, and endpoint attacks (R-01, R-03, R-10).
2. Containment in minutes inside limits the executive team approves in advance (the response authority matrix in document [08](../08-detection-and-incident-response.md)).
3. Fit with Microsoft 365 and Defender XDR: no new endpoint agent and no security information and event management (SIEM) system in year one.
4. Realism for an IT and security team of about five people (R-14).
5. Evidence for the SOC 2 monitoring and incident criteria (CC7.2 to CC7.4) without disturbing the current review period (M4).
6. Cost in proportion to a company of about 450 people, with a clean exit.
7. Clear boundaries: whatever the provider does not do, such as incident response for an active compromise or product platform monitoring, is covered elsewhere.

## Options considered

### Option A: Microsoft Defender Experts MDR Plan 1

Pros:
- Microsoft security analysts "manage your incident queue around the clock, triage and investigate incidents on your behalf, and either take action or guide your team through the response"; proactive hunting (Defender Experts Hunting) and Ask Defender Experts are included.
- Works natively in Defender XDR. The experts hunt over Fabrikam's advanced hunting data, which stays in its Defender storage location.
- Access is governed: granular delegated admin privileges (GDAP), a cross-tenant access policy, Conditional Access that requires the experts to use MFA and compliant devices, and just-in-time access approved in Microsoft's internal system, with the experts' sign-ins recorded in Fabrikam's Entra sign-in logs.
- Response authority is configurable: "Respond directly to active threats" (Security Operator access), with exclusions by device group and Entra security group that receive remediation guidance instead of action. That maps directly onto Fabrikam's call-first groups.
- Incident notification contacts can include a phone number for urgent matters, and a Teams channel carries managed response updates.
- Microsoft Learn states a 1,500-seat minimum for Plan 2 and gives no minimum for Plan 1; eligibility terms sit in the Microsoft Product Terms, which the evaluation confirms with Microsoft.

Cons:
- Covers Microsoft Defender workloads only, and only High and Medium severity incidents on Windows, Linux, and macOS devices: Microsoft's FAQ places custom detection, data loss prevention, and compliance incidents, and incidents on iOS or Android devices, outside the service, so Fabrikam's own R-01 custom detections (document 08, action 08.12) stay with the internal on-call. The finance system, code hosting, and the product cloud also stay outside it.
- "Neither plan is an incident response engagement." Response to an active compromise is a separate Microsoft service (Microsoft Defender Experts Cybersecurity Incident Response) or another firm.
- One-click managed actions are isolate device, quarantine file, restrict app execution, their reversals, and disable user; other steps arrive as guidance Fabrikam must carry out, so the internal on-call still matters. Microsoft says the service "augments your security operations center (SOC) rather than replacing it".
- A dedicated security delivery expert comes only at 1,500 or more seats or with cloud workloads.
- Case tickets and analyst notes are stored in Microsoft data centers worldwide for customers outside the EU Data Boundary and the government offering; General Counsel checks this against customer contracts.
- Delivered in English only, which suits Fabrikam.

### Option B: An independent MDR provider working in Defender XDR

Pros:
- Can bundle incident response hours and forensic support into the same contract.
- Can often bring non-Microsoft sources that matter to Fabrikam (finance system, code hosting, product cloud audit logs) into its own platform.
- Custom runbooks, a named analyst team, and reporting shaped to Fabrikam.

Cons:
- Quality varies widely; some services mostly forward alerts rather than investigate and contain.
- Fabrikam must design, grant, and review delegated access (least-privilege roles in Defender XDR unified role-based access control, MFA, Conditional Access), ideally on the pattern Microsoft documents for its own service.
- A provider platform that copies telemetry out of Microsoft 365 adds data handling, subprocessor, and assurance review (the provider's own SOC 2 report under CC9.2 and POL-10).
- Exit and data return need contract work.
- It needs the same Plan 2-level licenses to see endpoint and email detail.

### Option C: In-house round-the-clock SOC (rejected)

Pros: full control and deep knowledge of Fabrikam's business.

Cons: covering 168 hours a week, with leave, sickness, and turnover, takes roughly five or more analysts for a single seat, plus a lead. Fabrikam has no security staff today and plans one Security Engineer. Hiring, training, tooling, and retention would take longer than the plan year and cost far more than a managed service, and the knowledge would sit with a few people (R-14).

Rejected because it is out of proportion to a company of about 450 people.

### Option D: Business-hours internal coverage only (rejected)

Pros: no new spend; simple to run.

Cons: nights, weekends, holidays, and the year-end payroll peak stay uncovered, so an attack that starts on a Friday evening runs until Monday. It fails R-10 and the threat profile's top priorities.

Rejected because it leaves R-10 untreated.

Not an option: Defender Experts MDR Plan 2, which requires Microsoft Sentinel and a seat minimum above Fabrikam's size.

## Decision

Fabrikam will use a managed detection and response provider that works inside Microsoft Defender XDR, monitors around the clock, and contains threats inside a response authority matrix the executive team approves. Fabrikam will not build an in-house round-the-clock SOC and will not stay with business-hours coverage.

Defender Experts MDR Plan 1 is the reference option. In Phases 2 and 3 the Director scores it against at least two independent providers using the evaluation criteria below and brings a recommendation to the executive team at M3, together with the licensing decision in [ADR-001](ADR-001-microsoft-365-security-licensing.md). Plan 1 is preferred if it clears the minimum bar on every criterion, because it needs no separate access build and is run by the maker of the telemetry. An independent provider is chosen only if it scores materially higher, most likely on incident response surge or non-Microsoft coverage. For the year-end season before the MDR is live, an incident response retainer, or pre-agreed emergency terms with an incident response firm, is in place before mid-December with the CFO's approval; it folds into the MDR contract only if the chosen provider includes incident response, and otherwise stays beside it; with Defender Experts MDR, which excludes incident response, it stays a separate retainer (document 08, action 08.06).

The decision depends on ADR-001 funding Plan 2-level coverage for all users. ADR-001's chosen option, Microsoft Defender Suite on E3 for all users from Phase 4, does that if the executive team approves it at M3. Partial licensing does not work here: Microsoft sells its hunting service only at the tenant level, and an MDR cannot investigate users or devices it cannot see.

### Evaluation criteria for the provider choice

Weights are proposals. A provider that cannot contain inside Fabrikam's response authority matrix at night, or cannot export its case records, is out regardless of score.

| Criterion | Weight | What good looks like |
|---|---|---|
| Coverage of Fabrikam's top risks in Microsoft telemetry | 25% | Identity (Entra ID P2), email (Defender for Office 365 Plan 2), endpoint (Defender for Endpoint Plan 2), and cloud apps, including token theft, mailbox rule abuse, and business email compromise patterns; triage of Fabrikam's custom detections and of incidents on employees' phones, or a stated handoff to the on-call |
| Response authority and speed | 20% | Containment at any hour inside the matrix, call-first exclusions honored, phone escalation, committed acknowledgment and escalation times that support the KPI-16 target in document [12](../12-metrics-and-executive-reporting.md) |
| Native operation and access model | 15% | Works in Defender XDR with no extra agent; least-privilege, just-in-time access that Fabrikam can see in its logs and review |
| Incident response surge | 10% | Forensic and recovery hours included, or available on pre-agreed terms |
| Non-Microsoft coverage | 10% | A path to add the finance system, code hosting, or product cloud audit logs later |
| Reporting and evidence | 10% | Case records, monthly reports, and KPI-16 data usable as SOC 2 evidence and exportable |
| Commercials and exit | 10% | Clear cost drivers (per user or per device, term, surge rates), data return, no lock-in |

## Consequences

Positive:
- Round-the-clock monitoring and containment from the end of Phase 4, which treats the largest part of R-10.
- Faster containment, and KPI-16 measured from case data instead of estimates.
- The IT team spends its time on the build work in documents 06, 07, 13, and 15 instead of watching queues.
- Provider reports and incident records become evidence for CC7.2 to CC7.4.

Negative:
- A recurring service cost on top of the license uplift in ADR-001; document [04](../04-operating-model-team-and-budget.md) sizes the cost drivers.
- External analysts hold privileged access to Fabrikam's tenant, which must be governed and reviewed.
- Fabrikam still needs its on-call rotation and its decision makers; the provider hands back actions it cannot or must not take.
- Product platform monitoring stays with Engineering under the RACI in document 04.

## Risks and mitigations

| Risk | Mitigation |
|---|---|
| ADR-001 does not fund Plan 2-level licenses | The MDR cannot work meaningfully; the interim on-call model in document 08 continues and the residual R-10 goes to its executive owner (document [11](../11-risk-management.md)) |
| Cutover inside the current SOC 2 period (ends month 5) disturbs evidence | Agree the monitoring evidence with the SOC 2 audit firm before go-live; run in parallel with the internal on-call; move the cutover past M4 if the audit firm asks |
| Containment disrupts payroll or finance, for example disabling an integration account during a run | Call-first groups; the payroll calendar shared with the provider; reversible actions only inside the matrix |
| The provider under-performs or forwards alerts without acting | Contractual times, a monthly service review, the KPI-16 trend at the Quarterly Risk Review, and an exit clause |
| Case data is stored in places customer contracts do not allow | General Counsel reviews the provider's data terms against the contract clause inventory; the provider's assurance reports are reviewed under POL-10 |
| The MDR is mistaken for incident response | An incident response retainer, or pre-agreed emergency terms with an incident response firm, in place before mid-December with the CFO's approval; it folds into the MDR contract only if the chosen provider includes incident response, and otherwise stays beside it; the playbooks name who does what |
| Provider access is misused or left in place after exit | Least-privilege roles, sign-in monitoring of provider access, review at each service review, and removal on exit |

## Revisit when

- Fabrikam's licensed seats approach 1,500 and it adopts Microsoft Sentinel, the two conditions Microsoft sets for Plan 2.
- A SEV-1 incident shows the provider missed an agreed escalation or containment time.
- The contract comes up for renewal; the first review is at M7 (month 12).
- Engineering asks to bring product cloud telemetry under the same service.
- An acquisition adds another Microsoft 365 tenant.

## Related documents

- [08. Detection and incident response](../08-detection-and-incident-response.md): operating model, response authority matrix, severity, and the MDR onboarding actions (08.06, 08.08, 08.10).
- [ADR-001](ADR-001-microsoft-365-security-licensing.md): the licensing this decision depends on.
- [ADR-004](ADR-004-phishing-resistant-authentication-rollout.md) and [ADR-006](ADR-006-microsoft-365-backup.md): controls that reduce what the MDR has to catch and recover.
- Documents [04](../04-operating-model-team-and-budget.md) (partners, RACI, cost drivers), [06](../06-microsoft-365-security-baseline.md) (logging baseline), [11](../11-risk-management.md) (R-10), [12](../12-metrics-and-executive-reporting.md) (KPI-16), and [17](../17-threat-profile.md) (threats).
- [Payroll diversion and email compromise playbook](../playbooks/payroll-diversion-and-email-compromise.md).

## Sources

- What is Microsoft Defender Experts MDR? Microsoft Learn. https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-overview . Checked 2026-10-13. Primary.
- FAQs related to Microsoft Defender Experts MDR (incident scope by severity, platform, and category). Microsoft Learn. https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-faq . Checked 2026-10-13. Primary.
- Before you begin using the Microsoft Defender Experts MDR service. Microsoft Learn. https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-prerequisites . Checked 2026-10-13. Primary.
- Get started with Microsoft Defender Experts MDR. Microsoft Learn. https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-get-started . Checked 2026-10-13. Primary.
- How Microsoft Defender Experts permissions work. Microsoft Learn. https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-permissions . Checked 2026-10-13. Primary.
- Microsoft Defender Experts MDR managed detection and response. Microsoft Learn. https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-managed-response . Checked 2026-10-13. Primary.
- Before you begin using the Microsoft Defender Experts Hunting service. Microsoft Learn. https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-hunting-prerequisites . Checked 2026-10-13. Primary.
- Microsoft Defender XDR prerequisites. Microsoft Learn. https://learn.microsoft.com/en-us/defender-xdr/prerequisites . Checked 2026-10-13. Primary.
- Configure automatic attack disruption in Microsoft Defender XDR. Microsoft Learn. https://learn.microsoft.com/en-us/defender-xdr/configure-attack-disruption . Checked 2026-10-13. Primary.
- Overview of Microsoft Defender for Endpoint Plan 1. Microsoft Learn. https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-plan-1 . Checked 2026-10-13. Primary.
- Incident Response Recommendations and Considerations for Cybersecurity Risk Management: A CSF 2.0 Community Profile (NIST SP 800-61 Rev. 3). NIST. https://csrc.nist.gov/pubs/sp/800/61/r3/final . Checked 2026-10-13. Primary.
