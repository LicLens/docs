# Management and Automation: Permissions Explained

### Overview

The **Management and Automation** module in 365tune enables to take action on user accounts across their managed tenants. Unlike the read-only Reporting and Auditing module, this module allows you to modify user properties, reset passwords, and assign licenses directly from 365TUNE's interface.

This article explains the specific permissions required for the Management and Automation module, why they're needed, and how 365TUNE implements them securely.

### Required Permissions

The Management and Automation module requires six delegated permissions:

| Permission                           | Type      | Purpose                                                          |
| ------------------------------------ | --------- | ---------------------------------------------------------------- |
| `User.EnableDisableAccount.All`      | Delegated | Enable or disable user accounts                                  |
| `User-Phone.ReadWrite.All`           | Delegated | Modify phone numbers (businessPhones, mobilePhone)               |
| `User.ReadWrite.All`                 | Delegated | Modify user properties (displayName, jobTitle, department, etc.) |
| `User-PasswordProfile.ReadWrite.All` | Delegated | Reset user passwords                                             |
| `LicenseAssignment.ReadWrite.All`    | Delegated | Assign and remove licenses                                       |
| `User.Read.All`                      | Delegated | Read user account details                                        |

#### Why Delegated Permissions?

365TUNE uses **delegated permissions** for all management operations, which means:

**Every action is performed in the context of a logged-in admin**\
Your technician's identity is used when making changes, creating a complete audit trail in Microsoft's logs.

**Better security posture**\
Unlike application permissions that work 24/7 in the background, delegated permissions only work when someone is actively logged in.

**Full accountability**\
Entra ID audit logs show exactly which person made each change, not just "365tune application made a change."

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
