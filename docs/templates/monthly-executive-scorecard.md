# Monthly executive scorecard (template)

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

| Field | Value |
|---|---|
| Status | Template. It holds no results; every bracket is a placeholder |
| Month | [Month and year] |
| Data as of | [Last day of the month] |
| Prepared by | Director of IT and Security |
| Reviewed at | IT and Security Steering Group, [date]; then sent to the executive team |
| Definitions and targets | Document [12](../12-metrics-and-executive-reporting.md) and the [KPI catalog](../../data/kpi-catalog.csv) |

## How to fill it in (delete before sending)

- Keep it to one page: three sections, the same key performance indicators (KPIs) every month, and no overall score. The status key, abbreviations, and Sources at the end are reference material printed on the back.
- **Current:** this month's value, with the count (n) where the count is small.
- **Trend:** the last three monthly values, oldest first, and one word: better, worse, or steady.
- **Target:** the headline target from document 12, word for word; the KPI catalog keeps the full wording. Before M3, write "to be proposed at M3".
- **Status:** On track, At risk, Off track, Baseline only, or No data yet, by the rules in the status key below.
- **Note:** one line with the reason or the next step.
- **Watch:** any catalog KPI not on this page that is Off track this month.
- **Top risks, movement:** only risks whose rating, owner, or treatment changed, or flagged by a KPI or supporting check, plus new and closed risks; cite the KPI or the supporting check (document 12) behind each move.
- **Decisions needed:** each with options, a recommendation, the deciding executive, and a date; or "None this month". The Director proposes; the executive team decides; named executives accept risk.

## So what

[Up to three sentences: what changed this month, why it matters to the business, and what happens next.]

## Risk and compliance

| KPI | Current | Trend (last 3 months) | Target (proposal) | Status | Note |
|---|---|---|---|---|---|
| KPI-01 Top risks with an owner and an approved treatment plan (%) | [value] | [three values; word] | 100 percent by M3 and every month after | [status] | [note] |
| KPI-03 SOC 2 controls operating without exceptions (%) | Management testing: [value]. Audit firm, latest report: [value] | [three values; word] | No new exceptions caused by the Director's changes (period closing at M4); management testing 95 percent from Phase 4, 98 by M7 | [status] | [note] |
| KPI-04 Open audit exceptions and their median age | [count] open; median [days] days | [three values; word] | Owner and committed date within 10 business days; median age under 60 days from Phase 4 | [status] | [note] |

## Protection

| KPI | Current | Trend (last 3 months) | Target (proposal) | Status | Note |
|---|---|---|---|---|---|
| KPI-08 Phishing-resistant MFA coverage, admins and all users (%) | Admins: [value]. All employees: [value] (registered: [value]) | [three values; word] | Admins 100 percent by the end of Phase 2; all employees 90 percent by M6, 95 by M7; nobody on SMS or voice alone after 2027-02-01 | [status] | [note] |
| KPI-09 Standing privileged role assignments (count) | [count] (Global Administrators: [count]) | [three values; word] | Fewer than five Global Administrators, emergency access accounts included (end of Phase 1); fewer than 10 standing assignments (end of Phase 2); only the 2 emergency access accounts (end of Phase 4) | [status] | [note] |
| KPI-12 Leaver access removed within target (%) | [value] (n = [leavers]); urgent: [on time] of [urgent leavers] | [three values; word] | At least 98 percent from M6; every urgent leaver within one hour | [status] | [note] |
| KPI-16 Mean time to acknowledge and to contain high-severity incidents | Acknowledge: [minutes]. Contain: [hours] (n = [SEV-1 and SEV-2 incidents]) | [three values; word] | From MDR go-live: acknowledge within 15 minutes, contain within 4 hours | [status] | SEV-1: [count]; SEV-2: [count] (KPI-17) |
| KPI-19 Restore tests meeting target recovery times (%) | [value] (n = [tests]) | [three values; word] | Every scheduled test run; 90 percent meet their recovery time objective from Phase 4 | [status] | [note] |

## IT service

| KPI | Current | Trend (last 3 months) | Target (proposal) | Status | Note |
|---|---|---|---|---|---|
| KPI-20 Service desk tickets resolved within target (%) | [value] | [three values; word] | 85 percent from Phase 3; 90 by M7 | [status] | [note] |
| KPI-21 Employee satisfaction with IT support (CSAT) | [value] (response rate: [value]) | [three values; word] | 90 percent by M7 | [status] | [note] |
| KPI-22 New hires fully productive on day one (%) | [value] (n = [hires]) | [three values; word] | 90 percent by M6; 95 by M7 | [status] | [note] |

## Watch

[Catalog KPIs not on this page that are Off track this month, one line each with owner and next step, or "None".]

## Top risks: movement

| Risk | Owner | Last month | Now | Movement | Why | Next step |
|---|---|---|---|---|---|---|
| [R-xx and its name] | [executive owner] | [rating] | [rating] | [Up, Down, New, Closed, or Flagged] | [reason, citing the KPI or supporting check] | [action and date] |

## Decisions needed

| # | Decision | Options | Recommendation | Decision owner | Needed by |
|---|---|---|---|---|---|
| 1 | [decision] | [options] | [recommendation] | [executive role] | [date] |

## Status key

| Status | Rule (proposal, approved with the targets at M3) |
|---|---|
| On track | At or better than the target, or than this month's interim target |
| At risk | Below the interim target by no more than the KPI's tolerance (default: 5 percentage points for percentages, 20 percent for times and counts), or worse two months running |
| Off track | Below the interim target by more than the tolerance, or a milestone (M4 to M7) will be missed without a decision |
| Baseline only | No approved target yet (before M3), or the first month on a new data source |
| No data yet | Not measurable yet; the note gives the date of the first value |

Where more than one rule applies, the less favorable status applies.

Abbreviations: MFA, multifactor authentication; MDR, managed detection and response; CSAT, customer satisfaction score; SEV-1 and SEV-2, the two most serious incident severity levels in document [08](../08-detection-and-incident-response.md). SOC 2 is the attestation report on Fabrikam's controls that customers ask for.

## Sources

- Measurement Guide for Information Security: Volume 1, Identifying and Selecting Measures (NIST SP 800-55v1, December 2024), Sec. 3.1.1 (final and interim targets) and Sec. 3.1.2 (context in measurement reports). NIST. https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-55v1.pdf . Checked 2026-10-13. Primary.
- The NIST Cybersecurity Framework (CSF) 2.0 (CSWP 29), Sec. 5.1 (key performance and key risk indicators for executives). NIST. https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf . Checked 2026-10-13. Primary.
