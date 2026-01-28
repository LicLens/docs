# Community Recommended Controls

200+ automated security tests from community-driven framework. 365TUNE executes all tests automatically without scripting or configuration required. This section lists the collection of tests that have been created by the Maester community

### Test Categories

#### Maester Community Tests (76 tests)

**Test ID format:** MT.1001–MT.1085

**Conditional Access (20 tests):**

* Policy configuration validation
* Coverage gap detection
* Exclusion analysis
* Named location accuracy
* Authentication strength requirements
* Policy conflicts

**Privileged Identity Management:**

* Role assignment monitoring
* Activation requirements
* Maximum duration limits
* Approval workflow configuration

**Security Configuration:**

* Security Defaults usage
* License utilization (P1/P2)
* High-risk application detection
* Device registration settings
* Configuration drift monitoring

**Stale Reference Detection:**

* MT.1038: Deleted groups in CA policies
* MT.1066: Non-existent users/groups/roles
* MT.1067: Deleted groups in auth method policies

#### EIDSCA Integration (45 tests)

**Test ID format:** Two-letter category + number

**Authentication Methods:**

* FIDO2 security keys (6 tests)
* Microsoft Authenticator (8 tests)
* SMS/Voice restrictions (2 tests)
* Temporary Access Pass (2 tests)

**Authorization Policies (10 tests):**

* Default user permissions
* Guest access settings
* Group creation restrictions
* Application registration controls

**Consent Framework (7 tests):**

* User consent settings
* Admin consent workflow
* Publisher verification

**Password Protection (5 tests):**

* Custom banned lists
* Smart lockout configuration
* Password rule enforcement

#### CISA Integration (\~70 tests)

**Entra ID Controls (\~28 tests):**

* Legacy authentication blocking
* MFA enforcement
* Privileged role management
* Guest user restrictions
* Risk-based policies

**Exchange Online Controls (\~42 tests):**

* SPF, DKIM, DMARC
* Auto-forwarding restrictions
* Anti-phishing policies
* Mailbox auditing
* Modern authentication
* Safe Links/Attachments

#### CIS Benchmark Integration

**Estimated:** \~25 automated tests (many manual-only) **Version:** CIS v5.0.0

### Workload Coverage

#### Entra ID / Azure AD

* Conditional Access (20+ tests)
* Authentication methods (all types)
* Consent framework
* Password protection
* PIM configuration
* Security defaults
* Guest/B2B controls

#### Exchange Online

* Email authentication (SPF/DKIM/DMARC)
* SMTP settings
* Auto-forwarding controls
* Anti-spam/anti-phishing
* Safe Links/Attachments
* DLP policies
* Mailbox auditing

#### Microsoft Teams

* Meeting lobby controls
* Presenter restrictions
* Anonymous user controls
* External participant settings
* Limited coverage (meeting policies only)

#### SharePoint / OneDrive

* External sharing settings (2 tests)

#### Azure&#x20;

* Identity-focused only
* User Access Administrator checks
* No comprehensive Azure security testing

#### Intune

* Device compliance policy (1 test)
* Automatic cleanup rules (1 test)

#### Microsoft Defender

* Defender for Identity health (1 test)
* Credential exposure detection (1 test)
* Critical Asset Management (1 test)

### Key Capabilities

#### Conditional Access What-If Analysis

Simulates sign-ins against CA policies programmatically. Tests:

* User/group targeting
* Application access
* Location-based rules
* Risk-based conditions
* Device platform requirements
* Expected grant controls

#### Stale Reference Detection

Identifies policies referencing deleted objects:

* Deleted security groups
* Removed users
* Non-existent roles
* Decommissioned applications

Prevents policy evaluation errors and access issues.

#### License-Aware Testing

Automatically detects tenant licensing:

* Entra ID Free, P1, P2
* M365 E3, E5
* EMS E3, E5

Tests requiring unavailable licenses skip (not fail) with license upgrade guidance.

### Compliance Mappings

**MITRE ATT\&CK:** All 45 EIDSCA tests mapped to adversary techniques:

* T1078 (Valid Accounts)
* T1110 (Brute Force)
* T1566 (Phishing)
* T1528 (Steal Application Access Token)
* T1556 (Modify Authentication Process)
* T1098 (Account Manipulation)

**Compliance Frameworks:**

* CISA SCuBA baseline
* CIS Microsoft 365 Benchmark v5.0.0
* NIST Cybersecurity Framework
* EIDSCA (Entra ID Attack and Defense)

### Use Cases

**Security Assessment:** Comprehensive scan, gap identification, remediation prioritization.

**Continuous Monitoring:** Daily scans, drift detection, alert on new failures.

**Pre-Deployment Validation:** What-If analysis before CA policy deployment, impact assessment.

**Audit Preparation:** Compliance reports with evidence, historical tracking.

### Required Permissions

Read-only:

* Policy.Read.All
* Policy.Read.ConditionalAccess
* Directory.Read.All
* IdentityRiskEvent.Read.All
* RoleManagement.Read.All
* UserAuthenticationMethod.Read.All
* Exchange: View-Only Organization Management
* Teams: Teams Administrator (read-only)
* Intune: DeviceManagementConfiguration.Read.All

***

### Reference

* [Maester Framework](https://maester.dev/)
* [Microsoft Graph API](https://learn.microsoft.com/en-us/graph/api/overview)
* [Conditional Access](https://learn.microsoft.com/en-us/entra/identity/conditional-access/)
