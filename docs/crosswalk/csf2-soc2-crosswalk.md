# NIST CSF 2.0 and SOC 2 crosswalk

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

## Purpose and scope

This crosswalk relates the NIST Cybersecurity Framework (CSF) 2.0 Core, Fabrikam's (fictional) hub framework, to the SOC 2 Trust Services Criteria in Fabrikam's report scope (Security, Availability, and Confidentiality), and shows where the plan addresses each. View A starts from each of the 22 CSF 2.0 Categories; View B starts from each in-scope criterion, CC1.1 to CC9.2, A1.1 to A1.3, and C1.1 to C1.2. It is a reference mapping for planning, not an audit, an attestation, or an official mapping, and it does not change what the SOC 2 audit firm tests. The same rows are in [csf2-soc2-crosswalk.csv](../../data/csf2-soc2-crosswalk.csv).

## Read this first

- **No official mapping was found.** No AICPA mapping between the Trust Services Criteria and CSF 2.0 was found. AICPA's "Mapping: 2017 Trust Services Criteria to NIST CSF" is dated May 4, 2018, includes March 2020 updates, and does not say which CSF version it maps; it predates CSF 2.0 (February 26, 2024). AICPA's wider mappings page is reserved for members, so the absence is not proven. NIST's CSF 2.0 Informative References page, as read on 2026-10-13, lists no Trust Services Criteria mapping. A crosswalk that NIST hosts between the 2017 criteria and the NIST Privacy Framework is a community contribution and maps the Privacy Framework, not the CSF.
- **This is the author's analysis.** Every relationship and strength below is this plan's own judgment, made for Fabrikam's planning.
- **Versions.** NIST CSF 2.0 (CSWP 29, February 26, 2024): 6 Functions, 22 Categories, and 106 Subcategories (count of Appendix A). AICPA 2017 Trust Services Criteria with revised points of focus (2022); the 2022 revision changed the points of focus, not the criteria.
- **Copyright.** AICPA criteria appear by identifier with original paraphrases; no AICPA text is reproduced and no point of focus is quoted. CSF descriptions paraphrase NIST's public text, checked against CSWP 29 Appendix A.
- **Theme rows elsewhere.** The Framework mapping tables in other documents group identifiers by theme. A theme row does not claim that every listed Subcategory relates to every listed criterion; the pairs that do relate are here.

## Relationship strengths

| Strength | Meaning in this crosswalk |
|---|---|
| equivalent | The two address substantially the same objective at about the same scope. Even then, evidence for one does not automatically satisfy the audit firm for the other |
| partial | Substantial overlap, but one side is broader or adds requirements the other lacks |
| related | The same topic area; one supports the other without covering its objective |

View A compares a whole CSF Category with a criterion, so it rarely reaches "equivalent". View B names the closest Subcategories, where a pair can.

## Document key

| Key | Document |
|---|---|
| 01 | [Scenario and assumptions](../01-scenario-and-assumptions.md) |
| 04 | [Operating model, team, and budget](../04-operating-model-team-and-budget.md) |
| 05 | [Environment discovery](../05-environment-discovery.md) |
| 06 | [Microsoft 365 security baseline](../06-microsoft-365-security-baseline.md) |
| 07 | [Identity lifecycle: joiners, movers, and leavers](../07-identity-lifecycle-joiners-movers-leavers.md) |
| 08 | [Detection and incident response](../08-detection-and-incident-response.md) |
| 09 | [Security awareness and training](../09-security-awareness-and-training.md) |
| 10 | [Governance and compliance program](../10-governance-and-compliance-program.md) |
| 11 | [Risk management](../11-risk-management.md) |
| 12 | [Metrics and executive reporting](../12-metrics-and-executive-reporting.md) |
| 13 | [IT service management](../13-it-service-management.md) |
| 14 | [Business continuity and backup](../14-business-continuity-and-backup.md) |
| 15 | [Enterprise systems and SaaS](../15-enterprise-systems-and-saas.md) |
| 16 | [AI security and adoption guardrails](../16-ai-adoption-guardrails.md) |
| 17 | [Threat profile](../17-threat-profile.md) |
| playbook | [Payroll diversion and email compromise playbook](../playbooks/payroll-diversion-and-email-compromise.md) |
| ADR-002 | [HR system of record drives identity](../adr/ADR-002-hr-system-of-record-drives-identity.md) |
| ADR-003 | [Managed detection and response](../adr/ADR-003-managed-detection-and-response.md) |
| ADR-004 | [Phishing-resistant authentication rollout](../adr/ADR-004-phishing-resistant-authentication-rollout.md) |
| ADR-006 | [Microsoft 365 backup](../adr/ADR-006-microsoft-365-backup.md) |
| ADR-007 | [Compliance automation platform](../adr/ADR-007-compliance-automation-platform.md) |
| ADR-008 | [Endpoint management standard](../adr/ADR-008-endpoint-management-standard.md) |

Action IDs such as 06.17 refer to the phase plan of the document with that number.

## View A: CSF 2.0 Categories to SOC 2 criteria

### Govern

| Category | What it covers (paraphrase) | SOC 2 criteria (strength) | Plan documents | KPIs | Rationale |
|---|---|---|---|---|---|
| GV.OC Organizational Context | The mission, stakeholder expectations, dependencies, and legal, regulatory, and contractual requirements behind cybersecurity risk decisions are understood | CC3.1 (partial); CC2.1 (related); CC2.3 (related) | 01, 05, 08, 10 | KPI-01 | GV.OC supplies the mission, commitments, and requirements that CC3.1's objectives are built from; it has no outcome on information quality or on communicating outside, so those pairs are related only |
| GV.RM Risk Management Strategy | Priorities, constraints, risk appetite and tolerance, and assumptions are set, communicated, and used for operational risk decisions | CC3.1 (partial); CC3.2 (related); CC3.4 (related); CC5.1 (related); CC9.1 (related) | 10, 11 | KPI-01 | Agreed risk objectives feed CC3.1; GV.RM sets the method and appetite, while the criteria expect them in use during assessment and control selection, which ID.RA and the risk register carry |
| GV.RR Roles, Responsibilities, and Authorities | Roles, responsibilities, and authorities that support accountability, performance assessment, and improvement are set and communicated | CC1.3 (partial); CC1.1 (partial); CC1.4 (partial); CC1.5 (partial); CC2.2 (related); CC6.2 (related) | 04, 07, 09, 10 | KPI-01, KPI-12, KPI-14 | The CC1 criteria cover the whole organization's structure, ethics, competence, and accountability, and GV.RR covers the cybersecurity share of each; GV.RR-04 (cybersecurity in HR practices) drives the joiner and leaver steps CC6.2 tests |
| GV.PO Policy | Cybersecurity policy is set, communicated, enforced, and kept current | CC5.3 (partial); CC2.2 (related); CC1.1 (related); CC1.3 (related) | 07, 08, 10 | KPI-02 | Both expect policy that is set, communicated, and enforced; CC5.3 adds the procedures that put policy into practice |
| GV.OV Oversight | Results of risk management activities and performance are used to inform and adjust the risk strategy | CC1.2 (partial); CC4.1 (partial); CC4.2 (partial) | 10, 11, 12 | KPI-01, KPI-03, KPI-04 | Senior review of strategy and performance overlaps board oversight and monitoring; CC1.2 also requires a board independent of management, which CSF does not address |
| GV.SC Cybersecurity Supply Chain Risk Management | Supply chain risk management processes are set up, managed, monitored, and improved | CC9.2 (partial); CC2.3 (related); CC6.2 (related) | 07, 08, 10, 15, ADR-003 | KPI-05 | GV.SC holds CC9.2's core (criticality, contracts, due diligence, monitoring, exit); GV.SC is broader, and CC9.2 treats business partners on the same footing as vendors |

### Identify

| Category | What it covers (paraphrase) | SOC 2 criteria (strength) | Plan documents | KPIs | Rationale |
|---|---|---|---|---|---|
| ID.AM Asset Management | Data, hardware, software, systems, facilities, services, and people are identified and managed by their importance and the risk strategy | C1.1 (partial); CC6.1 (related); CC2.1 (related); CC6.5 (related); C1.2 (related); CC9.2 (related) | 05, 06, 13, 15 | KPI-06, KPI-07 | Data inventories (ID.AM-07) are how confidential information is identified for C1.1; the other inventories support access control, information quality, disposal, and vendor management without covering them |
| ID.RA Risk Assessment | Cybersecurity risk to the organization, its assets, and individuals is understood | CC3.2 (partial); CC3.4 (partial); CC5.1 (partial); CC7.1 (partial); CC3.1 (related); CC3.3 (related); CC8.1 (related); CC9.2 (related) | 06, 11, 13, 17 | KPI-01, KPI-11 | Threat, likelihood, impact, and response outcomes cover most of CC3.2 and the inputs to CC5.1, and vulnerability identification covers half of CC7.1; CSF has no fraud-specific outcome, so CC3.3 is related only |
| ID.IM Improvement | Improvements to risk management processes and activities are identified across all Functions | CC4.1 (partial); CC4.2 (partial); A1.3 (related); CC7.5 (related); CC9.1 (related) | 08, 10, 12, 14 | KPI-04, KPI-18 | Evaluations, tests, and exercises that drive improvement match the monitoring criteria; ID.IM-02 only identifies improvements from tests, so it relates to the recovery testing in A1.3 without covering it; CC4.2 adds timely reporting of deficiencies to those who must fix them |

### Protect

| Category | What it covers (paraphrase) | SOC 2 criteria (strength) | Plan documents | KPIs | Rationale |
|---|---|---|---|---|---|
| PR.AA Identity Management, Authentication, and Access Control | Physical and logical access is limited to authorized users, services, and hardware and managed in line with the risk of unauthorized access | CC6.1 (partial); CC6.2 (partial); CC6.3 (partial); CC6.4 (partial); CC6.6 (related); CC5.2 (related); CC4.1 (related) | 06, 07, 13, ADR-002, ADR-004 | KPI-08, KPI-09, KPI-12, KPI-13 | The Category spans logical and physical access, so each criterion matches only part of it; at Subcategory level PR.AA-05 with CC6.3, and PR.AA-06 with CC6.4, are equivalent (View B) |
| PR.AT Awareness and Training | Personnel receive awareness and training to perform their cybersecurity-related tasks | CC1.4 (partial); CC2.2 (partial) | 09, 16 | KPI-14, KPI-15 | Training builds competence and communicates responsibilities; CC1.4 also covers hiring and retention, and CC2.2 covers all internal control communication |
| PR.DS Data Security | Data is managed to protect its confidentiality, integrity, and availability in line with the risk strategy | CC6.7 (partial); C1.1 (partial); A1.2 (partial); A1.3 (partial); CC6.1 (related); C1.2 (related); CC6.6 (related); CC6.8 (related) | 06, 14, 16, ADR-006 | KPI-17, KPI-19 | Protection at rest and in transit overlaps CC6.7 and C1.1, and backups that are created, protected, maintained, and tested (PR.DS-11) are part of A1.2 and of the testing in A1.3; CC6.7 adds limits on who may move data, and disposal (C1.2) sits with ID.AM-08 |
| PR.PS Platform Security | Hardware, software, and services of physical and virtual platforms are managed in line with the risk strategy | CC8.1 (partial); CC7.1 (partial); CC6.8 (partial); CC5.2 (related); CC7.2 (related); CC6.1 (related) | 06, 13, ADR-008 | KPI-10, KPI-11, KPI-24 | Configuration, maintenance, secure development, logging, and software control overlap change management, vulnerability detection, and malware prevention; CSF has no single controlled-change outcome |
| PR.IR Technology Infrastructure Resilience | Security architectures protect asset confidentiality, integrity, and availability, and organizational resilience | CC6.6 (partial); A1.1 (partial); A1.2 (partial); CC6.1 (related); CC9.1 (related) | 06, 14 | KPI-19 | Network protection matches the boundary concern of CC6.6, capacity (PR.IR-04) matches A1.1 (equivalent at Subcategory level), and environmental and resilience mechanisms are part of A1.2 |

### Detect

| Category | What it covers (paraphrase) | SOC 2 criteria (strength) | Plan documents | KPIs | Rationale |
|---|---|---|---|---|---|
| DE.CM Continuous Monitoring | Assets are monitored to find anomalies, indicators of compromise, and other potentially adverse events | CC7.2 (partial); CC7.1 (partial); CC6.8 (related); CC6.4 (related); CC6.6 (related); CC7.3 (related); CC9.2 (related) | 06, 08, ADR-003 | KPI-16 | Monitoring networks, personnel activity, computing, and service providers covers most of CC7.2; CC7.2 also names natural disasters and errors as anomalies |
| DE.AE Adverse Event Analysis | Anomalies and other potentially adverse events are analyzed to characterize them and detect incidents | CC7.3 (partial); CC7.2 (partial) | 08 | KPI-16, KPI-17 | Analysis, impact estimation, and declaration against criteria match the evaluation step in CC7.3, which also expects action on the result |

### Respond

| Category | What it covers (paraphrase) | SOC 2 criteria (strength) | Plan documents | KPIs | Rationale |
|---|---|---|---|---|---|
| RS.MA Incident Management | Responses to detected incidents are managed | CC7.4 (partial); CC7.3 (related); CC7.5 (related) | 08, playbook | KPI-16, KPI-17 | Executing the plan, triage, prioritization, and escalation are the management part of the response program in CC7.4 |
| RS.AN Incident Analysis | Investigations support effective response, forensics, and recovery | CC7.4 (partial); CC7.3 (related) | 08, playbook | KPI-16 | Root cause and magnitude analysis are part of understanding incidents within CC7.4 |
| RS.CO Incident Response Reporting and Communication | Response activities are coordinated with internal and external stakeholders as laws, regulations, or policies require | CC7.4 (partial); CC2.3 (partial); CC2.2 (related) | 08, 10, playbook | KPI-18 | Notifying and sharing with stakeholders is part of CC7.4 and a large share of the external communication in CC2.3 |
| RS.MI Incident Mitigation | Activities prevent an event from expanding and reduce its effects | CC7.4 (partial) | 08, ADR-003 | KPI-16 | Containment and eradication are the remediation part of CC7.4 |

### Recover

| Category | What it covers (paraphrase) | SOC 2 criteria (strength) | Plan documents | KPIs | Rationale |
|---|---|---|---|---|---|
| RC.RP Incident Recovery Plan Execution | Restoration activities make affected systems and services available again | CC7.5 (partial); A1.2 (related); A1.3 (related) | 08, 14, ADR-006 | KPI-18, KPI-19 | Executing recovery, verifying restoration assets, and declaring the end of recovery match CC7.5; A1.2 and A1.3 cover the infrastructure and testing that recovery depends on |
| RC.CO Incident Recovery Communication | Restoration activities are coordinated with internal and external parties | CC2.3 (related); CC7.4 (related); CC7.5 (related) | 08, 14 | KPI-18 | Recovery updates to outside stakeholders are one narrow kind of the external communication under CC2.3 and continue the incident communication in CC7.4 |

## View B: SOC 2 criteria to plan controls

"Strength" here is the relationship between the criterion and the CSF 2.0 Subcategories listed. Plan controls name the action IDs and controls that address the criterion at Fabrikam.

### CC1 Control environment

| Criterion | Paraphrase | Closest CSF 2.0 Subcategories | Strength | Plan controls | Documents | KPIs | Rationale |
|---|---|---|---|---|---|---|---|
| CC1.1 | Leaders set and uphold standards of integrity and ethical conduct | GV.RR-01, GV.PO-01 | partial | POL-02 accepted at first sign-in (07) and with training (09); POL-01 and POL-14 approved by the executive team (10.14) | 07, 09, 10 | KPI-02, KPI-14 | GV.RR-01 asks leadership to foster an ethical, risk-aware culture; CC1.1 covers integrity and ethics in all conduct, not only cybersecurity |
| CC1.2 | Directors independent of management oversee how internal control is built and how well it works | GV.OV-01, GV.OV-02 | partial | Quarterly Risk Review (10.03); material the Director prepares for the CEO, who decides what reaches the investor board | 10, 11, 12 | KPI-01 | Both concern oversight of how the program performs; CC1.2 places that oversight with a board independent of management, which CSF does not address and the plan cannot create |
| CC1.3 | Management, overseen by the board, sets the structure, reporting lines, authorities, and responsibilities | GV.RR-02 | partial | Forums and decision rights (10.03); RACI with Engineering (04); control owners by role (10.01, 10.16) | 04, 10 | KPI-01 | GV.RR-02 covers cybersecurity roles and authorities; CC1.3 covers the whole organization's structure |
| CC1.4 | The organization hires, develops, and keeps people with the skills its objectives need | GV.RR-04, PR.AT-01, PR.AT-02 | partial | Team hiring sequence (04); role-based training (09.10, 09.12); POL-14 screening and onboarding duties (10.14) | 04, 09, 10 | KPI-14 | CSF covers cybersecurity in HR practices and training; CC1.4 covers hiring, development, and retention generally |
| CC1.5 | People answer for the internal control duties assigned to them | GV.RR-02, GV.RR-04 | partial | Named control owners with KPIs (10.01); POL-14 consequences for policy breaches; KPI reporting to the Steering Group (12.03) | 10, 12 | KPI-03, KPI-13 | Enforced roles and HR practices create accountability; CC1.5 also covers performance measures and incentives (a COSO point of focus) |

### CC2 Communication and information

| Criterion | Paraphrase | Closest CSF 2.0 Subcategories | Strength | Plan controls | Documents | KPIs | Rationale |
|---|---|---|---|---|---|---|---|
| CC2.1 | Relevant, reliable information is obtained or produced and used to run internal control | ID.AM-01, ID.AM-02, ID.AM-03, ID.AM-07, GV.OC-05 | related | Inventories v1 (05.05 to 05.08, 05.11); complete populations exported from systems of record (10.09); KPI data quality notes (05.10) | 05, 10, 12 | KPI-06, KPI-07 | CSF supplies inventories and dependency information as inputs but has no outcome about information quality for internal control |
| CC2.2 | Objectives and internal control responsibilities are communicated inside the organization | GV.PO-01, GV.RR-02, PR.AT-01 | partial | Policy publication and acceptance (10.14); training (09); incident roles (08.05, 08.08) | 08, 09, 10 | KPI-02, KPI-14 | Policies, roles, and awareness carry most internal communication; CC2.2 covers all internal control information |
| CC2.3 | Matters that affect internal control are communicated with outside parties | GV.OC-03, GV.SC-02, RS.CO-02, RS.CO-03, RC.CO-03 | partial | Assurance request process and bridge letters (10.11, 10.21); CUEC communication (10); contract clause inventory and notification path (08.04, 08.08); vendor contract clauses (10.17) | 08, 10 | KPI-05 | CSF covers requirements, supplier and customer roles, and incident communication; CC2.3 covers all external communication about internal control, including customer commitments |

### CC3 Risk assessment

| Criterion | Paraphrase | Closest CSF 2.0 Subcategories | Strength | Plan controls | Documents | KPIs | Rationale |
|---|---|---|---|---|---|---|---|
| CC3.1 | Objectives are defined clearly enough to find and assess the risks to them | GV.OC-01, GV.OC-03, GV.OC-04, GV.RM-01 | partial | Target Profile (10.13); service commitments from the clause inventory (08.04); risk appetite (11.06) | 08, 10, 11 | KPI-01 | Mission, requirements, and agreed risk objectives give CC3.1 its clarity; CC3.1 also covers objectives beyond cybersecurity |
| CC3.2 | Risks to objectives are found across the organization and analyzed to decide how to manage them | ID.RA-03, ID.RA-04, ID.RA-05, GV.RM-06 | partial | Risk register R-01 to R-15 with a stated scoring method (11.01, 11.03); threat profile (17.01, 17.02) | 11, 17 | KPI-01 | Threats, likelihood, impact, and a standard method cover the analysis; CC3.2 covers all risks to objectives, not only cybersecurity |
| CC3.3 | The potential for fraud is part of the risk assessment | ID.RA-03 | related | R-01 and R-02 treatments (11.07); out-of-band bank-detail checks (playbook); separation of duties between bank-detail maintenance and payment approval (07); executive tabletop (08.09) | 07, 08, 11, playbook | KPI-01, KPI-18 | CSF has no fraud-specific outcome; the plan treats payroll and payment fraud explicitly instead |
| CC3.4 | Significant changes that could affect internal control are spotted and assessed | ID.RA-07 | partial | In-period SOC 2 change protocol (10.02); Change Advisory Board (13.02, 13.19); legal questions log (10.05); acquired product line scope change (10.19, 10.23) | 10, 13 | KPI-24, KPI-03 | Both cover assessing changes for their effect; CC3.4 also includes changes in the business, leadership, and environment (COSO points of focus) |

### CC4 Monitoring activities

| Criterion | Paraphrase | Closest CSF 2.0 Subcategories | Strength | Plan controls | Documents | KPIs | Rationale |
|---|---|---|---|---|---|---|---|
| CC4.1 | Ongoing checks and separate evaluations confirm that internal control is in place and working | ID.IM-01, GV.OV-03, PR.AA-05 | partial | Platform control tests and quarterly sampling (ADR-007, 10.20); access reviews (07.06, 07.14, 07.19); Secure Score and Entra recommendations as review inputs, not evidence (06.35); Profile reassessment (10.28) | 06, 07, 10, ADR-007 | KPI-03, KPI-13 | Evaluations, performance reviews, and access reviews are forms of monitoring; CC4.1 requires evaluation of every internal control component |
| CC4.2 | Control deficiencies are assessed and reported promptly to the people who must fix them, up to senior management and the board when warranted | ID.IM-01, GV.OV-03 | partial | Exception tracking with owners and dates (10.25); Steering Group; Quarterly Risk Review | 10, 11, 12 | KPI-04 | Improvements and performance reviews correspond to deficiencies; CC4.2 adds timely reporting to the people who must act |

### CC5 Control activities

| Criterion | Paraphrase | Closest CSF 2.0 Subcategories | Strength | Plan controls | Documents | KPIs | Rationale |
|---|---|---|---|---|---|---|---|
| CC5.1 | Control activities are designed to bring risks down to acceptable levels | GV.RM-02, ID.RA-06 | partial | Risk treatment plans (11.07); Target Profile gap actions (10.13); the Microsoft 365 baseline (06) | 06, 10, 11 | KPI-01 | Appetite and chosen risk responses drive control selection; CC5.1 covers control activities for all objectives |
| CC5.2 | General controls over technology are designed to support objectives | PR.PS-01, PR.AA-05 | related | Microsoft 365 baseline (06); identity lifecycle (07); change control (13) | 06, 07, 13 | KPI-10, KPI-24 | Configuration and access outcomes are examples of general technology controls; CC5.2 is about selecting such controls |
| CC5.3 | Policies say what is expected, and procedures put it into practice | GV.PO-01, GV.PO-02 | partial | POL-01 to POL-15 (10.08, 10.14); procedures in documents 06, 07, 08, 13, 14, and 15 | 10 | KPI-02 | Both cover policy that is set, communicated, enforced, and reviewed; CC5.3 adds procedures |

### CC6 Logical and physical access

| Criterion | Paraphrase | Closest CSF 2.0 Subcategories | Strength | Plan controls | Documents | KPIs | Rationale |
|---|---|---|---|---|---|---|---|
| CC6.1 | Information assets are protected by logical access controls built into software, infrastructure, and architecture | PR.AA-01, PR.AA-03, PR.AA-05, PR.IR-01, PR.DS-01, ID.AM-01, ID.AM-02 | partial | Conditional Access CA-01 to CA-15 and phishing-resistant MFA (06.09, 06.24, 06.32; ADR-004); privileged access (06.03, 06.25); device compliance and encryption (06.17); app consent limits (06.12) | 06, ADR-004 | KPI-08, KPI-09, KPI-10 | Together these cover identity, authentication, network protection, data at rest, and the inventories access depends on; CC6.1 is broad and also covers architecture choices |
| CC6.2 | New internal and external users are registered and approved before they get credentials or access, and credentials are removed once access is no longer approved | PR.AA-01, PR.AA-02, GV.RR-04, GV.SC-10 | partial | HR-driven joiner and leaver workflows (07.11, 07.13, 07.14, 07.17; ADR-002); Temporary Access Pass onboarding after identity checks (07.10); guest and non-employee lifecycle (07.18); third-party access removed at exit (10.22) | 07, 10, ADR-002 | KPI-12, KPI-22 | Identity management, proofing, the HR-driven lifecycle, and third-party exits cover the topic; CC6.2 specifically requires approval before credentials and removal when no longer approved |
| CC6.3 | Access is granted, changed, and removed by role or system design, with least privilege and separation of duties | PR.AA-05 | equivalent | Access packages with separation-of-duties pairs (07.12); access reviews (07.14, 07.19); Privileged Identity Management (06.25); standing local admin rights removed (06.17) | 06, 07 | KPI-09, KPI-13 | Both govern how access permissions are granted, changed, and removed under least privilege and separation of duties; PR.AA-05 adds policy definition and review, and CC6.3 adds a role or system-design basis |
| CC6.4 | Only authorized people can physically reach facilities and protected assets | PR.AA-06 | equivalent | The cloud provider's physical controls, through the yearly review of its SOC report (10.10, 10.22); office physical access (05) | 05, 10 | KPI-05 | Both cover authorizing and enforcing physical access; at Fabrikam most of it belongs to the carved-out cloud provider |
| CC6.5 | Protections on physical assets end only after their data can no longer be read or recovered | ID.AM-08 | partial | Device recovery and sanitization under NIST SP 800-88 Rev. 2 (POL-04; 07; 06.31; 13.10, 13.22); vendor deletion confirmations at exit (10.22); the cloud provider's media disposal (10) | 06, 07, 10, 13 | KPI-05, KPI-06 | Life cycle management includes disposal; CC6.5 is specifically about keeping protection until data is unrecoverable |
| CC6.6 | Access controls defend the system against threats that originate outside its boundary | PR.IR-01, PR.AA-03, DE.CM-01 | partial | Legacy authentication blocked for everyone and the MFA baseline (06.10; finance and payroll join in 06.24); email protections and DMARC enforcement (06.14, 06.27); office network baseline and application proxy (06.20, 06.31) | 06 | KPI-08 | Network protection, authentication, and network monitoring address outside threats; CC6.6 centers on the system boundary |
| CC6.7 | Only authorized users and processes may send, move, or remove information, and it is protected while that happens | PR.DS-01, PR.DS-02 | partial | Data loss prevention for payroll identifiers (06.22, 06.28); sharing limits (06.18, 06.28); automatic external forwarding off (06.14); disk encryption and app protection (06.17, 06.29) | 06 | KPI-10, KPI-17 | Protection of data at rest and in transit overlaps; CC6.7 adds limits on who may move or remove information |
| CC6.8 | Controls stop, or detect and respond to, unauthorized or malicious software | PR.PS-05, DE.CM-09 | partial | Defender for Endpoint, attack surface reduction rules, and tamper protection (06.17, 06.26); Safe Attachments and Safe Links (06.14); standard user rights (06.17) | 06 | KPI-10 | Preventing unauthorized software and monitoring computing together cover CC6.8; each Subcategory alone covers part of it |

### CC7 System operations

| Criterion | Paraphrase | Closest CSF 2.0 Subcategories | Strength | Plan controls | Documents | KPIs | Rationale |
|---|---|---|---|---|---|---|---|
| CC7.1 | Detection and monitoring reveal configuration changes that open new weaknesses, and exposure to newly found vulnerabilities | ID.RA-01, PR.PS-01, DE.CM-09 | partial | Patching and remediation targets (06.17, 06.30; POL-07); monthly Secure Score and Entra recommendation review as an input (06.35); the external penetration test report (08.14); product vulnerability management (POL-12) | 06, 08, 10 | KPI-11 | Vulnerability identification, configuration management, and monitoring cover both concerns of CC7.1, spread across three Functions |
| CC7.2 | System components are watched for anomalies that could signal attacks, natural disasters, or errors, and anomalies are analyzed | DE.CM-01, DE.CM-03, DE.CM-09, PR.PS-04 | partial | MDR monitoring around the clock (08.10; ADR-003); Entra log archive (06.02, 08.03); unified audit logging confirmed (06.19); custom detections (08.12) | 06, 08, ADR-003 | KPI-16 | Monitoring and log generation cover most of CC7.2, which also names natural disasters and errors |
| CC7.3 | Security events are assessed to decide whether they are incidents, and incidents are acted on | DE.AE-02, DE.AE-04, DE.AE-08 | partial | Severity matrix and incident declaration (08.02, 08.08); MDR triage (08.10) | 08 | KPI-16, KPI-17 | Analysis, impact, and declaration against criteria match the evaluation step; CC7.3 also expects action on the result |
| CC7.4 | Identified security incidents are handled through a defined response program covering analysis, containment, fixes, and communication | RS.MA-01, RS.MA-02, RS.MA-03, RS.MA-04, RS.MA-05, RS.AN-03, RS.MI-01, RS.MI-02, RS.CO-02 | partial | POL-08 and the incident response plan (08.05, 08.08); response authority matrix (08); playbooks (08.15); notification decision path (08.04, 08.08) | 08, playbook | KPI-16, KPI-17 | Four Respond Categories together cover CC7.4; each alone covers part of it |
| CC7.5 | Recovery from security incidents is planned and carried out | RC.RP-01, RC.RP-03, RC.RP-06, ID.IM-04 | partial | After-action reports and tracked actions (08.09, 08.14); recovery with document 14; Microsoft 365 backup (ADR-006) | 08, 14, ADR-006 | KPI-18, KPI-19 | Recovery execution, verified restoration, closure, and plan improvement match CC7.5, which frames recovery as part of incident handling |

### CC8 Change management

| Criterion | Paraphrase | Closest CSF 2.0 Subcategories | Strength | Plan controls | Documents | KPIs | Rationale |
|---|---|---|---|---|---|---|---|
| CC8.1 | Changes to infrastructure, data, software, and procedures follow a controlled path from approval through testing to release | PR.PS-01, PR.PS-02, PR.PS-06, ID.RA-07 | partial | Change Advisory Board for corporate IT (13.02, 13.19); Engineering's change process (POL-11, POL-12); update rings with deadlines (06.17); the year-end freeze (10) | 06, 10, 13 | KPI-24 | Configuration management, maintenance, secure development, and change risk overlap; CSF has no single outcome for the controlled change life cycle in CC8.1 |

### CC9 Risk mitigation

| Criterion | Paraphrase | Closest CSF 2.0 Subcategories | Strength | Plan controls | Documents | KPIs | Rationale |
|---|---|---|---|---|---|---|---|
| CC9.1 | Mitigations are chosen and developed for risks of business disruption | GV.RM-04, PR.IR-03, ID.IM-04 | partial | Business impact analysis and continuity planning (14.07, 14.09; POL-09); risk treatment (11.07) | 11, 14 | KPI-01, KPI-19 | Risk response direction, resilience mechanisms, and operational plans cover the topic; CC9.1 covers business disruption broadly |
| CC9.2 | Risks from vendors and business partners are evaluated and managed | GV.SC-04, GV.SC-05, GV.SC-06, GV.SC-07, GV.SC-10, ID.AM-04, ID.RA-10 | partial | Intake (10.04, 10.17); due diligence and SOC report review including vendors' CUECs (10.10, 10.22); contract clauses (10.17); monitoring and offboarding (10); MDR provider review (ADR-003); cloud provider CSOCs (10) | 10, 15, ADR-003 | KPI-05 | These supplier outcomes cover the assessment and management in CC9.2; GV.SC is broader, and CC9.2 treats business partners on the same footing as vendors |

### A1 Availability

| Criterion | Paraphrase | Closest CSF 2.0 Subcategories | Strength | Plan controls | Documents | KPIs | Rationale |
|---|---|---|---|---|---|---|---|
| A1.1 | Processing capacity and usage are tracked and evaluated so demand is met and capacity can be added in time | PR.IR-04 | equivalent | Product capacity monitoring and year-end peak planning by Engineering under the RACI (04, 14) | 04, 14 | None in the catalog (an Engineering measure) | Both require capacity to be maintained so the service stays available |
| A1.2 | Environmental safeguards, backup processes, and recovery infrastructure are put in place, run, and monitored | PR.IR-02, PR.IR-03, PR.DS-11 | partial | Microsoft 365 backup (ADR-006); product backup and disaster recovery with Engineering (14); the cloud provider's environmental protections (CSOC, 10) | 10, 14, ADR-006 | KPI-19 | Environmental protection, resilience mechanisms, and backups match the parts of A1.2, which also covers monitoring the recovery infrastructure |
| A1.3 | Recovery procedures are tested | PR.DS-11, ID.IM-02 | partial | Restore tests (14.05, 14.12); the product disaster recovery test (Engineering, 14.16); exercises (08.14) | 08, 14 | KPI-19, KPI-18 | Backup testing and improvement from exercises overlap; A1.3 asks specifically for testing recovery plan procedures |

### C1 Confidentiality

| Criterion | Paraphrase | Closest CSF 2.0 Subcategories | Strength | Plan controls | Documents | KPIs | Rationale |
|---|---|---|---|---|---|---|---|
| C1.1 | Confidential information is identified and kept for its retention period | ID.AM-07, PR.DS-01, PR.DS-02 | partial | POL-05 classification; sensitivity labels (06.28); data inventories (05); data loss prevention (06.22, 06.28); support case data handling (06) | 05, 06, 10 | KPI-17 | Data inventories and protection at rest and in transit cover the topic; C1.1 applies to information designated confidential under Fabrikam's commitments |
| C1.2 | Confidential information is disposed of as confidentiality commitments require | ID.AM-08 | partial | POL-15 retention and deletion; device sanitization (POL-04; 13.10, 13.22); support case data deleted after closure (06); vendor deletion confirmations at exit (10.22) | 06, 07, 10, 13 | KPI-05 | Life cycle management includes disposal; C1.2 ties disposal to confidentiality commitments and retention |

## Coverage notes

- **Criteria Fabrikam meets partly through others.** CC6.4, and parts of A1.2 and CC6.5, rest on the carved-out cloud provider through complementary subservice organization controls (CSOCs), and A1.1 rests on Engineering's capacity monitoring under the RACI. The crosswalk shows the framework relationship; document 10 shows who carries each control.
- **Criteria with thin CSF coverage.** The board-independence element of CC1.2, CC3.3 (fraud), and the organization-wide reach of CC1.1, CC1.4, and CC2.1 have no close CSF 2.0 counterpart. The plan treats payroll and payment fraud directly (R-01, R-02) and leaves board composition to the CEO.
- **CSF outcomes without a close counterpart in the in-scope criteria** (author's judgment), for example GV.RM-07 (strategic opportunities, or positive risks) and PR.DS-10 (data in use). They stay in the Target Profile on their own merits.
- **Out of scope.** The Processing Integrity and Privacy criteria are outside the current report; document 10, section 3.11, sets the decision path.

## The CSV file

[csf2-soc2-crosswalk.csv](../../data/csf2-soc2-crosswalk.csv) holds both views: View A as one row per Category and criterion pair, and View B as one row per criterion. It is UTF-8, comma-separated, with every field quoted. Lists inside a field are separated by semicolons.

| Column | Meaning |
|---|---|
| view | A (CSF 2.0 Category to SOC 2 criterion) or B (SOC 2 criterion to CSF 2.0 Subcategories and plan controls) |
| row_id | Stable identifier: A-01 onward and B-01 onward |
| source_framework | Framework and version of the source identifier |
| source_id | The CSF 2.0 Category (View A) or the SOC 2 criterion (View B) |
| source_summary | Original paraphrase of the source |
| target_framework | Framework and version of the target identifiers |
| target_ids | The SOC 2 criterion (View A) or the CSF 2.0 Subcategories (View B) |
| target_summary | Original paraphrase of the target |
| relationship | equivalent, partial, or related, as defined above |
| rationale | Why that strength was chosen |
| plan_controls | View B only: action IDs and named controls that address the criterion; empty in View A |
| plan_documents | Document keys from the table above |
| kpis | KPI IDs; "none" where no catalog KPI applies |
| citation | Where the identifiers and paraphrases come from |

## Phase plan

These are the crosswalk's tasks inside document 10's actions; document 10's phase plan has the full action for each ID.

| Phase | Action ID | Action | Outcome | KPI | Owner role | Workstream |
|---|---|---|---|---|---|---|
| Phase 1 | 10.06 | Scope the NIST CSF 2.0 Organizational Profile with the CTO and gather its evidence through discovery | Profile scope agreed; evidence gathered | None (input to M3) | Director of IT and Security | WS-5 |
| Phase 2 | 10.07 | Draft the Current Profile at Category level, using this crosswalk to tag each control in the SOC 2 control list with its CSF 2.0 Subcategories | One evidence trail serves both frameworks | None (input to M3) | Director of IT and Security | WS-5 |
| Phase 3 | 10.13 | Build the Target Profile and gap action plan; link each gap to the criteria it affects through this crosswalk | Profiles approved (M3) | KPI-01 | Director of IT and Security | WS-5 |
| Phase 4 | 10.20 | Load the crosswalk data into the compliance automation platform as a custom mapping when the platform is connected (the same file was the custom-framework test in the ADR-007 selection, 10.15) | The mapping maintained in one place | KPI-03 | Director of IT and Security, then the GRC Analyst | WS-5 |
| Phase 5 | 10.28 | At M7, recheck every row against the current CSF and Trust Services Criteria editions and against any official AICPA or NIST mapping published since | Crosswalk current for year two | KPI-01, KPI-02 | GRC Analyst | WS-5 |

## Resourcing and dependencies

- **Roles.** The Director of IT and Security owns the crosswalk until the GRC Analyst maintains it from March 2027 (the base case start); Category owners named in the Current Profile check their rows; the Director approves any change of strength.
- **Partners.** The SOC 2 audit firm tests Fabrikam's controls against the criteria whatever this crosswalk says; it is not asked to approve the mapping, which stays Fabrikam's own analysis.
- **Licenses and tools.** None until the compliance automation platform goes live in April 2027 ([ADR-007](../adr/ADR-007-compliance-automation-platform.md)); until then the CSV in this repository is the working copy. NIST's CSF 2.0 Reference Tool supplies the Core in machine-readable form.
- **Depends on.** Document 10 (the control list and the Profiles) and every document and ADR in the document key, whose controls and action IDs it cites.

## Risks and open questions

- **Not official.** No AICPA mapping to CSF 2.0 was found, and AICPA's mappings page is for members only, so its absence is not proven. If AICPA or NIST publishes an official mapping, this crosswalk is compared with it at the next review (10.28).
- **Judgment, not fact.** Strength ratings are the author's analysis; another reader could rate some pairs differently. The audit firm's testing does not depend on them.
- **Source of the paraphrases.** The criteria paraphrases were checked against the criteria text in TSP section 100 (the 2017 criteria with the March 2020 updates). AICPA distributes the current edition, with the 2022 points of focus, through the download page in Sources; the 2022 revision changed the points of focus, not the criteria. No point of focus is quoted here; rationales that draw on one, such as those for CC1.5 and CC3.4, say so.
- **Moving targets.** CSF 2.0 is current (no CSF 2.1 exists as of 2026-10-13), and NIST's Informative References listing grows over time; both are rechecked at M7.
- **Document numbers.** Where a whole document carries a control rather than one action, the row cites the document number.

## Framework mapping

This document is the mapping. Its own role in the program supports:

| Theme | NIST CSF 2.0 | SOC 2 (2017 TSC) |
|---|---|---|
| Framework and contractual requirements understood and tracked | GV.OC-03 | CC3.1 |
| Using the mapping to evaluate and improve the program | GV.OV-03, ID.IM-01 | CC4.1 |

## Sources

- The NIST Cybersecurity Framework (CSF) 2.0 (CSWP 29, February 26, 2024), Appendix A (CSF Core). NIST. https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf . Checked 2026-10-13. Primary.
- CSF 2.0 Reference Tool. NIST. https://csrc.nist.gov/Projects/Cybersecurity-Framework/Filters#/csf/filters . Checked 2026-10-13. Primary.
- CSF 2.0 Informative References. NIST. https://www.nist.gov/cyberframework/informative-references . Checked 2026-10-13. Primary.
- 2017 Trust Services Criteria (With Revised Points of Focus, 2022), download page. AICPA & CIMA. https://www.aicpa-cima.com/resources/download/2017-trust-services-criteria-with-revised-points-of-focus-2022 . Checked 2026-10-13. Primary.
- SOC 2 Reporting on Controls at a Service Organization, Chapter 1 (2018 edition: trust services categories, common criteria, applicable criteria by category). AICPA, excerpt hosted by Wiley. https://catalogimages.wiley.com/images/db/pdf/9781945498602.excerpt.pdf . Checked 2026-10-13. Primary (AICPA text on a third-party host).
- Mapping: 2017 Trust Services Criteria to NIST CSF (dated May 4, 2018; includes March 2020 updates). AICPA & CIMA. https://www.aicpa-cima.com/resources/download/mapping-2017-trust-services-criteria-to-nist-csf . Checked 2026-10-13. Primary.
- Get mappings relevant to the trust services criteria (members-only mappings page). AICPA & CIMA. https://www.aicpa-cima.com/resources/article/get-mappings-relevant-to-the-soc-suite-of-services . Checked 2026-10-13. Primary.
- AICPA 2017 Trust Services Criteria Crosswalk (NIST Privacy Framework resource, community contribution). NIST. https://www.nist.gov/node/1831726 . Checked 2026-10-13. Primary.
- To the Point No. 2022-13 (November 2, 2022), a summary of AICPA's 2022 revisions to the Trust Services Criteria points of focus and the SOC 2 description criteria guidance. Ernst & Young LLP. https://ey.com/content/dam/ey-unified-site/ey-com/en-us/technical/accountinglink/documents/ey-ttp17549-221us-11-02-2022.pdf . Checked 2026-10-13. Secondary.
- Guidelines for Media Sanitization (SP 800-88 Rev. 2, September 2025). NIST. https://csrc.nist.gov/pubs/sp/800/88/r2/final . Checked 2026-10-13. Primary.
