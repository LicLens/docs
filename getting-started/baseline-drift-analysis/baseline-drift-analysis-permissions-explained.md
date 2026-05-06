---
description: >-
  This article explains the specific permissions required for the Baseline Drift
  Analysis module, why they are needed, and how 365TUNE uses them responsibly.
---

# Baseline Drift Analysis: Permissions Explained

The **Baseline Drift Analysis** module in 365TUNE continuously monitors your tenants' security configurations and compares them against established baselines — such as security controls. When settings deviate from the approved baseline, 365TUNE flags the drift so administrators can investigate and remediate before it becomes a compliance or security risk.

{% hint style="info" %}
**Read-Only by Design:** All permissions requested by the Baseline Drift Analysis module are strictly read-only. 365TUNE does not modify, create, or delete any configuration in your tenant as part of drift analysis. This module is built on the principle of least privilege — only the data needed to evaluate your security posture is accessed.&#x20;
{% endhint %}

#### Required Permissions

All permissions are **application type** with tenant-wide scope.

| Permission                    | Purpose                                                   |
| ----------------------------- | --------------------------------------------------------- |
| AdministrativeUnit.Read.All   | Read all administrative units                             |
| Application.Read.All          | Read all applications and service principal registrations |
| Group.Read.All                | Read all groups and group membership                      |
| IdentityProvider.Read.All     | Read identity providers configured in the tenant          |
| Organization.Read.All         | Read organization-level information and tenant properties |
| Policy.Read.All               | Read all organization policies                            |
| Policy.Read.ConditionalAccess | Read your organization's conditional access policies      |
| RoleManagement.Read.Directory | Read all directory RBAC settings and role assignments     |

***

#### What These Permissions Allow

**`AdministrativeUnit.Read.All`**

This permission allows 365TUNE to read Administrative Unit configurations, which define the scope boundaries for delegated administration in larger organizations.

**What 365TUNE uses this for:**

* Reading all Administrative Units and their memberships
* Detecting drift in scope-restricted administrator assignments
* Identifying unauthorized additions or removals of members and scoped roles within Administrative Units
* Verifying that AU-scoped role assignments align with the approved baseline

***

**`Application.Read.All`**

This permission allows 365TUNE to read all application registrations and enterprise app (service principal) configurations in the tenant.

**What 365TUNE uses this for:**

* Inventorying registered applications and their permission grants
* Detecting newly registered or removed applications that may represent unauthorized changes
* Identifying apps with high-privilege API permissions that deviate from the approved baseline
* Flagging changes to application credential expiry dates, redirect URIs, or owner assignments

***

**`Group.Read.All`**

This permission allows 365TUNE to read all security groups and Microsoft 365 groups, including their memberships and settings.

**What 365TUNE uses this for:**

* Reading security group and Microsoft 365 group membership
* Detecting unauthorized changes to groups used in Conditional Access policy assignments
* Identifying group membership drift that may affect privileged access or policy scope
* Verifying that dynamic group membership rules have not been modified

***

**`IdentityProvider.Read.All`**

This permission allows 365TUNE to read the external identity providers configured in the tenant, such as SAML-based federation or social identity providers.

**What 365TUNE uses this for:**

* Reading all configured identity providers (federated IdPs, B2B/B2C providers)
* Detecting unauthorized additions or removals of identity providers
* Flagging federation configuration drift that could affect authentication trust boundaries
* Verifying that only approved external identity providers are active in the tenant

***

**`Organization.Read.All`**

This permission allows 365TUNE to read organization-level properties and tenant configuration data.

**What 365TUNE uses this for:**

* Reading tenant display name, verified domains, and technical contact information
* Reading organization-level settings such as the default user role permissions
* Detecting changes to tenant-wide properties that are part of the security baseline
* Cross-referencing organization data with user and policy configurations during drift evaluation

***

**`Policy.Read.All`**

This permission allows 365TUNE to read all policy resources in the tenant, providing broad coverage of policy-based security configurations.

**What 365TUNE uses this for:**

* Reading token issuance and token lifetime policies
* Reading authentication flow and home realm discovery policies
* Reading authorization policies that govern default user permissions
* Detecting drift in any policy category that is part of the tenant's approved security baseline

***

**`Policy.Read.ConditionalAccess`**

This permission allows 365TUNE to read your organization's Conditional Access policies and compare them against your approved security baseline.

**What 365TUNE uses this for:**

* Reading all existing Conditional Access policies and their full configuration
* Comparing policy configurations (target users, conditions, grant controls, session controls) against baseline definitions
* Flagging policies that have been added, modified, or removed since the last baseline snapshot
* Detecting Conditional Access gaps — for example, missing MFA requirements for privileged roles

***

**`RoleManagement.Read.Directory`**

This permission allows 365TUNE to read directory role definitions and all active role assignments across the tenant.

**What 365TUNE uses this for:**

* Reading all built-in and custom directory role definitions
* Inventorying all active role assignments, including Privileged Identity Management (PIM) eligible assignments
* Detecting unauthorized additions to high-privilege roles such as Global Administrator, Exchange Administrator, or Security Administrator
* Flagging role assignment drift — new assignments, removed assignments, or scope changes that were not part of the approved baseline

***

#### Frequently Asked Questions

**Q: Does Baseline Drift Analysis change anything in my tenant?**\
A: No. Every permission in this module is read-only. 365TUNE reads your configurations, compares them against your approved baseline, and surfaces findings in the dashboard. No data is created, modified, or deleted in your tenant during drift analysis.

**Q: Why does 365TUNE need both `Policy.Read.All` and `Policy.Read.ConditionalAccess`?**\
A: These scopes cover different policy resource types in Microsoft Graph. `Policy.Read.ConditionalAccess` is specifically required to access the `conditionalAccessPolicies` endpoint with full detail. `Policy.Read.All` covers a broader set of policy types — such as token lifetime, authorization, and authentication flow policies — that are not exposed under the Conditional Access scope. Both are needed for complete baseline coverage.

**Q: Can 365TUNE modify roles or role assignments?**\
A: No. The `RoleManagement.Read.Directory` permission is read-only. 365TUNE can read role assignments to detect drift, but it cannot assign, remove, or modify any directory role.

**Q: Can 365TUNE access email content, user files, or SharePoint data?**\
A: No. Mail, calendar, file, and SharePoint permissions are not requested by this module. 365TUNE only accesses the security and identity configuration data necessary to evaluate your baseline.

**Q: What baselines does 365TUNE compare against?**\
A: 365TUNE supports the CIS Microsoft 365 Foundations Benchmark (currently v5.0.0) as a primary baseline framework. Custom baseline snapshots captured from approved tenant states are also supported, allowing drift to be measured against your own organization's security standard rather than a generic benchmark alone.

**Q: How often does 365TUNE check for drift?**\
A: Drift checks run on a scheduled basis per tenant. The frequency is configurable within the 365TUNE platform settings. Alerts can be configured to notify administrators immediately when a drift event is detected.

**Q: What happens if a tenant revokes consent for these permissions?**\
A: If application consent is revoked, 365TUNE will be unable to complete the drift analysis for that tenant. The platform will surface a consent error in the tenant health view, and the MSP administrator will need to re-authorize the application to resume monitoring.

**Q: How do application permissions differ from delegated permissions?**\
A: Application permissions operate with the service principal identity and do not require a signed-in user session. This allows 365TUNE to perform scheduled background drift checks continuously, without depending on an administrator being actively logged in.
