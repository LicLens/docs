# CIS Microsoft 365 Foundations Benchmark

Under CIS Microsoft 365 Foundations Benchmark, 365TUNE automatically scans \~25 automated controls. Industry-standard framework recognized by auditors globally. CIS Microsoft 365 Foundations Benchmark is one of the 4 four frameworks 365TUNE supports.

### Control Sections

#### Section 1: Admin Center (\~15 controls)

* Administrative account separation (L1, E3)
* Shared mailbox sign-in blocking (L1, E3)
* Modern authentication enforcement (L1, E3)
* Audit log search enabled (L2, E3)
* Public group management (L1, E3)
* Customer lockbox (L2, E3)

#### Section 2: Defender (\~20 controls)

* Safe Links for Office apps (L2, E5)
* Safe Attachments (L2, E5)
* Common attachment filter (L1, E3)
* DLP for Teams (L1, E3)
* SPF records (L1, E3)
* DKIM signing (L1, E3)
* DMARC enforcement (L1, E3)
* Anti-malware notifications (L1, E3)

#### Section 3: Purview (\~15 controls)

* Audit logging enabled (L2, E5)
* Mailbox auditing (L2, E5)
* Group creation restrictions (L2, E5)

#### Section 4: Data Management (\~15 controls)

* Sensitivity labels (L2, E5)
* DLP policies (L2, E5)
* Safe Links for Office (L2, E5)
* Information protection (L2, E5)

#### Section 5: Entra Admin Center (\~25 controls)

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

#### Section 9: Power BI (\~10 controls)

* Publish to web disabled (L1, E3)
* Workspace creation restricted (L2, E3)
* Guest access limited (L2, E3)
* Data export restricted (L2, E3)

***

### Automated vs. Manual Controls

**Automated (\~25 controls):** 365TUNE executes via PowerShell and Microsoft Graph API.

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

### Use Cases

**Baseline Implementation:** L1 assessment, gap analysis, phased remediation, validation.

**Audit Preparation:** Compliance reports, control mappings, configuration evidence.

**Continuous Compliance:** Weekly scans, regression monitoring, trend analysis.

**Multi-Framework Compliance:** Single assessment for NIST, ISO 27001, PCI DSS.

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

### Reference

* [CIS Microsoft 365 Benchmark](https://www.cisecurity.org/benchmark/microsoft_365)
* [CIS Controls](https://www.cisecurity.org/controls)
* [Microsoft 365 Security](https://learn.microsoft.com/en-us/microsoft-365/security/)
