# ADR-008: One endpoint management standard

> **Reference work.** Fictional scenario built for a public portfolio. Not deployed in, derived from, or describing any employer environment. Not professional advice.

## Status

Proposed. Date: 2026-10-13.

The Director of IT and Security proposes this decision; the executive team approves it with the plan and the Asset and Device Management Policy (POL-04) at M3.

## Context

- **Day 1 (assumption A-04).** At Fabrikam (fictional), Windows laptops are enrolled in Intune with inconsistent compliance policies. Engineering and Design use Macs that are only partly managed. Local admin rights are common, there is no LAPS, and a few Windows 10 devices remain. Staff read email and Teams on personal iOS and Android phones.
- **Acquisitions.** Some device management from the two acquisitions is still separate or duplicated, alongside separate identities, file storage, and SaaS. Document [15](../15-enterprise-systems-and-saas.md) and [ADR-005](ADR-005-acquired-company-consolidation.md) own that consolidation.
- **Conditional Access needs one trusted device signal.** CA-06 and CA-09 in document [06](../06-microsoft-365-security-baseline.md) grant access only to compliant devices. Intune can mark devices compliant on every platform. Third-party device managers can also feed compliance to Microsoft Entra ID through Microsoft's compliance partner integration, which Microsoft's partner page lists for Android, iOS/iPadOS, and macOS (not every partner supports every platform), with an Intune license still assigned to each user; Microsoft's grant-control page describes non-Microsoft management for Windows devices instead. The pages differ, but on either reading only Intune covers Windows and macOS alike.
- **Licenses already held.** Microsoft 365 E3 includes Intune Plan 1 and, since July 2026, Intune Plan 2 with Remote Help and Intune Advanced Analytics. Platform SSO for macOS is included in every Intune plan. Defender for Endpoint Plan 1 covers Windows and Mac. Intune app protection policies need a user license, which E3 provides; device-only licenses do not support them.
- **Team.** An IT Operations Manager and three IT generalists run devices, the service desk, and Microsoft 365. One toolset is what that team can operate well.
- **Audit.** Device controls are in SOC 2 scope, and the current review period closes at M4.

## Decision drivers

1. One compliance signal that Conditional Access can trust for every corporate computer (R-03, R-07).
2. Lean-team capacity: one console, one skill set, one support tool (Remote Help, already in E3).
3. Cost: use E3 entitlements and retire duplicate device management contracts (R-09).
4. macOS controls good enough for Engineering and Design: encryption with key escrow, phishing-resistant sign-in, zero-touch enrollment, a managed local admin account, Defender.
5. Personal phones: protect work data without managing the person's device.
6. SOC 2 evidence from one system, with no gap before M4.
7. Clear measures: KPI-06 (devices managed out of devices known) and KPI-10 (compliant devices).

## Options considered

### Option 1: One standard. Intune for Windows and macOS, app protection for personal phones

- **Pros:** one compliance source that Conditional Access trusts for both platforms; licensed today; Windows Autopilot and Apple automated device enrollment for zero-touch setup; BitLocker and FileVault keys escrowed; Windows LAPS, and a LAPS-managed local admin account on Macs enrolled through automated device enrollment; Platform SSO for phishing-resistant sign-in on Macs; Defender for Endpoint deployed by the same tool; enforced update deadlines for Windows and macOS; app protection on phones without enrolling them; one place for SOC 2 device evidence.
- **Cons:** some macOS features in specialist tools may go deeper than Intune's; attack surface reduction rules and Endpoint Privilege Management are Windows-only, so Mac admin elevation needs a service desk process; Macs must be new or wiped to use automated device enrollment; migration work for acquired devices.
- **Verdict:** chosen.

### Option 2: Keep the separate tools from the acquisitions

- **Pros:** no migration disruption; each team keeps familiar tools.
- **Cons:** several compliance sources, each needing its own partner connection to reach Conditional Access, if the tool offers one at all; inconsistent baselines; duplicate contracts; more consoles than the team can watch; SOC 2 evidence from several tools; the duplication behind assumption A-08 and R-09 continues.
- **Verdict:** rejected.

### Option 3: Intune for Windows plus a separate Apple-focused platform for Macs

- **Pros:** an Apple-focused platform may offer deeper macOS management or faster support for new macOS features (to be evaluated per vendor).
- **Cons:** a second console, contract, and skill set for a minority of devices; Mac compliance would reach Conditional Access through Microsoft's compliance partner integration, which makes the partner the management authority for those users, still needs an Intune license per user, and allows one partner per platform; Microsoft says it is revamping that partner process in 2026; two sets of SOC 2 evidence.
- **Verdict:** rejected for now (see Revisit when).

### Option 4: Enroll personal phones in full device management

- **Pros:** device-level controls such as a device passcode and full wipe.
- **Cons:** intrusive on personal devices; resistance from staff; more service desk work; app protection already gives the data controls needed (PIN, encryption of work data, copy and save limits, selective wipe of company data).
- **Verdict:** rejected. Company-owned phones, such as administrators' phones under [ADR-004](ADR-004-phishing-resistant-authentication-rollout.md), do enroll.

## Decision

Option 1. Intune is the single endpoint management standard for corporate Windows and macOS devices, and Intune app protection without enrollment is the standard for personal phones.

| Device class | Standard | Key controls (document 06) |
|---|---|---|
| Windows laptops | Microsoft Entra joined, enrolled through Windows Autopilot, registered by the IT hardware partner at purchase or by hardware hash upload | Compliance, BitLocker, Windows LAPS, Defender for Endpoint, ASR rules, update rings with deadlines, Windows Hello for Business |
| Macs | Apple automated device enrollment for corporate Macs (new or wiped), marked corporate | Compliance with an OS floor at the oldest macOS release Defender supports, FileVault with escrowed and rotated keys, a LAPS-managed local admin account, Platform SSO with a Secure Enclave key, Defender for Endpoint, update deadlines through Apple's declarative device management |
| Personal phones | No enrollment; Intune app protection, enforced by CA-07 | Microsoft's data protection framework, enhanced level for most staff and high level for the wave 2 group; the Company Portal app on Android; selective wipe of company data at offboarding (document [07](../07-identity-lifecycle-joiners-movers-leavers.md)) |
| Company-owned phones | Enrolled in Intune | Compliance; Authenticator passkeys for administrators (ADR-004) |

The shared phones and tablets at customers' work sites belong to customers and sit outside Fabrikam's endpoint management. Fabrikam controls what its app keeps on a device, session length, and remote sign-out of a lost device; customers secure and manage the devices (a complementary user entity control in document [10](../10-governance-and-compliance-program.md)).

Local admin rights end for everyone. Elevation on Windows and Mac goes through a service desk request with an agreed response time (document 13); developer tooling exceptions for Engineering are agreed with the Engineering Manager through the Change Advisory Board and expire.

## Consequences

**Positive**

- One compliance signal lets CA-06 and CA-09 enforce managed devices in Phase 4.
- KPI-06 and KPI-10 come from one system, and SOC 2 device evidence from one place.
- Remote Help, already licensed, serves every corporate device.
- Duplicate device management contracts from the acquisitions can end at their notice dates, which offsets part of the plan's cost.

**Negative**

- Macs outside automated device enrollment must be wiped and re-enrolled.
- Mac power users lose standing admin rights and depend on the elevation process.
- Migration waves load the service desk.
- Any macOS feature that only a specialist tool offers is unavailable unless Fabrikam revisits Option 3.

### Consequences for document 15's consolidation

- Document 15 schedules acquired devices into Intune in waves sized to service desk capacity (KPI-20): after the year-end freeze and, for devices in SOC 2 scope, after M4 or with the SOC 2 audit firm's agreement.
- **Windows devices from another tenant.** Microsoft's order matters: delete the device from the old Intune first, then deregister it from that tenant's Autopilot, then register it to Fabrikam and reprovision. Skipping steps or removing records out of order can leave orphaned or unrecoverable devices.
- **Device records.** Microsoft Entra device records are not deleted by hand before a device is reprovisioned: deleting the record loses the LAPS password stored in Microsoft Entra ID, and deleting the Intune object for a Microsoft Entra joined device removes BitLocker key protectors and leaves BitLocker suspended.
- **Macs** need to be new or wiped for automated device enrollment, so each Mac's files are confirmed in OneDrive before its wipe.
- **Personal phones** move from any acquired-company device management to Intune app protection, with no enrollment.
- **Windows 10 devices** are replaced or upgraded, not migrated (document 06's Windows 10 decision).
- **Retirement.** Each retired device management console loses its contract at the notice date, and its enterprise app, consent grants, and keys in Microsoft Entra ID are removed (R-08, R-09).
- **Inventory.** Devices known from Intune, Microsoft Entra ID, Defender, and purchase records are reconciled into one list, which sets the KPI-06 baseline at M1.

## Risks and mitigations

| Risk | Mitigation |
|---|---|
| Engineering productivity drops on Macs without admin rights | Pilot with Engineering first, with the Engineering Manager; an elevation response time; time-limited exceptions through the Change Advisory Board |
| Data loss when a Mac or PC is wiped for enrollment | Files confirmed in OneDrive before any wipe; wipe and reprovision on the same day |
| Device records deleted out of order | Microsoft's deregistration order in the runbook; no Microsoft Entra or Intune deletes outside it |
| Service desk overload during migration waves | Waves sized to KPI-20; the next wave waits if service levels slip |
| A macOS control Engineering needs is missing from Intune | Recorded as a trigger to revisit Option 3 |
| SOC 2 evidence continuity | Device migrations in scope wait for M4 or the audit firm's agreement |

## Revisit when

- Macs become a large share of the fleet, or Engineering identifies a macOS control that Intune cannot provide and that blocks a security or productivity requirement.
- Another acquisition brings a large managed fleet.
- Microsoft materially changes Intune licensing or macOS support.
- The first annual program review (M7).

## Related documents

- [06. Microsoft 365 security baseline](../06-microsoft-365-security-baseline.md) (devices section, CA-06, CA-07, CA-09)
- [15. Enterprise systems and SaaS](../15-enterprise-systems-and-saas.md) and [ADR-005](ADR-005-acquired-company-consolidation.md) (consolidation)
- [13. IT service management](../13-it-service-management.md) (endpoint standards, elevation), [07. Identity lifecycle](../07-identity-lifecycle-joiners-movers-leavers.md) (offboarding wipe), [05. Environment discovery](../05-environment-discovery.md) (device inventory), [04. Operating model, team, and budget](../04-operating-model-team-and-budget.md)
- [ADR-001](ADR-001-microsoft-365-security-licensing.md), [ADR-004](ADR-004-phishing-resistant-authentication-rollout.md)

## Sources

- How to Configure Grant Controls in Microsoft Entra. Microsoft Learn. https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-grant . Checked 2026-10-13. Primary.
- Third-party device compliance partners support in Microsoft Intune. Microsoft Learn. https://learn.microsoft.com/en-us/intune/device-security/compliance/third-party-partners . Checked 2026-10-13. Primary.
- Microsoft Intune Licensing Plans and Options. Microsoft Learn. https://learn.microsoft.com/en-us/intune/fundamentals/licensing . Checked 2026-10-13. Primary.
- Microsoft 365 Pricing and Packaging Updates. Microsoft (Licensing news). https://www.microsoft.com/en-us/licensing/news/2026-m365-packaging-pricing-updates . Checked 2026-10-13. Primary.
- Device compliance policies in Microsoft Intune. Microsoft Learn. https://learn.microsoft.com/en-us/intune/device-security/compliance/overview . Checked 2026-10-13. Primary.
- Overview of Windows Autopilot. Microsoft Learn. https://learn.microsoft.com/en-us/autopilot/overview . Checked 2026-10-13. Primary.
- Windows Autopilot registration overview. Microsoft Learn. https://learn.microsoft.com/en-us/autopilot/registration-overview . Checked 2026-10-13. Primary.
- Set up automated device enrollment (ADE) for macOS. Microsoft Learn. https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-automated-macos . Checked 2026-10-13. Primary.
- Configure Platform SSO for macOS devices. Microsoft Learn. https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/configure-platform-sso-macos . Checked 2026-10-13. Primary.
- Encrypt macOS devices with FileVault using Intune. Microsoft Learn. https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/encrypt-filevault-macos . Checked 2026-10-13. Primary.
- Encrypt Windows devices with BitLocker using Intune. Microsoft Learn. https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/encrypt-bitlocker-windows . Checked 2026-10-13. Primary.
- Overview of Windows LAPS with Microsoft Intune. Microsoft Learn. https://learn.microsoft.com/en-us/intune/device-security/laps/overview . Checked 2026-10-13. Primary.
- Microsoft Defender for Endpoint on macOS prerequisites. Microsoft Learn. https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites . Checked 2026-10-13. Primary.
- Attack surface reduction rules overview. Microsoft Learn. https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview . Checked 2026-10-13. Primary.
- Learn about using Endpoint Privilege Management with Microsoft Intune. Microsoft Learn. https://learn.microsoft.com/en-us/intune/epm/overview . Checked 2026-10-13. Primary.
- App Protection Policies Overview. Microsoft Learn. https://learn.microsoft.com/en-us/intune/app-management/protection/overview . Checked 2026-10-13. Primary.
- Manage Windows Update Ring Policies. Microsoft Learn. https://learn.microsoft.com/en-us/intune/device-updates/windows/manage-update-rings . Checked 2026-10-13. Primary.
- Configure Update Policies for Apple Devices. Microsoft Learn. https://learn.microsoft.com/en-us/intune/device-updates/apple/ . Checked 2026-10-13. Primary.
