# Stakeholder conversation guide

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

## Purpose

This template supports the Phase 1 listening work in document [05](../05-environment-discovery.md). It gives the Director of IT and Security five to eight questions for each executive at Fabrikam (fictional) and for the team leads whose work touches IT, security, or customer data. Every set covers the same five themes so that answers can be compared: priorities, risk tolerance, pain points, what good looks like, and upcoming events. The questions are a starting point; a good follow-up matters more than finishing the list.

## How to run the conversations

- **Timing (proposal).** About 45 minutes each, in weeks 1 and 2 of Phase 1, executives first. Customers' benefits open enrollment and year-end preparation make November busy, so sessions are booked in the first days.
- **Preparation.** Send the five themes ahead, not the questions, and reread the relevant part of document [01](../01-scenario-and-assumptions.md) before each session.
- **Posture.** Listen, and ask to see a real example rather than hear a summary. Do not propose solutions yet; note ideas for later.
- **Notes.** Write up each conversation the same day in the one-page format below and keep it in the restricted discovery location. The listening report quotes themes, not names, unless the speaker agrees.
- **Same close every time.** "Who else should the Director talk to?" and "What should the IT and security team keep doing exactly as it does today?"
- **Log as you go.** An answer that names a risk or contradicts a day-1 assumption (A-01 to A-12) goes into the findings log that day.

## Questions for executives

### CEO

1. **Priorities.** What are Fabrikam's three most important business goals for the next 12 months, and where could an IT or security failure get in their way?
2. **Risk tolerance.** Which event would you least want to explain to customers or the board: a payroll outage during year-end, a leak of workers' Social Security numbers, a fraudulent payment, or something else? Where would you accept more risk to move faster?
3. **Risk ownership.** Which business risks should you own personally, and which belong to other executives?
4. **Pain points.** Where do IT or security slow the business down today, and what have customers or prospects complained about?
5. **What good looks like.** A year from now, what would make you call this function an asset? What do you want to see each month, and in what form?
6. **Upcoming events.** What is coming that the plan must support, such as board meetings, fundraising, acquisitions, or major launches? What does the board expect to hear about cyber risk?
7. **Escalation.** How and when do you want to hear about a serious incident, including at night or on a weekend?

### CFO

1. **Priorities.** Which finance processes must never fail: Fabrikam's own payroll, vendor payments, the month-end close, the audit?
2. **Risk tolerance.** How are vendor bank-detail changes and urgent payment requests verified today, and has Fabrikam seen attempts? What size of loss would be material?
3. **Pain points.** Where does SOC 2 coordination take the finance manager's time near audit dates, and what does the outside readiness consultant do that Fabrikam should own itself?
4. **Budget.** How are IT and security budgets set today (cycle, approval path, level of detail), and what would make the budget proposal at M3 credible to you?
5. **What good looks like.** How should value be shown: cost drivers, options, and using licenses Fabrikam already pays for before buying more?
6. **Upcoming events.** When do the budget cycle, the audit, the Microsoft agreement renewal, and major vendor renewals fall?
7. **Vendors.** Which vendors can reach customer or employee data, and who reviews them today?

### CTO

1. **Priorities.** What are Engineering's goals for the year, and which platform changes are planned (architecture, AI features, the acquired product line)?
2. **Shared responsibility.** Where should the line sit between corporate IT, company-wide security, and product security engineering? What do senior engineers handle informally today?
3. **Risk tolerance.** What availability and recovery do customers expect during their payroll runs, and when was disaster recovery last tested?
4. **Pain points.** Where do corporate IT or security get in Engineering's way today, for example Mac management, access to tools, or the change process?
5. **What good looks like.** What should the Director deliver in the first 90 days to earn Engineering's trust?
6. **Upcoming events.** Which releases, migrations, and audits fall before and after the mid-December freeze, and when is Engineering's time scarcest?
7. **Working together.** How often, and in what form, do you want updates between IT and Security Steering Group meetings?

### Chief Product Officer

1. **Priorities.** Which roadmap themes matter most this year: AI features, the acquired product line, integrations, something else?
2. **Data.** Which new data types or uses are planned (for example more location data, the proposed voice verification for customers' administrators who call the support line, or AI on workforce data), and who reviews privacy and security before launch?
3. **Risk tolerance.** When a security requirement and a delivery date conflict, how should the decision be made, and by whom?
4. **Pain points.** Which customer security reviews or questionnaires slowed a launch or a deal?
5. **What good looks like.** What would customers need to see to treat security as a reason to buy, for example SOC 2 coverage of the acquired product line or phishing-resistant sign-in for customer administrators?
6. **Upcoming events.** Which launches, customer advisory meetings, or product changes could alter the SOC 2 system description?
7. **AI at work.** How do product teams use AI tools today, and what guidance would help them rather than block them?

### Chief Customer Officer

1. **Priorities.** What do customers value most, and what would make them leave?
2. **Risk tolerance.** What happens today when a customer reports that an administrator account was taken over or a worker's bank details were changed? The FBI warned in 2025 that criminals use search ads to impersonate employee self-service and payroll sites; has Fabrikam seen this?
3. **Pain points.** How do support staff handle payroll exports and other customer files during a case, and how do they confirm who is calling?
4. **What good looks like.** If Fabrikam had a security incident, how should customers hear about it, and who should speak to them?
5. **Customer requirements.** Which customers ask for audits, questionnaires, or specific controls, and what does Fabrikam's SOC 2 report expect customers to do themselves?
6. **Upcoming events.** When do year-end, tax form season, open enrollment peaks, and major renewals stretch the team?

### VP of People

1. **Priorities.** What are the people plans for the year: hiring waves, reorganizations, new locations?
2. **Lifecycle.** How do joiners, movers, and leavers reach IT today, what goes wrong, and how quickly should a leaver lose access, including after an involuntary exit?
3. **HR data.** Fabrikam runs its own product as its HR system of record. Who owns the accuracy of start dates, end dates, managers, and departments?
4. **Risk tolerance.** What do employees receive today about monitoring and acceptable use, and what is the stance on phishing simulations? NIST's learning program guidance says such exercises should not be punitive and suggests involving the legal team in their design.
5. **Pain points.** What is a new hire's first day like today, from an IT point of view?
6. **What good looks like.** What would effective security training look like for all staff, and for higher-risk roles such as payroll, finance, and support?
7. **Upcoming events.** When do hiring waves, Fabrikam's own benefits enrollment, and policy acknowledgment cycles fall?

### General Counsel

1. **Priorities.** Which legal and regulatory matters will take your time this year, and which changes worry you most? California's automated decisionmaking technology rules, for example, apply from 2027-01-01.
2. **Contracts.** Which customer contracts or data processing terms set the shortest incident notification clock, and whom must Fabrikam tell first?
3. **Risk tolerance.** Which security commitments in contracts, or in the SOC 2 system description, go beyond what the controls deliver today?
4. **Privacy roles.** For the customer employee data it processes, which role does Fabrikam hold under California's privacy law and other state laws, and what follows from it? California's 2026 regulations, for example, require service providers to cooperate with the businesses they serve on cybersecurity audits and risk assessments.
5. **Regulatory questions.** Is Fabrikam an E-Verify employer agent for its customers? Could any customer contract, partner contract, or Fabrikam's own payroll activity bring the FTC Safeguards Rule into play?
6. **Biometrics and location.** How is the proposed voice verification for customers' administrators who call Fabrikam's support line reviewed before any decision, and by whom? Which location notices do customers rely on Fabrikam to support?
7. **Offices and staff.** In which states are the two offices, and which employee monitoring notice laws apply to Fabrikam's own staff there?
8. **Pain points and upcoming events.** Where do security questions slow contracts down, and which regulatory dates or customer audits fall in the next 12 months?

## Questions for team leads

### IT Operations Manager

1. **Priorities.** What does the IT team need most right now, and what works well that must not be broken?
2. **Pain points.** Which tickets and manual tasks recur most, and where does work depend on a single person?
3. **Risk tolerance.** Which changes worry you, and what has broken before?
4. **Inventories.** Where do the lists of devices, accounts, and applications live today, and how far can they be trusted?
5. **Admin access.** Who holds admin roles, which accounts are shared, and how are emergency access accounts kept and tested?
6. **What good looks like.** Which service levels would you be comfortable committing to, and which tools would you retire?
7. **Upcoming events.** Which renewals, hardware refreshes, and office changes are due? Which devices or applications still send mail through SMTP AUTH before Basic authentication is disabled by default (end of December 2026, per a community mirror of Microsoft's message center), and which users still rely on SMS or voice before Microsoft-provided delivery ends for most users on 2027-02-01?

### Engineering Manager

1. **Priorities.** What are the team's goals, and how is security work planned today?
2. **Pain points.** Where do device management, access requests, or code hosting permissions slow engineers down?
3. **Risk tolerance.** How are secrets and integration credentials stored and rotated, and how is access to the live platform granted and removed?
4. **Secure development.** How do code review, dependency checks, and vulnerability reports from customers or researchers work today?
5. **What good looks like.** Which guardrails would help engineers rather than slow them?
6. **Upcoming events.** Which releases must land before the freeze, and which AI features or migrations follow it?

### Site Reliability Engineering (SRE) lead

1. **Priorities.** What are the reliability goals, and what do customers' payroll windows mean for operations?
2. **Recovery.** What are the recovery targets, when was disaster recovery last tested, and who can delete or alter backups?
3. **Logging.** Which product logs exist, how long are they kept, and could they show which customer data was accessed during an incident?
4. **Pain points.** Where do on-call load, alert noise, or dependencies on corporate IT hurt most?
5. **Risk tolerance.** Which single points of failure worry you most?
6. **What good looks like.** What would a shared incident process and joint exercises with corporate IT look like?
7. **Upcoming events.** When are the capacity peaks around year-end and tax forms, and which migrations are planned?

### Support leader

1. **Priorities.** What are Support's goals and peak periods?
2. **Caller verification.** How do agents confirm that a caller is an authorized customer administrator before changing access or bank details?
3. **Customer data in cases.** How are payroll exports and other files requested, shared, stored, and deleted?
4. **Pain points.** Which tools, access steps, or security steps slow agents down?
5. **Risk tolerance.** Which shortcuts happen under time pressure? The answer is used to fix processes, not to assign blame.
6. **What good looks like.** What would a safe and fast way to handle customer files look like?
7. **Upcoming events.** How do year-end, tax form season, and open enrollment change volumes and staffing?

### Sales leader

1. **Priorities.** What are the revenue goals, and which customer segments matter most?
2. **Security reviews.** How are security questionnaires and SOC 2 report requests handled, how long do they take, and where do deals stall?
3. **The acquired product line.** What do enterprise buyers ask about its SOC 2 coverage, and which deals depend on it?
4. **Risk tolerance.** Which security commitments has Sales made, or been asked to make?
5. **Pain points.** Where do CRM access, marketing email delivery, or security reviews cost time?
6. **What good looks like.** What security story could Sales tell honestly and with confidence?
7. **Upcoming events.** Which large deals, renewals, and sales events fall in the next two quarters?

## One-page note format

| Field | What to record |
|---|---|
| Who and when | Role and date |
| Priorities | In the speaker's own words |
| Risks named | Matched to R-01 to R-15 where possible, or marked as new |
| Risk tolerance | What the speaker would accept, and what they would not |
| Pain points | With concrete examples |
| What good looks like | Measurable where possible |
| Dates and events | Anything that affects timing |
| Assumptions affected | A-01 to A-12, confirmed or contradicted |
| Follow-ups | Owner and due date |

## How the answers feed M1

| What was heard | Where it goes |
|---|---|
| Priorities and dates | The listening report; the change calendar in document [13](../13-it-service-management.md); phase timing in documents [02](../02-first-90-days.md) and [03](../03-twelve-month-roadmap.md) |
| Risks named and risk tolerance | The top risks draft for document [11](../11-risk-management.md), with a proposed executive owner for each risk |
| Pain points | The listening report; Phase 2 quick wins in documents [06](../06-microsoft-365-security-baseline.md), 13, and [15](../15-enterprise-systems-and-saas.md) |
| What good looks like | Proposed KPI targets and scorecard choices in document [12](../12-metrics-and-executive-reporting.md) |
| Contract, legal, and customer commitments | The notification clock in document [08](../08-detection-and-incident-response.md); policy and privacy work in document [10](../10-governance-and-compliance-program.md) |
| Contradicted assumptions | The assumption verification in document 05, reported at M1 |

## Sources

- The NIST Cybersecurity Framework (CSF) 2.0 (CSWP 29), Organizational Context category (GV.OC). NIST. https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf . Checked 2026-10-13. Primary.
- Building a Cybersecurity and Privacy Learning Program (SP 800-50 Rev. 1), section 2.7.2 on phishing exercises. NIST. https://csrc.nist.gov/pubs/sp/800/50/r1/final . Checked 2026-10-13. Primary.
- California Finalizes Regulations to Strengthen Consumers' Privacy (September 23, 2025). California Privacy Protection Agency. https://www.cppa.ca.gov/announcements/2025/20250923.html . Checked 2026-10-13. Primary.
- Text of approved regulations on CCPA updates, cybersecurity audits, risk assessments, and automated decisionmaking technology (section 7050). California Privacy Protection Agency. https://cppa.ca.gov/regulations/pdf/ccpa_updates_cyber_risk_admt_appr_text.pdf . Checked 2026-10-13. Primary.
- 16 CFR Part 314, Standards for Safeguarding Customer Information (the FTC Safeguards Rule; eCFR, as of 2026-10-01). Office of the Federal Register and GPO. https://www.ecfr.gov/api/versioner/v1/full/2026-10-01/title-16.xml?part=314 . Checked 2026-10-13. Primary.
- Cyber Criminals Impersonating Employee Self-Service Websites to Steal Victim Information and Funds (Alert I-042425-PSA). FBI Internet Crime Complaint Center (IC3). https://www.ic3.gov/PSA/2025/PSA250424 . Checked 2026-10-13. Primary.
- Passkeys by default and retirement of Microsoft-provided SMS and voice authentication. Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sms-voice-retirement . Checked 2026-10-13. Primary.
- Deprecation of Basic authentication in Exchange Online. Microsoft Learn. https://learn.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/deprecation-of-basic-authentication-exchange-online . Checked 2026-10-13. Primary.
- MC786329, Exchange Online to retire Basic Auth for Client Submission (SMTP AUTH). mc.merill.net, a community mirror of Microsoft 365 Message Center posts. https://mc.merill.net/message/MC786329 . Checked 2026-10-13. Secondary.
