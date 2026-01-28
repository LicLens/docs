# Entra ID Security Config Analyzer

45 security configuration controls mapping to documented adversary techniques. 365TUNE automatically scans all EIDSCA controls. Each control derived from offensive security research with MITRE ATT\&CK mappings.

### Attack-Informed Approach

Controls derived from real attack scenarios:

1. Adversary technique documented
2. Entra ID configuration enabling technique identified
3. Secure configuration defined
4. MITRE ATT\&CK mapping established
5. Control added to baseline

### MITRE ATT\&CK Mappings

All 45 EIDSCA tests mapped to adversary techniques:

| Technique                    | EIDSCA Controls                            | Attack Vector           |
| ---------------------------- | ------------------------------------------ | ----------------------- |
| T1566 (Phishing)             | Authentication hardening, MFA              | Credential harvesting   |
| T1078 (Valid Accounts)       | Authorization policies, guest restrictions | Compromised credentials |
| T1110 (Brute Force)          | Smart lockout, password protection         | Password spray          |
| T1528 (Token Theft)          | Consent policies, admin workflow           | OAuth token theft       |
| T1556 (Auth Modification)    | Authentication method policies             | Auth bypass             |
| T1098 (Account Manipulation) | Authorization policies                     | Privilege escalation    |

### Control Categories

#### FIDO2 Security Keys (6 tests: AF01–AF06)

* Attestation enforcement
* Enforce attestation for registrations
* Manufacturer restrictions
* Self-service credential management

#### General Authentication (3 tests: AG01–AG03)

* Security defaults configuration
* Legacy authentication settings
* Authentication method registration

#### Microsoft Authenticator (8 tests: AM01–AM10)

* Passwordless authentication enabled
* Number matching required
* Additional context display
* Application ID display
* Geographic location display
* Companion app restrictions
* Registration campaign settings

#### Default Authorization (10 tests: AP01–AP14)

* Users can register applications
* Users can consent to apps
* Users can create security groups
* Users can add guests
* Guest user permissions
* Guest invite restrictions
* LinkedIn account connections
* Collaboration restrictions

#### SMS Authentication (1 test: AS04)

* SMS restricted to MFA only (not primary auth)

#### Temporary Access Pass (2 tests: AT01–AT02)

* One-time use enforced
* Maximum lifetime restrictions

#### Voice Authentication (1 test: AV01)

* Voice call authentication restricted

#### Consent Policy (3 tests: CP01–CP04)

* User consent settings
* Risk-based consent
* Publisher verification enforcement

#### Admin Consent Request (4 tests: CR01–CR04)

* Workflow enabled
* Multiple reviewers configured
* Request expiration
* Justification required

#### Password Protection (5 tests: PR01–PR06)

* Custom banned password list
* Global banned list enabled
* Smart lockout threshold
* Lockout duration
* Password protection mode (enforced vs. audit)

#### M365 Groups (2 tests: ST08–ST09)

* Group creation restrictions
* Group naming policies

### Risk Scoring

**Severity Levels:**

* Critical: Common attacks with active exploitation
* High: Frequent attack vectors
* Medium: Defense-in-depth controls
* Low: Additional hardening

**Risk Classifications:**

* Critical: 85+ (immediate action)
* High: 70-84 (urgent remediation)
* Medium: 50-69 (planned remediation)
* Low: <50 (acceptable with monitoring)

### Use Cases

**Threat-Informed Review:** Assess against threat landscape, prioritize by active threats, implement defenses.

**Post-Breach Hardening:** Analyze attack chain, identify preventive controls, implement in priority order.

**SOC Integration:** Export to SIEM, correlate failures with incidents, automated alerts.

**Red Team Preparation:** Pre-exercise assessment, identify attack paths, validate post-exercise.

### Security Incident Integration

**Incident Correlation:** 365TUNE correlates EIDSCA failures with security incidents:

**Example 1: Compromised Credential**

* Incident: Impossible travel sign-in
* EIDSCA: Risk-based CA policy not enforced
* Action: Immediate policy remediation + credential reset

**Example 2: Malicious OAuth App**

* Incident: Suspicious app consent
* EIDSCA: Users can consent to unverified publishers
* Action: Disable user consent + revoke app

**Example 3: Password Spray**

* Incident: Multiple failed sign-ins
* EIDSCA: Lockout threshold too high
* Action: Lower threshold + enable banned list

### Required Permissions

Read-only:

* Policy.Read.All
* Policy.Read.ConditionalAccess
* Directory.Read.All
* UserAuthenticationMethod.Read.All
* Organization.Read.All
* Domain.Read.All

### Reference

* [AzureAD-Attack-Defense](https://github.com/Cloud-Architekt/AzureAD-Attack-Defense)
* [EIDSCA Implementation](https://github.com/Cloud-Architekt/AzureAD-Attack-Defense/blob/main/AADSecurityConfigAnalyzer.md)
* [MITRE ATT\&CK](https://attack.mitre.org/)
* [Microsoft Threat Intelligence](https://www.microsoft.com/security/blog/threat-intelligence/)
