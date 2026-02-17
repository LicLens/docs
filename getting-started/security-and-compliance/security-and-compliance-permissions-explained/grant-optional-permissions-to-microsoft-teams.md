---
description: >-
  By default, 365TUNE connects to Microsoft Graph to assess identity, directory,
  and core Microsoft 365 security configurations. However, Some Teams data
  exists outside of Microsoft Graph.
---

# Grant Optional Permissions to Microsoft Teams

365TUNE application requires **Teams Reader role** in tenant to perform teams related security tests. Microsoft Teams uses **Role-Based Access Control (RBAC)** to authorize access to Teams-specific configuration and policy settings. Unlike Microsoft Graph API permissions which allow authentication and service-level access, Teams requires a **service-specific Entra ID role assignment** to complete the authorization chain.

{% hint style="info" %}
Assign Microsoft Teams RBAC Role to 365TUNE only if you want 365TUNE to assess Team related security configurations in your tenant. Without this role Teams-related assessment checks may fail or be skipped.

**These steps are optional. If you do not need these checks, you can skip this section.**
{% endhint %}

Follow these steps to assigns the **Teams Reader** role to the '365TUNE Security and Compliance' application.

Log in to  [https://entra.microsoft.com/](https://entra.microsoft.com/) as a Global Administrator or Privileged Role Administrator&#x20;

* Navigate to Roles and administrators
* Search and select **Teams Reader**
* Select **Add assignment**
* Select **No member selected**
* Search for '365TUNE Security and Compliance' and select **Select** to confirm
* Select **Next** to confirm
* Ensure that **Active** and **Permanently assigned** are ticked
* Enter **Justification**
* Select **Assign** to confirm.
