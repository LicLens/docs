---
description: >-
  This article documents the Microsoft Graph API permissions required for the
  Security and Compliance module.
---

# Security and Compliance: Permissions Explained

**All permissions are read-only.** 365TUNE collects security and compliance data for reporting and analysis. No modifications are made to security policies, device configurations, or identity settings.

{% hint style="info" %}
Some permission use and analysis capabilities depend on tenant licensing. Controls requiring unavailable licenses (e.g., PIM requires Entra ID P2) are automatically skipped during the tests.
{% endhint %}

### Required Permissions

All permissions are **application type** with tenant-wide scope.

| Permission                              | Purpose                                              |
| --------------------------------------- | ---------------------------------------------------- |
| DeviceManagementConfiguration.Read.All  | Read Intune device configuration policies            |
| DeviceManagementManagedDevices.Read.All | Read managed device inventory and compliance status  |
| DeviceManagementRBAC.Read.All           | Read Intune role-based access control settings       |
| DeviceManagementServiceConfig.Read.All  | Read Intune service configuration                    |
| Directory.Read.All                      | Read directory objects (users, groups, applications) |
| DirectoryRecommendations.Read.All       | Read Microsoft Entra recommendations                 |
| IdentityRiskEvent.Read.All              | Read identity risk detections                        |
| Policy.Read.All                         | Read organization policies                           |
| Policy.Read.ConditionalAccess           | Read Conditional Access policies                     |
| PrivilegedAccess.Read.AzureAD           | Read Privileged Identity Management (PIM) settings   |
| Reports.Read.All                        | Read usage and activity reports                      |
| ReportSettings.Read.All                 | Read report configuration settings                   |
| RoleEligibilitySchedule.Read.Directory  | Read PIM role eligibility schedules                  |
| RoleManagement.Read.All                 | Read role assignments and definitions                |
| SecurityIdentitiesSensors.Read.All      | Read Microsoft Defender for Identity sensors         |
| SecurityIdentitiesHealth.Read.All       | Read Defender for Identity health data               |
| SharePointTenantSettings.Read.All       | Read SharePoint tenant configuration                 |
| ThreatHunting.Read.All                  | Read advanced threat hunting data                    |
| UserAuthenticationMethod.Read.All       | Read user authentication methods                     |
| OnPremDirectorySynchronization.Read.All | Read Entra Connect sync configuration                |

### Optional Permissions

Some test require elevated permissions

| Permission                   | Purpose                                |
| ---------------------------- | -------------------------------------- |
| ReportSettings.ReadWrite.All | Required to disable report obfuscation |

In addition, 365TUNE required below optional permissions to complete some tests. Tests will be skipped if these permissions are not granted:

Grant Permissions to Exchange Online

Grant Permissions to Microsoft Teams

Grant Permissions to Azure

### Permission Details by Category

#### Device Management (Intune)

**DeviceManagementConfiguration.Read.All**

* Device configuration policies
* Compliance policies
* Device enrollment restrictions
* Configuration profiles

**DeviceManagementManagedDevices.Read.All**

* Device inventory
* Compliance status
* Device health
* Installed applications
* Hardware information

**DeviceManagementRBAC.Read.All**

* Intune role assignments
* Custom role definitions
* Scope tags
* Administrative permissions

**DeviceManagementServiceConfig.Read.All**

* Intune subscription state
* Service configuration
* Terms and conditions
* Certificate connectors

#### Directory and Identity

**Directory.Read.All**

* Users and their properties
* Groups and membership
* Applications and service principals
* Devices
* Organizational contacts
* Directory roles (read-only, not assignments)

**DirectoryRecommendations.Read.All**

* Microsoft Entra recommendations
* Security improvement suggestions
* Tenant health insights

**OnPremDirectorySynchronization.Read.All**

* Entra Connect sync configuration
* Synchronization status
* Sync errors and warnings
* Password hash sync status

#### Security and Risk

**IdentityRiskEvent.Read.All**

* Risk detections (impossible travel, anonymous IP, malware-linked IP)
* User risk levels
* Sign-in risk levels
* Risk event timeline

**SecurityIdentitiesSensors.Read.All**

* Microsoft Defender for Identity sensor deployment
* Sensor health status
* Sensor configuration

**SecurityIdentitiesHealth.Read.All**

* Defender for Identity health alerts
* Service status
* Coverage analysis

**ThreatHunting.Read.All**

* Advanced hunting queries
* Threat intelligence data
* Security incident correlation

#### Policy and Conditional Access

**Policy.Read.All**

* Authorization policies
* Feature rollout policies
* Claims mapping policies
* Token lifetime policies
* Activity-based timeout policies

**Policy.Read.ConditionalAccess**

* Conditional Access policies
* Named locations
* Terms of use
* Policy assignments

#### Privileged Access Management

**PrivilegedAccess.Read.AzureAD**

* PIM settings for Azure AD roles
* Eligible role assignments
* Active role assignments
* PIM alerts

**RoleEligibilitySchedule.Read.Directory**

* Time-bound role eligibility
* Activation schedules
* Role assignment schedules

**RoleManagement.Read.All**

* Azure AD role definitions
* Role assignments (eligible and active)
* Administrative units
* Custom role definitions

#### Reports and Settings

**Reports.Read.All**

* Sign-in logs
* Audit logs
* User activity reports
* Application usage reports
* Device usage statistics

**ReportSettings.Read.All**

* Report configuration
* Data retention settings
* Export settings

**UserAuthenticationMethod.Read.All**

* Registered authentication methods (MFA, FIDO2, Windows Hello)
* Authentication method policies
* Registration status
* Default authentication methods

#### Tenant Configuration

**SharePointTenantSettings.Read.All**

* SharePoint tenant settings
* OneDrive policies
* Sharing configuration
* External user settings

### What 365TUNE Cannot Do with these permissions:

Even with these permissions, 365TUNE cannot:

* Modify Conditional Access policies
* Change device compliance policies
* Assign or remove PIM roles
* Configure authentication methods
* Modify directory objects
* Change SharePoint settings
* Update Intune configurations
* Dismiss risk detections
* Modify security policies
* Access mailbox content
* Read file contents from SharePoint/OneDrive
* Modify threat hunting queries

### Data Collection Scope

#### What 365TUNE Collects

**Identity Data:**

* User accounts (properties, status, risk levels)
* Group memberships
* Authentication methods
* Sign-in activity

**Device Data:**

* Device inventory
* Compliance status
* Configuration profile assignments
* Application deployments

**Security Data:**

* Conditional Access policies (configuration only)
* PIM role assignments
* Risk detections
* Security recommendations

**Configuration Data:**

* Intune policies
* SharePoint settings
* Entra Connect status
* Directory sync configuration

#### What 365TUNE Does Not Collect

* Passwords or credentials
* Email content
* File content from SharePoint/OneDrive
* Chat messages
* Personal identifiable information beyond directory attributes
* Application data
* Customer data from workload

### Frequently Asked Questions

**Q: Can 365TUNE modify security policies?** A: No. All permissions are read-only.

**Q: Does 365TUNE access email or files?** A: No. Mail and file content permissions are not requested.

**Q: What happens if a Conditional Access policy blocks 365TUNE?** A: 365TUNE service principal must be excluded from Conditional Access policies that block service principals. Alternatively, create an exception for 365TUNE's application ID.

**Q: Can 365TUNE see passwords?** A: No. Password hashes and credentials are not accessible via these permissions.

**Q: Why does 365TUNE need PIM permissions?** A: To report on privileged role assignments and identify over-privileged accounts as part of security posture assessment.

**Q: What if our organization doesn't use Intune?** A: Device Management permissions will return empty results. They do not grant access to non-existent resources.

**Q: How often does 365TUNE collect data?** A: Collection frequency depends on subscription tier. Typical range: hourly to daily.

**Q: Can we revoke specific permissions?** A: Yes, but this may impact specific reports. 365TUNE will indicate which reports require which permissions.

***

### Reference

**Microsoft Documentation:**

* [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference)
* [Application permissions overview](https://learn.microsoft.com/en-us/graph/auth-v2-service)
* [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/)
* [Intune Graph API](https://learn.microsoft.com/en-us/graph/api/resources/intune-graph-overview)
* [Conditional Access](https://learn.microsoft.com/en-us/entra/identity/conditional-access/)
* [Privileged Identity Management](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/)
