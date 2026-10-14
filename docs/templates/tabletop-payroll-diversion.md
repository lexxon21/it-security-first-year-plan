# Tabletop exercise template: payroll diversion (R-01)

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

| Field | Value |
|---|---|
| Status | Untested template. No exercise has been run, and this file holds no results |
| Format | Discussion-based and facilitator-led; 90 minutes; in person or on video |
| Scenario basis | R-01: payroll diversion or payment fraud against Fabrikam's own finance and HR through business email compromise (BEC); threat scenarios S-01 and S-04 in document [17](../17-threat-profile.md) |
| Playbook exercised | [Payroll diversion and email compromise](../playbooks/payroll-diversion-and-email-compromise.md) |
| First planned run | Late February 2027, Phase 4 (action 08.09 in document [08](../08-detection-and-incident-response.md)) |

## Purpose

This template runs a 90-minute executive tabletop for Fabrikam (fictional) on its top-ranked fraud risk. BEC was the second largest loss category in the 2025 report of the FBI's Internet Crime Complaint Center (IC3), with 24,768 complaints, and the FBI has warned specifically about payroll diversion. The exercise tests decisions rather than technology: who stops a payment, who decides about customers, and how fast. Its design follows NIST SP 800-84 for test, training, and exercise programs, and it borrows the structure of CISA's Tabletop Exercise Packages: objectives, a scenario, discussion questions, and an after action report.

## Objectives

| ID | Objective | What it tests |
|---|---|---|
| O1 | Finance and People staff stop a bank-change request, verify it by calling a known number, and know when to escalate | Playbook steps 1 to 3 |
| O2 | An after-hours alert reaches a decision maker, and an incident commander is named quickly | On-call, roles, and escalation in document 08; R-10 |
| O3 | Payment decisions are clear: bank recall, IC3 report, holding a payroll change, and paying an affected employee on time | Decision rights of the CFO and VP of People |
| O4 | The team decides whether customer data is involved and whether a notice is due, using the contract clause inventory | General Counsel; R-10 |
| O5 | Customer and employee messages are agreed from the holding statements | Chief Customer Officer, VP of People |
| O6 | The exercise ends with owned, dated improvement actions | KPI-18 |

## Participants

| Exercise role | Who | Plays |
|---|---|---|
| Incident commander | Director of IT and Security | Their own role |
| Payments | CFO | Their own role |
| Employee pay and communication | VP of People | Their own role |
| Legal | General Counsel | Their own role, and describes how CEO approval would be obtained |
| Customer communication | Chief Customer Officer | Their own role |
| Technology executive | CTO | Their own role, and speaks for Engineering on product questions |
| On-call and IT operations | IT Operations Manager | Their own role and the on-call |
| Facilitator (not a player) | For the first run, the MDR provider's exercise lead or an outside facilitator, because the GRC Analyst and the Security Engineer start in March 2027 in the base case; for later runs, either of them as well | Runs the clock and reads the injects |
| Note-taker and evaluator (not a player) | A second non-player | Completes the decision log and the evaluation sheet |

The payroll and accounts payable leads may observe.

## Ground rules

- No fault. The exercise reviews decisions and processes, not people.
- Use today's real processes, contact lists, and contracts. "We don't know" is a useful answer and goes in the notes.
- No live systems are touched and no real messages are sent.
- The scenario, people, and messages are fictional.
- The after-action report records gaps and actions; it does not attribute quotes to individuals.

## Preparation checklist

Two to three weeks before the exercise:

- [ ] Date set outside payroll run days, month-end close, and mid-December through January.
- [ ] Participants have the playbook and the roles and decision rights sections of document 08 (about 30 minutes of reading). They are not told the scenario.
- [ ] The current on-call list, the executive contact list, Fabrikam's bank fraud contact, and the status of the contract clause inventory are available in the room.
- [ ] The facilitator has the inject cards and timings; the note-taker has the decision log and the evaluation sheet below.
- [ ] Holding statement drafts are printed.
- [ ] The facilitator sets the scenario conditions to match the real state on the day.

## Scenario conditions

| Condition | Default for a late February 2027 run | Actual on the day |
|---|---|---|
| MDR provider | Onboarding, not yet live; after-hours alerts reach the on-call as Defender email notifications turned into a phone page; an incident response retainer, or pre-agreed emergency terms with an incident response firm, in place since before mid-December (document 08) | |
| Sign-in methods | Administrators on phishing-resistant methods since December; the wave 2 group (finance, payroll, People, Support staff with customer data access, executives, and IT staff daily accounts) enforced in February; push MFA or passkeys for everyone else, and no employee on SMS or voice after 2027-02-01 (document 06) | |
| Email authentication | DMARC aggregate reporting on every sending domain; the older brand domain that no longer sends already parked at p=reject; enforcement under way from February, the older brand domain that still sends first and the main domain last (document 06) | |
| Payroll calendar | Fabrikam's own payroll runs on Friday; several customers are mid-cycle | |

## Timed injects

| Time | Inject | Situation (read aloud) | Discussion questions | Decision points |
|---|---|---|---|---|
| 0:00 to 0:08 | Opening | The facilitator states the objectives, ground rules, and scenario conditions | None | None |
| 0:08 to 0:20 | 1 | Tuesday, 09:10. A payroll team member receives an email that appears to come from a customer success manager's personal address. It asks to switch their direct deposit to a new bank before Friday's run because "the old account was closed", and it quotes their employee ID. | How is this request verified today? Who may approve it? Can the employee make the change in the HR system of record themselves? What happens if a busy team member keys it in anyway? | D1 |
| 0:20 to 0:32 | 2 | Wednesday, 14:30. Accounts payable receives a reply on a real, months-old email thread with a long-standing supplier, giving new remittance details for an invoice due Friday. The message passes SPF, DKIM, and DMARC checks from the supplier's real domain. | Does passing authentication mean the request is genuine? Who calls whom, and on which number? Who decides to delay a payment that is due? Should the supplier be told its mailbox may be compromised? | D1, D7 |
| 0:32 to 0:47 | 3 | Wednesday, 22:50. A high-severity alert reaches the on-call: a new inbox rule on an accounts payable team member's mailbox moves messages that mention invoices or bank details to an obscure folder. It was created minutes after a sign-in from an unfamiliar location. If the scenario conditions say the MDR is live, it has already revoked the sessions and disabled the account under the pre-approved matrix. | Who is incident commander tonight? What severity? Who must be told tonight, and who can wait until morning? What happens if nobody answers the phone? Is the inject 2 payment now on hold? | D2 |
| 0:47 to 0:59 | 4 | Friday, 08:00. Payroll ran overnight. The customer success manager from inject 1 calls: their pay did not arrive. Records show the direct-deposit change from Tuesday was keyed in. | Who calls the bank, and how fast? Who reports to IC3? How is the employee paid on time, and who decides? What is said to the employee? | D3, D6 |
| 0:59 to 1:12 | 5 | Friday, 11:00. The investigation finds that the compromised mailbox holds a support-case thread with one customer's payroll export (Social Security numbers and bank details), and the attacker's session synced that folder. | Is customer data involved? What does that customer's contract require, and by when? One customer or more? Which holding statement, approved by whom, sent by whom? Do the logs reach back far enough to know what else was touched? | D4, D5 |
| 1:12 to 1:20 | 6 | Friday, 13:00. A customer's payroll administrator forwards a message received from the compromised Fabrikam address, asking them to update Fabrikam's remittance details. | Who contacts this customer and any others who may have received the message, and what do they say? Does Engineering need to check recent bank-detail changes in the product? | D7 |
| 1:20 to 1:30 | Hot wash | An immediate debrief led by the facilitator | What worked? What would have failed in a real incident? Which three actions matter most, with owners and dates? | None |

Facilitator background for inject 5: Microsoft documents that when a mailbox folder is synced, every item in that folder is treated as compromised, which is why the question of scope is hard.

## Discussion questions by role

- **CFO:** What loss threshold raises severity? Who at the bank is called, and is that number on file? Who can hold a payment or a payroll run?
- **VP of People:** How does an employee change direct deposit today? How is someone whose pay was diverted paid, and how fast? What do staff hear, and from whom?
- **General Counsel:** Which contracts define the notice clock, and from which event? When does a legal hold start? When is law enforcement involved beyond IC3?
- **Chief Customer Officer:** Who speaks to the affected customer? What do customer-facing teams say if asked?
- **CTO:** Is the product involved? Who in Engineering checks product-side bank changes, and how quickly?
- **Director of IT and Security:** When was the incident commander named? Which questions could the logs answer, and which not?
- **IT Operations Manager:** Did the alert reach a person? What could the on-call do alone, and what needed someone else?

## Decision log

The note-taker completes this during the exercise.

| ID | Decision | Expected owner | Decision reached | Who decided | Time taken |
|---|---|---|---|---|---|
| D1 | Is the request genuine? Is the change held? | Process owner | | | |
| D2 | Is an account compromised? What severity? Who is incident commander? | Incident commander | | | |
| D3 | Bank recall and IC3 report | CFO | | | |
| D4 | Is customer data involved? | Incident commander, General Counsel | | | |
| D5 | Is a customer notice due? | General Counsel, with CEO approval (simulated) | | | |
| D6 | How is the employee paid, and what are they told? | VP of People, CFO, General Counsel | | | |
| D7 | Warn customers, partners, or the supplier? | Chief Customer Officer or process owner, with General Counsel | | | |

## Evaluation criteria

| Objective | Met when | Rating (Met, Partly met, Not met) | Notes |
|---|---|---|---|
| O1 | Players name the known-number call and the two-person check without prompting, and hold the changes in injects 1 and 2 | | |
| O2 | An incident commander is named during inject 3, the right executives are told within the times in document 08, and a fallback exists if the on-call does not answer | | |
| O3 | The CFO names who calls the bank and when, the IC3 report has an owner, and the VP of People and CFO agree how the employee is paid on time | | |
| O4 | General Counsel reaches a customer data decision using the clause inventory, or records that the clause is unknown, and sets the next decision time | | |
| O5 | A holding statement is chosen, an approver and a sender are named, and an employee message is agreed | | |
| O6 | At least three actions leave the room with an owner and a due date | | |

## After-action report template

The Director of IT and Security prepares the report within 10 business days (proposal). Participants review it; actions go into the action tracker and are reported as KPI-18 at the monthly IT and Security Steering Group and the Quarterly Risk Review. The report is internal and confidential because it describes process weaknesses.

### 1. Exercise overview

| Field | Entry |
|---|---|
| Date and duration | |
| Facilitator and note-taker | |
| Participants (roles) | |
| Scenario conditions on the day | |
| Objectives | O1 to O6 |

### 2. Summary

Two or three sentences: overall readiness, the most important gap, and the most important strength.

### 3. Results by objective

| Objective | Rating | What happened | Gap |
|---|---|---|---|
| O1 | | | |
| O2 | | | |
| O3 | | | |
| O4 | | | |
| O5 | | | |
| O6 | | | |

### 4. Strengths

What worked and should be kept.

### 5. Areas for improvement

For each area: what happened, why (process, people, technology, or missing information), and the likely impact in a real incident.

### 6. Improvement plan

| ID | Finding | Action | Owner role | Due date | Status | Linked document or risk |
|---|---|---|---|---|---|---|
| | | | | | | |

### 7. Review and sign-off

| Step | Who | Date |
|---|---|---|
| Prepared | Director of IT and Security | |
| Reviewed | Exercise participants | |
| Actions accepted | Named action owners | |

## Facilitator notes

- Keep time, and park side topics on a visible list for later.
- Read each situation as written and do not reveal the next inject early.
- If players solve the problem in inject 1, let them; the later injects still test escalation, legal, and communication decisions.
- If the real state on the day differs from the scenario conditions, adjust the inject wording rather than skipping it.
- Variant for R-02: replace injects 5 and 6 with a customer administrator account takeover in the product, and add the Engineering Manager and the Chief Product Officer.

## Sources

- Guide to Test, Training, and Exercise Programs for IT Plans and Capabilities (NIST SP 800-84, September 2006), publication record. NIST. https://csrc.nist.gov/pubs/sp/800/84/final . Checked 2026-10-13. Primary.
- CISA Tabletop Exercise Packages. CISA. https://www.cisa.gov/resources-tools/services/cisa-tabletop-exercise-packages . Checked 2026-10-13. Primary.
- Incident Response Recommendations and Considerations for Cybersecurity Risk Management: A CSF 2.0 Community Profile (NIST SP 800-61 Rev. 3). NIST. https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r3.pdf . Checked 2026-10-13. Primary.
- 2025 IC3 Annual Report (Internet Crime Report 2025). FBI Internet Crime Complaint Center (IC3). https://www.ic3.gov/AnnualReport/Reports/2025_IC3Report.pdf . Checked 2026-10-13. Primary.
- Cybercriminals Utilize Social Engineering Techniques To Obtain Employee Credentials To Conduct Payroll Diversion (Alert I-091818-PSA). FBI IC3. https://www.ic3.gov/PSA/2018/PSA180918 . Checked 2026-10-13. Primary.
- Cyber Criminals Impersonating Employee Self-Service Websites to Steal Victim Information and Funds (Alert I-042425-PSA). FBI IC3. https://www.ic3.gov/PSA/2025/PSA250424 . Checked 2026-10-13. Primary.
- Use MailItemsAccessed to investigate compromised accounts. Microsoft Learn. https://learn.microsoft.com/en-us/purview/audit-log-investigate-accounts . Checked 2026-10-13. Primary.
