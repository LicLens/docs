# CISA Secure Cloud Business Applications

CISA Secure Cloud Business Applications is a Security baseline with 65-85 controls across seven Microsoft 365 workloads. 365TUNE automatically scans all CISA controls. Direct mappings to NIST SP 800-53 Rev. 5 and MITRE ATT\&CK.

### Workload Coverage

#### Microsoft Entra ID (MS.AAD) — \~28 controls

**Legacy Authentication:**

* MS.AAD.1.1v1: Block legacy authentication protocols
* Detection of Basic Auth, IMAP, POP, SMTP AUTH
* Legacy protocol usage monitoring

**Multi-Factor Authentication:**

* MS.AAD.2.1v1: Phishing-resistant MFA for privileged users
* MS.AAD.2.2v1: MFA required for all users
* Authentication method configuration

**Conditional Access:**

* MS.AAD.3.1v1: Minimum CA policy deployment
* MS.AAD.3.2v1: Block high-risk sign-ins
* MS.AAD.3.3v1: Block high-risk users
* Policy coverage validation

**Privileged Roles:**

* MS.AAD.4.1v1: Limited Global Administrator assignments
* MS.AAD.4.2v1: Dedicated cloud-only admin accounts
* MS.AAD.4.3v1: Privileged role activation requirements
* Emergency access configuration

**Guest Access:**

* MS.AAD.5.1v1: Guest invitation restrictions
* MS.AAD.5.2v1: Limited guest permissions
* MS.AAD.5.3v1: Guest access reviews
* B2B collaboration policies

**Sign-In Risk:**

* MS.AAD.6.1v1: Risk-based access policies
* MS.AAD.6.2v1: High-risk sign-in blocking
* MS.AAD.6.3v1: Risk remediation requirements

#### Exchange Online (MS.EXO) — \~42 controls

**Email Authentication:**

* MS.EXO.1.1v1: SPF records for all domains
* MS.EXO.1.2v1: DKIM signing enabled
* MS.EXO.1.3v1: DMARC policy enforced
* MS.EXO.1.4v1: External sender identification

**Automatic Forwarding:**

* MS.EXO.2.1v1: External forwarding disabled
* MS.EXO.2.2v1: Transport rules reviewed
* MS.EXO.2.3v1: Client-side forwarding restrictions
* Audit logging enabled

**Anti-Phishing:**

* MS.EXO.3.1v1: Impersonation protection
* MS.EXO.3.2v1: Mailbox intelligence
* MS.EXO.3.3v1: Advanced phishing thresholds
* MS.EXO.3.4v1: User impersonation list

**Mailbox Auditing:**

* MS.EXO.4.1v1: Enabled for all users
* MS.EXO.4.2v1: Log retention configured
* MS.EXO.4.3v1: Admin actions logged
* Alert configuration

**DLP Policies:**

* MS.EXO.6.1v1: Cover sensitive data
* MS.EXO.6.2v1: Incident alerts configured
* MS.EXO.6.3v1: All users in scope

**Additional Controls:**

* SMTP authentication restrictions
* Contact folder sharing
* MailTips configuration
* Outlook add-in policies

#### SharePoint Online (MS.SHAREPOINT)

**Currently Implemented:**

* MS.SHAREPOINT.1.1v1: External sharing restrictions
* MS.SHAREPOINT.1.3v1: Default link settings.

#### Microsoft Teams (MS.TEAMS)

Teams controls implemented:

* Meeting lobby requirements
* Anonymous join restrictions
* External participant controls
* Presenter role limitations

#### Microsoft Defender (MS.DEFENDER)

Defender controls implemented:

* Safe Attachments (via Exchange)
* Safe Links (via Exchange)
* Credential exposure detection

### Compliance Mappings

#### NIST SP 800-53 Rev. 5

| CISA Control | NIST Control     | Description                 |
| ------------ | ---------------- | --------------------------- |
| MS.AAD.1.1v1 | IA-2(1), IA-2(2) | Multi-factor authentication |
| MS.EXO.1.1v1 | SI-8             | Spam protection             |
| MS.EXO.4.1v1 | AU-2, AU-12      | Audit generation            |
| MS.AAD.3.1v1 | AC-3, AC-6       | Access enforcement          |

#### MITRE ATT\&CK

Over 6,300 technique mappings via MITRE Center for Threat-Informed Defense:

* T1078 (Valid Accounts) → MS.AAD.2.x (MFA)
* T1110 (Brute Force) → MS.AAD.3.x, MS.AAD.6.x (Risk blocking)
* T1566 (Phishing) → MS.EXO.3.x (Anti-phishing)
* T1114 (Email Collection) → MS.EXO.2.x, MS.EXO.4.x (Forwarding, auditing)

***

### Assessment Process

1. **Data Collection:** Microsoft Graph API, Exchange Online PowerShell
2. **Policy Evaluation:** Compare against CISA baseline requirements
3. **Classification:** Pass/Fail/Warning/Not Applicable with severity
4. **Reporting:** Baseline compliance summary

**Execution:** On-demand, scheduled, continuous monitoring

**License Detection:** Controls requiring unavailable licenses marked.

### Use Cases

**Baseline Compliance:** Assessment, compliance reporting, evidence for audit.

**Security Hardening:** Identify SHALL failures, prioritize remediation, validate fixes.

**Continuous Monitoring:** Daily scans for SHALL controls, alerts for failures, trend tracking.

### Required Permissions

Read-only:

* Policy.Read.All
* Policy.Read.ConditionalAccess
* Directory.Read.All
* IdentityRiskEvent.Read.All
* RoleManagement.Read.All
* UserAuthenticationMethod.Read.All
* Reports.Read.All
* Exchange: View-Only Organization Management
* Defender: Security Reader

### Reference

* [CISA SCuBA Project](https://www.cisa.gov/scuba)
* [SCuBA GitHub](https://github.com/cisagov/ScubaGear)
* [NIST SP 800-53](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final)
* [MITRE ATT\&CK](https://attack.mitre.org/)
