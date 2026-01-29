---
description: >-
  If you have received a request for admin consent to register 365TUNE in your
  Microsoft 365 tenant, this article explains what's being requested and what
  you need to know before approving.
---

# Understanding the Admin Consent Request

### Why you received this request

Someone in your organization or one of your Managed Service Providers initiated the process to add your tenant to 365TUNE. Because this requires access to your Microsoft 365 data, a privileged administrator must grant explicit consent.

### What is 365TUNE?

365TUNE is a secure reporting tool designed to help organizations and their partners gain insights into license usage, generate financial reports, and ensure security compliance.&#x20;

To provide these capabilities, 365TUNE needs read-only access to specific Microsoft 365 data through Microsoft Graph APIs.

### Why Admin Consent is Required

365TUNE uses **application permissions** to access Microsoft 365 data for reporting and monitoring. This means:

**Continuous monitoring capability:** The application can collect data 24/7 without requiring a user to be logged in, ensuring reports and dashboards stay current.

**Background data processing:** 365TUNE operates independently in the background, analyzing usage patterns and generating insights without manual intervention.

**Secure API access:** All data access happens through Microsoft's secure APIs using application-level authentication, not user credentials.

{% hint style="info" %}
Only Global Administrators and Privileged Role Administrators can grant this consent. Regular users cannot approve these requests.
{% endhint %}

### Step-by-Step Process for Granting Permissions

365TUNE relies on secure, Microsoft-managed authentication to establish a connection with your Microsoft 365 environment. During the onboarding, the app seamlessly connects to the Microsoft 365 environment using the Enterprise Application registration process in Entra ID.

Here’s a breakdown of the process involved in Application registration:

1. **Global Admin Logs In**: When prompted during the onboarding process, The Global Administrator logs into the Microsoft 365 Admin Portal.
2. **Review Permissions**: The Global Admin reviews the permissions 365TUNE will request.
3. **Grant Consent**: The Global Admin grants consent for 365TUNE to access the necessary data with the approved permissions.
4. **App Registration**: 365TUNE completes the registration in Microsoft’s identity platform, creating a secure connection for ongoing data access.

This process ensures that only authorized applications have access to your Microsoft 365 environment, and it is designed to be transparent and secure.

### What Permissions Are Being Requested

When you click the consent link in the email, you'll see the specific Microsoft Graph API permissions that 365TUNE is requesting. 365TUNE follows the **principle of least privilege** - requesting only the minimum permissions necessary to function.

#### For Standard Reporting Access

365TUNE requests read-only permissions for monitoring and reporting like:

* **User.Read.All** - Read user profiles and license assignments
* **Reports.Read.All** - Access usage reports and metrics
* **Directory.Read.All** - Read directory data (groups, roles)
* **AuditLog.Read.All** - Read audit logs for compliance

{% hint style="info" %}
For a complete list of permissions and explanation of each permission and how 365TUNE uses it, refer to the [Permissions Explained article](permissions-explained.md).
{% endhint %}

#### For Management Feature Access

> **Feature Status:** Management features are currently in **Private Preview**. General availability is planned for **Q2 2026**.

If your organization needs **management capabilities** (license assignment, user modifications, etc.), a **separate consent request** will be sent with elevated write permissions.

### After Granting Consent

* **The admin who granted the consent become the default administrator** for 365TUNE
* This Admin must invite other users (including the person who requested consent) and assign roles.
* Data collection begins immediately

### **Revoke access**&#x20;

You can remove 365TUNE's access at any time:

1. Navigate to **Enterprise Applications** in Azure AD
2. Find "365TUNE"
3. Click **Delete** or **Remove**
4. Access is revoked immediately

### Common Questions

**What happens if I don't grant consent?**

If you deny the consent request or ignore the email, 365TUNE will not be able to access your tenant. The person who initiated onboarding won't be able to use 365TUNE for your organization.

**Can I grant partial permissions?**

No. You cannot selectively approve individual permissions. 365TUNE follows the principle of least privilege - requesting only the minimum permissions necessary to function. 365TUNE manages permission consent for reporting/monitoring and management feature separately. This means least required permissions are requested separately based on the organizations need.

**How long does my consent remain valid?**

Once granted, consent remains valid indefinitely unless you explicitly revoke it. The permissions don't expire automatically.

**Will this affect our existing Microsoft 365 services?**

No. Granting 365TUNE access does not affect any of your existing Microsoft 365 services or other applications. It simply allows 365TUNE to read (and potentially modify, if management permissions are granted) data through Microsoft's APIs.

**Can other users in my organization grant this consent?**

No. Only Global Administrators and Privileged Role Administrators can grant organization-wide application consent. Regular users cannot approve these requests.

**How do I know which admin should grant consent?**

Any Global Administrator or Privileged Role Administrator in your organization can grant consent. However, whoever grants consent becomes the default 365TUNE administrator and will be responsible for inviting other users in 365TUNE platform.&#x20;

**Do admin users in 365TUNE need special Microsoft 365 permissions in Tenant?**

For read-only features with application permissions: No. Once you invite users to 365TUNE, they can access the platform with their Microsoft 365 credentials without need to give them permissions in the Microsoft tenant.

For management features with delegated permissions: Yes. If 'delegated permissions' model is selected for Management features, Users can only perform actions that their Azure AD role allows. Alternatively, the admin could choose 'application permissions' model that does not require the user permissions in the tenant.

### Summary

This consent mechanism aligns with Microsoft's zero-trust security principles and ensures you maintain complete visibility and control over applications accessing your organization's data. The separation of read-only and management permissions provides granular control over what 365TUNE can do in your environment.
