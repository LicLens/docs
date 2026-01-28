# CIS Microsoft 365 Foundations Benchmark

140 prescriptive security controls across nine Microsoft 365 service areas. 365TUNE automatically scans all automated controls without configuration required. Industry-standard framework recognized by auditors globally.

### Control Sections

#### Section 1: Microsoft 365 Admin Center (\~15 controls)

* Administrative account separation
* Shared mailbox sign-in blocking
* Modern authentication enforcement
* Audit log search enabled
* Public group management
* Customer lockbox

#### Section 2: Microsoft 365 Defender (\~20 controls)

* Safe Links for Office apps (L2, E5)
* Safe Attachments (L2, E5)
* Common attachment filter (L1, E3)
* DLP for Teams (L1, E3)
* SPF records (L1, E3)
* DKIM signing (L1, E3)
* DMARC enforcement (L1, E3)

#### Section 3: Microsoft Purview (\~15 controls)

* Audit logging enabled
* Mailbox auditing
* Group creation restrictions

#### Section 4: Data Management (\~15 controls)

* Sensitivity labels (L2, E5)
* DLP policies (L2, E5)
* Safe Links for Office (L2, E5)

#### Section 5: Microsoft Entra Admin Center (\~25 controls)

* MFA for all users (L1, E3)
* Risk-based MFA (L2, E5)
* Security Defaults disabled when using CA (L1, E3)
* 2-4 Global Administrators (L1, E3)
* Legacy authentication blocked (L1, E3)
* Password protection (L2, E5)
* Guest user reviews (L2, E3)
* PIM for roles (L2, E5)

#### Section 6: SharePoint Admin Center (\~15 controls)

* External calendar sharing disabled (L1, E3)
* External sharing restricted (L2, E3)
* Link expiration configured (L2, E3)
* Domain allow/block lists (L2, E3)
* "Everyone" sharing audited (L1, E3)

#### Section 7: Mobile Device Management (\~10 controls)

* Advanced security configurations (L2, E3)
* Password requirements (L2, E3)
* Device encryption (L2, E3)
* Compliance policies (L2, E5)

#### Section 8: Teams Admin Center (\~15 controls)

* Channel email disabled (L2, E3)
* External control restricted (L2, E3)
* Guest file sharing limited (L2, E3)
* Anonymous meeting join blocked (L1, E3)
* External file sharing restricted (L2, E3)

#### Section 9: Microsoft Fabric (Power BI) (\~10 controls)

* Publish to web disabled (L1, E3)
* Workspace creation restricted (L2, E3)
* Guest access limited (L2, E3)
* Data export restricted (L2, E3)

### Compliance Mappings

Single assessment covers multiple frameworks:

* NIST Cybersecurity Framework (CSF)
* NIST SP 800-53
* NIST SP 800-171
* ISO/IEC 27001:2022
* PCI DSS
* HIPAA
* SOC 2
* CMMC
* FedRAMP
* FISMA
* GLBA
* SOX

### Control Structure

Each control includes:

* ID number (e.g., 5.1.1.1)
* Title and description
* Level (L1/L2) and licensing (E3/E5)
* Assessment status (Automated/Manual)
* Rationale
* Audit instructions
* Remediation steps
* Impact analysis
* Default values

### Assessment Process

**Automated Controls:** 365TUNE executes via PowerShell, Microsoft Graph API, Exchange/SharePoint/Teams/Power BI management modules.

### Output

**Compliance Dashboard:**

* Overall compliance percentage
* Level breakdown (L1: 85%, L2: 68%)
* Licensing breakdown (E3: 92%, E5: 71%)
* Section scores (Admin 80%, Defender 75%, etc.)

**Control Results:**

* CIS control number
* Pass/fail status
* Configuration evidence
* Compliance framework mappings (NIST, ISO, PCI, etc.)
* Remediation steps with PowerShell commands
* Impact analysis

***

### Use Cases

**Baseline Implementation:** Run L1 assessment, export failed controls, prioritize remediation, validate fixes.

**Audit Preparation:** Generate compliance reports, control mappings, configuration evidence, exception documentation.

**Continuous Compliance:** Weekly scans, alert on regressions, track trends, monthly executive reports.

**Multi-Framework Compliance:** Single assessment covers NIST, ISO 27001, PCI DSS with unified remediation.

***

### Required Permissions

Read-only:

* Policy.Read.All
* Policy.Read.ConditionalAccess
* Directory.Read.All
* RoleManagement.Read.All
* UserAuthenticationMethod.Read.All
* DeviceManagementConfiguration.Read.All
* DeviceManagementManagedDevices.Read.All
* Exchange/SharePoint/Teams: View-only
* Power BI: Administrator (read-only)
* Intune: Read-only Operator

***

### Licensing Requirements

| Section        | Minimum          | Notes                              |
| -------------- | ---------------- | ---------------------------------- |
| 1 (Admin)      | M365 E3          | All controls                       |
| 2 (Defender)   | M365 E3          | Some L2 require E5/Defender Plan 2 |
| 3 (Purview)    | M365 E5          | Most require E5                    |
| 4 (Data)       | M365 E5          | Advanced DLP requires E5           |
| 5 (Entra)      | M365 E3          | Risk controls require E5/P2        |
| 6 (SharePoint) | M365 E3          | All controls                       |
| 7 (MDM)        | M365 E3 + Intune | Intune Plan 1 minimum              |
| 8 (Teams)      | M365 E3          | All controls                       |
| 9 (Power BI)   | Power BI Pro     | Some require Premium               |

***

### Reference

* [CIS Microsoft 365 Benchmark](https://www.cisecurity.org/benchmark/microsoft_365)
* [CIS Controls](https://www.cisecurity.org/controls)
* [Microsoft 365 Security](https://learn.microsoft.com/en-us/microsoft-365/security/)
