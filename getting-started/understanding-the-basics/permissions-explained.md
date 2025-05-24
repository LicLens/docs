---
description: >-
  This article explains what permissions are required for 365TUNE to operate and
  how data is accessed from Microsoft platforms.
---

# Permissions Explained

365TUNE collects data from Microsoft 365 exclusively through the **Microsoft Graph API**, which provides secure and streamlined access to a wide range of Microsoft 365 services.&#x20;

## 1. **Application Registration and Permissions**

* During the initial setup, a **Global Administrator** grants **read-only permissions** to 365TUNE, including User.Read.All, Reports.Read.All and others. These permissions allow the tool to retrieve user profile data and usage reports without the ability to modify or delete any data.
* 365TUNE is registered as an application within Microsoft Entra ID (formerly Azure Active Directory), enabling it to securely access Microsoft 365 data.
* 365TUNE does not store Global Admin credentials. It uses secure authentication through **OAuth 2.0** to access the necessary data.

Below are the detailed breakdown of permissions requested during the onboarding/app registration process.

**Microsoft Graph Permissions:**

<table><thead><tr><th width="197">Permission Names</th><th width="160.33333333333331">Permission Type</th><th>Description</th></tr></thead><tbody><tr><td>AuditLog.Read.All</td><td>Application</td><td>Read audit log data from Microsoft 365</td></tr><tr><td>Directory.Read.All</td><td>Application</td><td>Read directory data Entra ID. Example: Get assigned licenses details of a user</td></tr><tr><td>Mail.ReadBasic</td><td>Application</td><td>Read basic mail in all mailboxes. This does not grand access to email contents.</td></tr><tr><td>Reports.Read.All</td><td>Application</td><td>Read usage reports from Microsoft 365</td></tr><tr><td>User.Read.All</td><td>Application</td><td>Read users' profiles to fetch details. Example: Cost Center</td></tr><tr><td>UserAuthenticationMethod.Read.All</td><td>Application</td><td>Read users' authentication methods. </td></tr></tbody></table>

## 2. **Using Microsoft Graph API**

* After the initial setup and permission approval, 365TUNE interacts solely with the **Microsoft Graph API**, which is the gateway to Microsoft 365 data. The Graph API enables access to a variety of data, including:
  * **User data**: Information on users, their assigned licenses, and roles.
  * **Usage data**: Activity and usage reports from services like Exchange, Teams, and OneDrive.
* 365TUNE makes **API calls** to Microsoft Graph endpoints to collect this data in real-time.

## 3. **Secure Data Access**

* 365TUNE uses **OAuth 2.0 tokens** to authenticate API requests. These tokens are obtained once the Global Administrato**r** grants consent and will be used for subsequent requests to Microsoft Graph.
* This method ensures that 365TUNE accesses the data securely and does not require storing any sensitive credentials. It operates with the granted **read-only permissions**, ensuring that it can only **view and analyze** data without the ability to make changes.
* 365TUNE sends requests to Microsoft Graph API to retrieve specific datasets such as:
  * **User profiles**: Data about users, their licenses, and assigned roles.
  * **Reports**: License usage, activity metrics, and other compliance reports.
* The data collected is then analyzed and compiled into reports, which help administrators monitor license consumption and user activity across the organization.

## Conclusion

365TUNE relies entirely on **Microsoft Graph API** for collecting and analyzing data from Microsoft 365. By using secure OAuth 2.0 authentication and read-only permissions, 365TUNE ensures that it can gather important insights without compromising data integrity or requiring continuous admin access. The tool’s ability to operate solely via the Microsoft Graph API makes it both secure and efficient for reporting and compliance monitoring.

{% hint style="info" %}
Want to learn more about Entra ID App Registration & Permissions? Head to [this article ](https://learn.microsoft.com/en-us/entra/identity-platform/permissions-consent-overview)from Microsoft.
{% endhint %}
