# Fabrikam, Inc. (fictional): a first-year IT and security plan

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

How an incoming Director of IT and Security would run the first year of internal IT and security at Fabrikam, Inc. (fictional), a workforce software company of about 450 people on Microsoft 365 with no dedicated security staff. The role covers the company's own IT and security: employee technology, enterprise systems, the help desk, security, and the SOC 2 program. The product platform Fabrikam sells, and its security, availability, and recovery, are owned by Engineering and are out of scope here. The plan covers IT operations and security together, in five phases from November 2026 to October 2027, with dated milestones and a one-page monthly scorecard of key performance indicators (KPIs) the executive team can hold it to. Its top priorities: phishing-resistant identity and protecting the company's own staff and finance from business email compromise, detect and contain incidents at any hour, run the SOC 2 program and keep the report without a gap, let the HR record drive who has access, make corporate data recoverable, and consolidate the systems left by two acquisitions. Every plan document cites its sources, with the date each was checked.

**Start here:** the [executive summary](docs/00-executive-summary.md) gives the situation, the top five priorities, and the decisions the executive team is asked to make. IT and security leaders can go straight to the [judgment calls](#for-it-and-security-leaders).

**AI-assisted.**

## The scenario

Fabrikam, Inc. (fictional) is a privately held, remote-first US software company of about 450 people. It sells a cloud workforce platform (recruiting, onboarding, HR, payroll, benefits, and time tracking) to several thousand employers with hourly workforces. Engineering owns that product platform and its security, availability, and recovery; the Director's remit is the company's own internal IT and security. Two acquisitions left duplicate identities, devices, file storage, and cloud applications. On day 1, IT is an operations manager and three generalists running a lightly configured Microsoft 365 E3, with no dedicated security staff. Fabrikam holds a SOC 2 Type II report its customers rely on, whose current review period ends in March 2027; the Director runs the company-wide SOC 2 program and its corporate controls, while Engineering owns the product controls. It has chosen the NIST Cybersecurity Framework (CSF) 2.0 as its framework but has no formal risk register, and its policies are out of date. The Director reports to the chief technology officer (CTO), and the executive team approves the plan, the budget, and policies.

The full scenario and the 12 day-1 assumptions, with how each is verified, are in [document 01](docs/01-scenario-and-assumptions.md).

## The year at a glance

Day 1 is Monday, 2026-11-02. Customer-facing changes freeze from mid-December through January 31, during year-end payroll and tax form season, while internal IT changes continue with care. [Document 03](docs/03-twelve-month-roadmap.md) charts the year by workstream. Every date is a proposal.

| Phase | Name | Window | Calendar |
|---|---|---|---|
| Phase 1 | Listen and learn | Days 1 to 30 | November 2026 |
| Phase 2 | Stabilize | Days 31 to 60 | December 2026 |
| Phase 3 | Commit | Days 61 to 90 | January 2027 |
| Phase 4 | Build | Months 4 to 6 | February to April 2027 |
| Phase 5 | Scale and sustain | Months 7 to 12 | May to October 2027 |

| ID | When | Milestone |
|---|---|---|
| M1 | Day 30 (2026-12-01) | Listening report and environment baseline: inventories v1, KPI baselines, top risks draft |
| M2 | Day 60 (2026-12-31) | Stabilization quick wins done; risk register v1; current SOC 2 period on track |
| M3 | Day 90 (executive team meeting, Thursday 2027-01-28) | The executive team approves the 12-month plan, budget, policy set, and NIST CSF 2.0 current and target Profiles |
| D120 | Friday 2027-02-26 | Day 120 readout: KPIs against their Phase 1 baselines, early Phase 4 actions under way, and what is at risk |
| M4 | Month 5 (end of March 2027) | The current SOC 2 review period closes with no new audit exceptions from the Director's changes, and the next period starts without a gap |
| M5 | Month 9 (July 2027) | Acquisition systems consolidated: one identity per person, duplicate tools retired |
| M6 | Month 9 (July 2027) | Identity lifecycle automation live for all employees; phishing-resistant multifactor authentication (MFA) for all admins and most users |
| M7 | Month 12 (October 2027) | First annual program review: KPIs against targets, re-baselined risks, next-year plan |

## Suggested reading paths

### For executives

Start with 1; 2 and 3 add the detail behind it.

1. [00. Executive summary](docs/00-executive-summary.md): the situation, the top five priorities, and the decisions requested.
2. [02. The first 90 days](docs/02-first-90-days.md): what changes before the year-end freeze, and the readouts at days 30, 60, 90, and 120.
3. [04. Operating model, team, and budget](docs/04-operating-model-team-and-budget.md): who does what, and the budget by category and relative size.

Then, as needed: the [twelve-month roadmap](docs/03-twelve-month-roadmap.md), [metrics and executive reporting](docs/12-metrics-and-executive-reporting.md), the one-page [monthly scorecard](docs/templates/monthly-executive-scorecard.md), a filled-in [Quarterly Risk Review sample](docs/templates/quarterly-risk-review-sample.md) (every number illustrative), and the 90-minute [executive tabletop on payroll diversion](docs/templates/tabletop-payroll-diversion.md).

### For IT and security leaders

A suggested order; each row is a judgment call the linked document makes.

| # | Read | What it shows |
|---|---|---|
| 1 | [10, section 3.2](docs/10-governance-and-compliance-program.md#32-protecting-the-current-period-to-m4) | Protects the SOC 2 review period already under way: no change that would break its evidence without the audit firm's agreement, the urgent Phase 1 fixes disclosed to the firm in week 1, and redesigned controls started with the next period on 2027-04-01 where possible, so each period tests one design |
| 2 | [02, ground rules](docs/02-first-90-days.md#ground-rules-for-all-90-days) | Sequences around the year-end payroll freeze: changes customers would notice land before mid-December or after January 31, and finance and payroll staff get no new sign-in or device enforcement until February, while legacy protocols and device code sign-in are blocked for them before the freeze |
| 3 | [06, email authentication](docs/06-microsoft-365-security-baseline.md#email-authentication-dmarc-dkim-and-spf) | Moves DMARC from monitoring only (p=none, with reports nobody reads) to full enforcement (p=reject) in steps: reporting on every sending domain, a sender inventory and DKIM signing, third-party senders aligned, then enforcement domain by domain after the freeze. Every sending service has a named owner, the finish line also requires no unknown sender in the monthly report, and the section says what enforcement does not stop |
| 4 | [ADR-001](docs/adr/ADR-001-microsoft-365-security-licensing.md) | Configures what Microsoft 365 E3 already includes before buying more, then proposes Microsoft Defender Suite for all users and Microsoft Entra ID Governance from Phase 4, keeps a named fallback if the executive team declines, and rejects Microsoft 365 E7 for now |
| 5 | [ADR-003](docs/adr/ADR-003-managed-detection-and-response.md) | Chooses an MDR provider over an in-house round-the-clock security operations center (SOC) or business-hours coverage, and scores Microsoft's Defender Experts MDR Plan 1 against at least two independent providers on weighted criteria. Because no MDR is live until the end of April, an incident response retainer, or pre-agreed emergency terms, is in place before mid-December; it stays beside the MDR contract unless the chosen provider includes incident response, which Microsoft states neither Defender Experts plan does |
| 6 | [07, identity verification](docs/07-identity-lifecycle-joiners-movers-leavers.md#identity-verification-before-the-first-credential-r-15) and [ADR-002](docs/adr/ADR-002-hr-system-of-record-drives-identity.md) | Lets the HR record drive joiners, movers, and leavers, and treats a fraudulent remote hire as a named risk (R-15): each new account stays disabled until a trained People verifier checks the new hire on video against a government-issued ID and the HR record |
| 7 | [Payroll diversion playbook](docs/playbooks/payroll-diversion-and-email-compromise.md) and [tabletop](docs/templates/tabletop-payroll-diversion.md) | Makes a call to a known number the control that matters most, because lookalike domains and compromised partner mailboxes get past email authentication, and tests the executives' decisions (stopping a payment, a bank recall, a customer notice) in a 90-minute tabletop. Neither has been exercised |
| 8 | [11. Risk management](docs/11-risk-management.md) | States the scoring method first, drafts a risk appetite by area for executive approval, limits who may accept residual risk at each band (never the Director), names the controls that are not open to exception, and shows R-08 still above appetite at month 12 in the illustration |
| 9 | [ADR-004](docs/adr/ADR-004-phishing-resistant-authentication-rollout.md) | Rolls out phishing-resistant sign-in in risk-ordered waves around Microsoft's 2027-02-01 retirement of its own SMS and voice codes: the emergency access accounts on their own security keys in Phase 1, administrators in December, the highest-risk business roles registered before year-end and enforced in February, and everyone else in rings, most by M6. It rejects stopping at push with number matching, keeping SMS through a telephony provider, and security keys for every employee |
| 10 | [16, AI security overview](docs/16-ai-adoption-guardrails.md#ai-security-overview) | Sets out AI security in three layers: policy (the AI rules for people in the Acceptable Use Policy, and an AI security standard under the Information Security Policy rather than a new policy, both approved with the policy set at M3), guardrails for people and teams, and a register of controls tied to existing risks and measured by existing KPIs. It offers an approved tool, Copilot Chat signed in with the work account, before restricting unapproved ones, holds the Copilot pilot behind an oversharing readiness gate, and assumes some prompt injection gets through, so it limits what an assistant can reach and never lets an AI summary verify a payment or access change |
| 11 | [03, deferred to year two](docs/03-twelve-month-roadmap.md#deferred-to-year-two) | Shows where the first year stops: it defers a security information and event management system, any Processing Integrity, Privacy, or SOC 1 readiness (decided at M7), and the closing of R-08 to year two |

## What is here

| Area | Where | Contents |
|---|---|---|
| Executive set | [00](docs/00-executive-summary.md), [02](docs/02-first-90-days.md), [03](docs/03-twelve-month-roadmap.md), [04](docs/04-operating-model-team-and-budget.md), [12](docs/12-metrics-and-executive-reporting.md) | The executive summary and its decisions; the first 90 days and the Day 120 readout; the twelve-month roadmap; the operating model, team, and budget by relative size; and the 24 KPIs, the monthly scorecard, and the Quarterly Risk Review |
| Depth documents | [docs/](docs/): 01, 05 to 11, 13 to 17 | [01](docs/01-scenario-and-assumptions.md) scenario and assumptions; [05](docs/05-environment-discovery.md) environment discovery; [06](docs/06-microsoft-365-security-baseline.md) Microsoft 365 security baseline; [07](docs/07-identity-lifecycle-joiners-movers-leavers.md) identity lifecycle; [08](docs/08-detection-and-incident-response.md) detection and incident response; [09](docs/09-security-awareness-and-training.md) security awareness and training; [10](docs/10-governance-and-compliance-program.md) governance and compliance, with policies POL-01 to POL-15; [11](docs/11-risk-management.md) risk management, with the 13 risks R-01, R-03, and R-05 to R-15; [13](docs/13-it-service-management.md) IT service management; [14](docs/14-business-continuity-and-backup.md) business continuity and backup; [15](docs/15-enterprise-systems-and-saas.md) enterprise systems and software as a service (SaaS); [16](docs/16-ai-adoption-guardrails.md) AI security and adoption guardrails, with an AI security standard and a register of AI security controls; [17](docs/17-threat-profile.md) threat profile, mapped to MITRE ATT&CK v20. Each has numbered actions by phase, resourcing, risks and open questions, and a framework mapping |
| Architecture decision records | [docs/adr/](docs/adr/) (8) | ADR-001 Microsoft 365 security licensing; ADR-002 the HR system of record drives the identity lifecycle; ADR-003 managed detection and response (MDR); ADR-004 phishing-resistant authentication; ADR-005 acquired-company consolidation; ADR-006 Microsoft 365 backup; ADR-007 a compliance automation platform (category only, no vendor named); ADR-008 one endpoint management standard. Each is proposed, compares options, and names at least one rejected alternative |
| Playbook | [docs/playbooks/](docs/playbooks/payroll-diversion-and-email-compromise.md) | Payroll diversion and email compromise: triggers, first-hour actions, investigation in Microsoft Defender XDR, decision points, and an ATT&CK v20 mapping. An untested template |
| Templates | [docs/templates/](docs/templates/) (5) | A stakeholder conversation guide; joiner, mover, and leaver checklists; the monthly executive scorecard; an illustrative Quarterly Risk Review sample for month 6; and a 90-minute executive tabletop on payroll diversion (R-01) |
| Crosswalk | [docs/crosswalk/](docs/crosswalk/csf2-soc2-crosswalk.md) | NIST CSF 2.0 and SOC 2 in two views: each of the 22 CSF 2.0 Categories to the SOC 2 criteria in scope, and each criterion in scope (CC1.1 to CC9.2, A1.1 to A1.3, C1.1 to C1.2) to plan controls and documents, with a relationship strength on every row |
| Data | [data/](data/) (3 CSV files) | `kpi-catalog.csv`, the 24 KPIs with definitions, formulas, data sources, cadences, owners, and targets; `risk-register.csv`, the 13 risks with illustrative scores; `csf2-soc2-crosswalk.csv`, both crosswalk views in 133 rows |
| Queries | [queries/](queries/) (8 KQL files) | Microsoft Defender XDR advanced hunting queries q01 to q08 for KPI measurement, investigation, and later cross-checks of the day-1 assumptions: sign-ins that did not require MFA, legacy authentication, privileged role changes, external mail forwarding, app consent grants, stale accounts, remaining Windows 10 devices, and "Anyone" sharing links. All eight need licensing above Microsoft 365 E3, so they run from Phase 4 if Microsoft Defender Suite is approved; each header names an E3 alternative where one exists. Untested templates |

## Limitations

- **Fictional and untested.** Fabrikam is fictional, and nothing in the plan has been carried out or tested in any organization. The risk scores in document 11 and `data/risk-register.csv` are illustrative until the named owners rate their risks.
- **Proposals, not prescriptions.** Every cadence, target, threshold, and timeline is a proposal for Fabrikam to tune after discovery, as [document 01](docs/01-scenario-and-assumptions.md) states once for the whole repository.
- **Internal IT and security only.** The Director's scope is the company's own IT and security: employee technology, enterprise systems, the help desk, security, and the SOC 2 program. The product platform Fabrikam sells, and its security, availability, recovery, and product AI, are owned by Engineering and are out of scope, described only where the two connect. The Director runs the company-wide SOC 2 program and its corporate controls, while Engineering owns the product controls under the RACI in [document 04](docs/04-operating-model-team-and-budget.md).
- **Time-sensitive facts carry check dates.** Sources were checked on 2026-10-13 or 2026-10-14, and each document's Sources section gives the dates. Microsoft's packaging, features, and dates can change after that, including the July 2026 additions to Microsoft 365 E3, the retirement of Microsoft-provided SMS and voice MFA on 2027-02-01 for most users (2027-07-01 for Global Administrators and external users), and anything labeled preview. The SMTP AUTH date rests on a secondary source and is rechecked before acting. MITRE released ATT&CK v20 on 2026-10-13; the mappings were checked against it on 2026-10-13 or 2026-10-14, and on 2026-10-14 Claude confirmed that every ATT&CK ID cited in the repository, and every technique or tactic name given with its ID, matches the ATT&CK v20.0 data.
- **The queries are untested templates.** None has been run against any tenant, workspace, or lab. Each header states the licensing it assumes, which Fabrikam has only if the executive team approves Microsoft Defender Suite at M3 ([ADR-001](docs/adr/ADR-001-microsoft-365-security-licensing.md)), and three read a sign-in table that Microsoft lists as preview (as of 2026-10-13). The only checks so far are static: on 2026-10-14 Claude confirmed that all eight parse and pass analysis with Microsoft's Kusto language library against table schemas built from Microsoft Learn's reference pages, with no errors or warnings.
- **The crosswalk is an analysis, not an official mapping.** Its relationship strengths are the author's analysis of the published texts. No official AICPA mapping between the Trust Services Criteria and CSF 2.0 was found, and because AICPA's mappings page is for members only, the absence is not proven. The crosswalk is not an audit or an attestation.
- **Legal readings are questions for counsel.** The plan names legal questions for Fabrikam's General Counsel and does not answer them, and statutes and regulations are cited as read on 2026-10-13 or 2026-10-14. Nothing here is legal advice.
- **No dollar figures, by design.** Costs appear as categories, cost drivers, and relative size, and quotes come at decision time.
- **The sample numbers are illustrative.** Every number, rating, status, event date, and finding about Fabrikam in the Quarterly Risk Review sample is invented to show the format; none is a measured result.

## License

- **Code: [MIT License](LICENSE)** for the KQL queries (`queries/*.kql`).
- **Documents and data: [CC BY 4.0](LICENSE-docs)** for the Markdown documents, including this README, and the CSV files in `data/`.

Copyright 2026 Jacob Welch. Both licenses allow reuse and adaptation with credit, and both cover original content only. Third-party names, identifiers, and quoted material stay under their owners' terms, as [NOTICE.md](NOTICE.md) records.

## Author

**Jacob Welch.** 17+ years in IT and systems administration, including regulated healthcare and financial services. Current role: Associate Director of Security and Compliance. [LinkedIn](https://www.linkedin.com/in/jacobwelch21)

The parts of this plan closest to his own experience are Conditional Access and Privileged Identity Management in Microsoft Entra, SOC 2 Type II audits, customer security reviews, email authentication (SPF, DKIM, and DMARC), disaster recovery testing, and security awareness training. Like the rest of the repository, those parts were written for the fictional scenario from public sources and contain no employer information.

The plan deliberately reaches beyond his hands-on experience into areas such as managed detection and response, identity lifecycle automation with Microsoft Entra ID Governance, and NIST CSF 2.0 Organizational Profiles; those parts are design and analysis work.

Certifications:

- Certified Information Security Manager (CISM), ISACA
- Microsoft Certified: Cybersecurity Architect Expert (SC-100)
- Microsoft Certified: Security Operations Analyst Associate (SC-200)
- Microsoft Certified: Identity and Access Administrator Associate (SC-300)
- Microsoft Certified: Azure Security Engineer Associate (AZ-500)
- Microsoft 365 Certified: Administrator Expert
- CompTIA Security+ ce
- ITIL 4 Foundation in IT Service Management
