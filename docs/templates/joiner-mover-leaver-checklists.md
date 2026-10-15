# Joiner, mover, and leaver checklists

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

These checklists put document [07](../07-identity-lifecycle-joiners-movers-leavers.md) into practice for Fabrikam (fictional). Each step names an owner role and the system where it happens. Steps marked "(automated)" are run by Lifecycle Workflows, entitlement management, or SCIM provisioning; the named owner watches for failures. When automation is unavailable, the owner performs the step by hand from this list, which is the manual fallback in [ADR-002](../adr/ADR-002-hr-system-of-record-drives-identity.md). Every timing is a proposal to be tuned after discovery.

Owner roles are those in document [04](../04-operating-model-team-and-budget.md), plus the People team (the VP of People's organization), the manager, the sponsor (the Fabrikam employee accountable for a contractor or guest), the system owner (the business owner of an application), and the new hire. SRE means Site Reliability Engineering, and PIM means Privileged Identity Management.

The company does not hire a Security Engineer or a GRC Analyst. The Director of IT and Security covers the security-engineering steps, and the Director with the outside audit-readiness consultant covers the GRC and SOC 2 steps (documents [03](../03-twelve-month-roadmap.md) and 04).

## Joiner

Steps J9, D1, and D2 cite R-15 from document [11](../11-risk-management.md), "A fraudulent remote hire passes onboarding and receives credentials" (proposed risk owner: VP of People).

### Before day 1

| # | Step | Owner role | System |
|---|---|---|---|
| J1 | Enter the hire at least five business days before the start date: worker ID, start date and time, worker type, department, job family, manager, and country | People team | HR system |
| J2 | (automated) Account created disabled and matched on worker ID | Systems Engineer (Identity and Endpoint) | Inbound provisioning, Microsoft Entra ID |
| J3 | Clear the new hire from the daily reconciliation report, fixing any missing data at the source | Service Desk Analyst | Reconciliation report, HR system |
| J4 | (automated) License group and birthright access packages assigned | Systems Engineer (Identity and Endpoint) | Group-based licensing, entitlement management |
| J5 | Allocate the laptop, register it for Windows Autopilot or Apple automated device enrollment, and ship it to arrive before day 1 | Service Desk Analyst, with the IT hardware partner | ITSM tool, Intune |
| J6 | Request role-specific access that birthright does not cover; the resource owner approves sensitive, request-only packages only after the D2 result is on the joiner ticket | Manager | My Access portal |
| J7 | Create accounts in apps without SCIM from the automatic ticket | System owner | App admin console, ITSM tool |
| J8 | (automated from Phase 4) Single-use Temporary Access Pass, valid for two hours from the start time, emailed to the manager one day before the start date; the manager holds it until D2 passes. Until the workflow runs, the Service Desk Analyst creates the pass during the D2 call and gives it only after D2 passes, never by email (documents 07 and 13) | Systems Engineer (Identity and Endpoint); Service Desk Analyst for the manual pass | Lifecycle Workflows; Microsoft Entra ID for the manual pass |
| J9 | Record the legal name exactly as it appears on the identity document the new hire will show, and confirm that background screening, where the role requires it, raised no identity mismatch (R-15) | People team | HR system |

### Day 1

| # | Step | Owner role | System |
|---|---|---|---|
| D1 | Enable the account only after the verifier records the D2 result on the joiner ticket; until then it stays disabled, even past the start time (R-15) | Service Desk Analyst | Microsoft Entra ID, ITSM tool |
| D2 | Identity check before the pass (R-15; red flags in document 07): on a one-to-one video call with cameras on and no background effects, the new hire holds an unexpired government-issued photo ID beside their face and follows unscripted prompts; the verifier compares face, name, and date of birth with the document and the HR record, and the manager confirms this is the person they interviewed. Record the result on the joiner ticket at once; only then is the account enabled (D1) and the pass given; on any red flag, stop and report a security event | Trained People team member, with the manager (the sponsor for a contractor) | Microsoft Teams, ITSM tool, HR system |
| D3 | Still on the D2 call, sign in on the laptop with the pass and register a passkey, Windows Hello for Business, or the macOS platform credential; register no SMS or voice method | New hire, with the Service Desk Analyst on standby | Microsoft Entra ID, Windows Autopilot or Apple automated device enrollment |
| D4 | Accept the Acceptable Use Policy (POL-02) at first sign-in | New hire | Conditional Access terms of use |
| D5 | (automated) Accounts created in SCIM-connected apps | Systems Engineer (Identity and Endpoint) | Microsoft Entra provisioning service |
| D6 | Welcome check: device compliant; mail, Teams, and core apps working; any gap logged on the joiner ticket | Service Desk Analyst | ITSM tool, Intune |
| D7 | If the pass fails or has expired, issue a new one only after the D2 check is on record and the caller is verified (document [13](../13-it-service-management.md)) | Service Desk Analyst | Microsoft Entra ID, ITSM tool |
| D8 | Record the D2 result, method, verifier, and time on the joiner ticket and in the HR system; never record the call or keep an image of the document | People team | ITSM tool, HR system |

### Week 1

| # | Step | Owner role | System |
|---|---|---|---|
| W1 | (automated) Team groups and Teams added | Systems Engineer (Identity and Endpoint) | Lifecycle Workflows |
| W2 | Complete onboarding security training | New hire | Training platform (document [09](../09-security-awareness-and-training.md)) |
| W3 | Confirm the new hire has what they need (input to KPI-22) | Manager | ITSM tool survey |
| W4 | Close the joiner ticket; log any failed step as a defect against the workflow or the process | IT Operations Manager | ITSM tool |

## Mover

| # | Step | Owner role | System |
|---|---|---|---|
| M1 | Record the change and its effective date: department, job family, manager, worker type, or country | People team | HR system |
| M2 | (automated) Attributes updated | Systems Engineer (Identity and Endpoint) | Inbound provisioning |
| M3 | (automated) New birthright packages assigned; old ones removed after a seven-day handover grace | Systems Engineer (Identity and Endpoint) | Entitlement management |
| M4 | If the license changes, add the new license group before removing the old one | Systems Engineer (Identity and Endpoint) | Group-based licensing |
| M5 | Mover review: confirm or remove each item of request-based access within 10 business days; unconfirmed items are removed | Manager (new) | Access reviews or ITSM review task |
| M6 | Re-approve or remove administrator roles | Director of IT and Security | PIM |
| M7 | Re-approve or remove production access | Engineering Manager | Engineering's access process |
| M8 | Transfer ownership of groups, Teams, SharePoint sites, and app registrations the person no longer needs | Manager (previous) | Microsoft Entra ID, Microsoft 365 |
| M9 | Change the devices or apps the new role needs | Service Desk Analyst | ITSM tool, Intune |

## Standard leaver

### Before the last day

| # | Step | Owner role | System |
|---|---|---|---|
| L1 | Enter the last working day and time on the day notice is given | People team | HR system |
| L2 | (automated) Leave date set | Systems Engineer (Identity and Endpoint) | Inbound provisioning |
| L3 | (automated) Pre-offboarding notice to the manager seven days before the last day | Systems Engineer (Identity and Endpoint) | Lifecycle Workflows |
| L4 | Transfer ownership of groups, Teams, SharePoint sites, app registrations, service accounts, and mailbox delegations | Manager, with the leaver | Microsoft Entra ID, Microsoft 365 |
| L5 | Arrange device return with a prepaid return | Service Desk Analyst | ITSM tool, IT hardware partner |

### At the end of the last working day

| # | Step | Owner role | System |
|---|---|---|---|
| L6 | (automated) Account disabled, refresh tokens revoked, access packages removed, pending requests cancelled, groups and Teams removed | Systems Engineer (Identity and Endpoint) | Lifecycle Workflows |
| L7 | (automated) Accounts in SCIM-connected apps deprovisioned | Systems Engineer (Identity and Endpoint) | Microsoft Entra provisioning service |
| L8 | Remove access in apps without SCIM within one business day | System owner | App admin console, ITSM tool |
| L9 | Remove product production access and internal support tooling access; confirm in the ticket | SRE lead | Product cloud access tooling, support tooling |
| L10 | If the person held administrator roles: disable admin accounts, remove PIM assignments, and validate the emergency access accounts | Systems Engineer (Identity and Endpoint) | Microsoft Entra ID, PIM (document [06](../06-microsoft-365-security-baseline.md)) |
| L11 | If Fabrikam acts as an E-Verify employer agent and the person had program access, remove it | System owner | E-Verify (see document 07) |

### After the last day

| # | Step | Owner role | System |
|---|---|---|---|
| L12 | Recover the device before deleting any device record (BitLocker key protectors, LAPS password, FileVault keys), then use Autopilot Reset or sanitize it under POL-04 | Service Desk Analyst | Intune, Microsoft Entra ID |
| L13 | Handle the mailbox and OneDrive under POL-15 and give the manager what they need | Manager, with the Service Desk Analyst | Exchange Online, OneDrive |
| L14 | (automated) Account deleted 30 days after the last day, once handover is confirmed | Systems Engineer (Identity and Endpoint) | Lifecycle Workflows |
| L15 | Compare leave time with disable time for KPI-12 and review any miss | IT Operations Manager | Reconciliation report, workflow history |

## Urgent leaver

Target: Microsoft Entra ID access ends within one hour of notice.

| # | Step | Owner role | System |
|---|---|---|---|
| U1 | Phone the IT Operations Manager or the on-call contact and open an urgent ticket; the call time starts the clock | People team or General Counsel | Phone, ITSM tool |
| U2 | Have a second team member confirm the person's identity, then run the on-demand leaver workflow, timed to the conversation | Service Desk Analyst or IT Operations Manager | Lifecycle Workflows |
| U3 | Disable the person's registered devices and remotely lock corporate devices; wipe only on a decision by the Director of IT and Security with General Counsel | IT Operations Manager | Microsoft Entra ID, Intune |
| U4 | Disable admin accounts and remove PIM assignments, if any | Systems Engineer (Identity and Endpoint) | Microsoft Entra ID, PIM |
| U5 | Remove production and support tooling access within the hour | SRE lead | Product cloud access tooling, support tooling |
| U6 | Remove finance and payroll system access within the hour | Finance manager | Finance and accounting system, HR system |
| U7 | Rotate shared secrets the person knew in the enterprise password vault, and change the safe combinations for the emergency access keys if they had access (document 06) | Director of IT and Security | Credential vault (document 06) |
| U8 | Apply General Counsel's holds before any deletion and pause the post-offboarding deletion | IT Operations Manager | Microsoft 365 retention (POL-15) |
| U9 | Alert on sign-in attempts against the disabled account for 30 days | Director of IT and Security, with the MDR provider once live if it triages custom detections, and the on-call rotation in document [08](../08-detection-and-incident-response.md) | Microsoft Entra sign-in logs |
| U10 | Close the ticket with timestamps for KPI-12 | IT Operations Manager | ITSM tool |

## Contractor end

| # | Step | Owner role | System |
|---|---|---|---|
| C1 | Make sure every contractor record carries a sponsor and an end date; no end date, no account | People team | HR system |
| C2 | (automated) Notify the sponsor 14 days before the end date | Systems Engineer (Identity and Endpoint) | Lifecycle Workflows |
| C3 | To extend, enter the new end date in HR before the old one passes and re-approve sensitive access for the new term | Sponsor | HR system, My Access portal |
| C4 | At the end date, run standard leaver steps L6 to L11, automated where possible | Systems Engineer (Identity and Endpoint) | Lifecycle Workflows |
| C5 | Recover Fabrikam equipment and confirm data is returned or destroyed under the contract | Sponsor, with the Service Desk Analyst | ITSM tool |
| C6 | Tell the contracting firm that access has ended and close the engagement under POL-10 | Sponsor, with the Director of IT and Security and the outside audit-readiness consultant | Third-party records |

## Sources

- Lifecycle Workflows templates and categories. Microsoft Learn. https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-templates . Checked 2026-10-13. Primary.
- Lifecycle Workflows tasks and definitions. Microsoft Learn. https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-tasks . Checked 2026-10-13. Primary.
- Configure an automatic assignment policy for an access package in entitlement management. Microsoft Learn. https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-access-package-auto-assignment-policy . Checked 2026-10-13. Primary.
- Assign or unassign licenses to a group in the Microsoft 365 admin center. Microsoft Learn. https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-group-licenses . Checked 2026-10-13. Primary.
- Revoke user access in an emergency in Microsoft Entra ID. Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/users/users-revoke-access . Checked 2026-10-13. Primary.
- Configure a Temporary Access Pass in Microsoft Entra ID to register passwordless authentication methods. Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-temporary-access-pass . Checked 2026-10-13. Primary.
- Manage emergency access admin accounts. Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/security-emergency-access . Checked 2026-10-13. Primary.
- Overview of Windows Autopilot. Microsoft Learn. https://learn.microsoft.com/en-us/autopilot/overview . Checked 2026-10-13. Primary.
- Set up automated device enrollment (ADE) for macOS. Microsoft Learn. https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-automated-macos . Checked 2026-10-14. Primary.
- Configure Platform SSO for macOS devices (Secure Enclave setup can start with a Temporary Access Pass). Microsoft Learn. https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/configure-platform-sso-macos . Checked 2026-10-14. Primary.
- Encrypt Windows devices with BitLocker using Intune. Microsoft Learn. https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/encrypt-bitlocker-windows . Checked 2026-10-13. Primary.
- Overview of Windows LAPS with Microsoft Intune. Microsoft Learn. https://learn.microsoft.com/en-us/intune/device-security/laps/overview . Checked 2026-10-13. Primary.
- Encrypt macOS devices with FileVault using Intune. Microsoft Learn. https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/encrypt-filevault-macos . Checked 2026-10-13. Primary.
- NIST SP 800-88 Rev. 2, Guidelines for Media Sanitization. NIST. https://csrc.nist.gov/pubs/sp/800/88/r2/final . Checked 2026-10-13. Primary.
- The E-Verify Memorandum of Understanding for Employer Agents (Revision Date 06/01/2013). DHS, USCIS E-Verify program. https://www.e-verify.gov/sites/default/files/everify/memos/MOUforEVerifyEmployerAgents.pdf . Checked 2026-10-13. Primary (this revision; a newer revision was not ruled out on the check date).
