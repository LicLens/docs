---
description: >-
  This article provides a detailed breakdown of the specific Microsoft Entra ID
  permissions that 365TUNE requires to perform management actions within you
  tenant.
---

# Management and Automation: Permissions Explained

### Overview

The **Management and Automation** module in 365tune enables to take action on user accounts across their managed tenants. Unlike the read-only Reporting and Auditing module, this module allows you to modify user properties, reset passwords, and assign licenses directly from 365TUNE's interface.

This article explains the specific permissions required for the Management and Automation module, why they're needed, and how 365TUNE implements them securely.

{% hint style="info" %}
**Current Limitation**: Synchronized users (hybrid identity) cannot be modified due to on-premises Active Directory source of authority constraints. Hybrid AD support is in the roadmap and will be available in the platform by mid 2026.
{% endhint %}

### Required Permissions

All permissions are **application type** with tenant-wide scope.

| Permission                         | Purpose                                        |
| ---------------------------------- | ---------------------------------------------- |
| User.ReadWrite.All                 | Modify user properties                         |
| User.EnableDisableAccount.All      | Enable/disable accounts                        |
| User-Phone.ReadWrite.All           | Update phone numbers                           |
| User-Mail.ReadWrite.All            | Modify otherMails property. Can't read emails. |
| User-PasswordProfile.ReadWrite.All | Reset passwords                                |
| User.DeleteRestore.All             | Delete/restore users                           |
| User.Read.All                      | Read user properties                           |
| LicenseAssignment.ReadWrite.All    | Manage license assignments                     |
| GroupMember.ReadWrite.All          | Manage group membership                        |
| Group.ReadWrite.All                | Modify group properties                        |

***

### What These Permissions Allow

#### `User.EnableDisableAccount.All`

This permission allows 365tune to toggle the `accountEnabled` property on user accounts.

**What you can do:**

* Enable a user account (set `accountEnabled` to `true`)
* Disable a user account (set `accountEnabled` to `false`)

***

#### `User-Phone.ReadWrite.All`

This permission allows 365tune to modify phone number properties on user accounts.

**What you can do:**

* Update the `businessPhones` property
* Update the `mobilePhone` property
* Read identifier-related properties (id, userPrincipalName, etc.)

***

#### `User.ReadWrite.All`

This permission allows 365tune to modify standard user properties.

**What you can do:**

**Identity fields:**

* displayName, givenName, surname, userPrincipalName

**Organization fields:**

* jobTitle, department, companyName, employeeId, employeeType, officeLocation, manager

**Contact fields:**

* streetAddress, city, state, postalCode, country, mailNickname

**Account fields:**

* usageLocation

***

#### `User-PasswordProfile.ReadWrite.All`

This permission allows 365tune to reset passwords for user accounts.

**What you can do:**

* Update the `passwordProfile` property
* Set new passwords (either custom or system-generated)
* Force password change on next sign-in
* Read identifier-related properties

***

#### `LicenseAssignment.ReadWrite.All`

This permission allows 365tune to assign and remove licenses for users and groups.

**What you can do:**

* Assign licenses to users
* Remove licenses from users
* Assign licenses to groups (for group-based licensing)
* Remove licenses from groups
* Enable or disable specific service plans within licenses

***

#### `User.Read.All`

This permission allows 365tune to read user account information.

**What you can do:**

* View all user properties
* View account status (accountEnabled property)
* Verify changes after updates
* Display user information in the 365tune interface

### Frequently Asked Questions

**Q: Can 365TUNE access email or files?** A: No. Mail and file permissions are not requested.

**Q: Can 365TUNE assign Global Administrator?** A: No. RoleManagement.ReadWrite.Directory is not requested.

**Q: Why so many permissions?** A: Microsoft's granular permission model requires separate permissions for specific operations. This provides better audit trails and least-privilege access.

**Q: What happens to synchronized user management?** A: Properties controlled by on-premises AD cannot be modified. License assignment and usage location management remain functional.

**Q: How do application permissions differ from delegated?** A: Application permissions operate with service principal identity without requiring logged-in users. Delegated permissions inherit user access levels and require user sessions.

**Q: What if password writeback isn't enabled?** A: Password resets work for cloud-only users. For synchronized users, password changes affect cloud services only without writeback configuration.

If you’re setting up 365TUNE for the first time or reviewing your security posture, ensure that the required permissions are granted and aligned with your organization’s governance policies.
