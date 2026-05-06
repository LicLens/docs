---
description: >-
  This article explains the specific permissions required for the Baseline
  Restore module, why they are needed, and how 365TUNE implements them securely.
---

# Baseline Drift Restore: Permissions Explained

The **Baseline Drift Restore** module in 365TUNE enables administrators to remediate security configuration drift by restoring tenant settings to their approved baseline state. Where the Baseline Drift Analysis module identifies what has changed, Baseline Restore takes action - reverting unauthorized or unintended changes to Conditional Access policies, authentication methods, security defaults, group configurations, and directory settings.

{% hint style="info" %}
**Write Permissions Required:** Unlike the read-only Baseline Drift Analysis module, Baseline Restore requires write-capable permissions to apply changes to your tenant. All restore actions are administrator-initiated - 365TUNE never modifies tenant configurations automatically or without explicit approval from a user with the appropriate role in the platform.
{% endhint %}

{% hint style="info" %}
**Restore vs. Remediation:** Baseline Restore does not make freeform changes. It restores configurations to a previously approved and captured baseline snapshot. Every restore action is logged with a before/after record in the 365TUNE audit trail for compliance and review purposes.
{% endhint %}

#### Required Permissions

| Permission                            | Type        | Purpose                                                                     |
| ------------------------------------- | ----------- | --------------------------------------------------------------------------- |
| AdministrativeUnit.ReadWrite.All      | Application | Read and restore administrative unit configurations                         |
| Directory.ReadWrite.All               | Application | Read and write directory data to support cross-object restore               |
| Group.ReadWrite.All                   | Application | Read and restore group memberships and configurations                       |
| Policy.ReadWrite.AuthenticationMethod | Application | Read and restore authentication method policies                             |
| Policy.ReadWrite.ConditionalAccess    | Application | Read and restore Conditional Access policies                                |
| Policy.ReadWrite.SecurityDefaults     | Application | Read and restore the tenant's security defaults policy                      |
| User.Read                             | Delegated   | Sign in and verify the identity of the administrator initiating the restore |

***

#### What These Permissions Allow

**`AdministrativeUnit.ReadWrite.All`**

This permission allows 365TUNE to read Administrative Unit configurations and restore them to their approved baseline state when drift is detected.

**What 365TUNE uses this for:**

* Reading all Administrative Units, their memberships, and scoped role assignments
* Restoring Administrative Unit membership to the approved baseline when unauthorized additions or removals are detected
* Reverting scoped role assignments within Administrative Units to their baseline configuration
* Verifying the restored state matches the approved baseline after the restore action completes

***

**`Directory.ReadWrite.All`**

This permission allows 365TUNE to read and write broad directory data, supporting restore operations that span multiple object types within the tenant.

**What 365TUNE uses this for:**

* Reading directory objects (users, service principals, application registrations) to validate pre-restore state
* Writing directory-level properties that are part of the approved baseline but not covered by more specific scopes
* Supporting cross-object restore operations where configurations span multiple directory resource types
* Verifying object-level consistency after a restore action is applied

***

**`Group.ReadWrite.All`**

This permission allows 365TUNE to read and modify group configurations and memberships, restoring them to the approved baseline when unauthorized changes are detected.

**What 365TUNE uses this for:**

* Reading security group and Microsoft 365 group configurations and membership lists
* Restoring group membership to the approved baseline (re-adding removed members or removing unauthorized additions)
* Reverting changes to group settings, such as dynamic membership rules or visibility settings
* Restoring groups that are referenced by Conditional Access policies to ensure policy assignments remain intact after a restore

***

**`Policy.ReadWrite.AuthenticationMethod`**

This permission allows 365TUNE to read and restore the tenant's Authentication Methods policy when changes to enabled or disabled authentication methods are detected as drift.

**What 365TUNE uses this for:**

* Reading the current state of the Authentication Methods policy (FIDO2, Microsoft Authenticator, SMS, Temporary Access Pass, and others)
* Restoring the enabled/disabled state of individual authentication methods to match the approved baseline
* Reverting configuration changes within a method, such as target group scope or external app policy settings
* Ensuring MFA and passwordless authentication method availability aligns with the tenant's security baseline after restore

***

**`Policy.ReadWrite.ConditionalAccess`**

This permission allows 365TUNE to read and restore Conditional Access policies — the most critical control surface for identity-based security in Microsoft 365.

**What 365TUNE uses this for:**

* Reading the full configuration of all Conditional Access policies (conditions, users, grant controls, session controls)
* Restoring modified policies to their approved baseline configuration
* Re-enabling policies that were disabled without authorization
* Removing unauthorized policies that were created outside the approved baseline
* Recreating policies that were deleted, using the captured baseline snapshot as the source of truth

{% hint style="info" %}
**Important:** Changes to Conditional Access policies can affect authentication for all users in the tenant. All Conditional Access restore actions in 365TUNE require explicit administrator confirmation before execution and are logged in full in the platform audit trail.&#x20;
{% endhint %}

***

**`Policy.ReadWrite.SecurityDefaults`**

This permission allows 365TUNE to read and restore the Security Defaults setting for the tenant.

**What 365TUNE uses this for:**

* Reading whether Security Defaults are currently enabled or disabled
* Restoring Security Defaults to the approved baseline state when an unauthorized change is detected
* Alerting when Security Defaults are disabled in tenants where no compensating Conditional Access policies are in place
* Re-enabling Security Defaults as part of a restore when the baseline specifies them as the tenant's baseline protection posture

***

**`User.Read`** _**(Delegated)**_

This is the only **delegated** permission in the Baseline Restore module. Unlike the application permissions above, this permission operates in the context of the signed-in administrator who initiates the restore action.

**What 365TUNE uses this for:**

* Verifying the identity of the administrator initiating the restore
* Associating the restore action with a named user account for audit trail purposes
* Ensuring that restore operations are attributed to a real, authenticated administrator rather than an anonymous service call

**Why Delegated?** Delegated permissions require an active user session. For Baseline Restore, this is intentional — it ties every write action to an authenticated administrator identity, creating a clear and accountable audit record of who approved and triggered each restore operation.&#x20;

***

#### Frequently Asked Questions

**Q: Can 365TUNE trigger a restore automatically without administrator approval?**\
A: No. Baseline Restore is always administrator-initiated. 365TUNE identifies drift through the Baseline Drift Analysis module and surfaces findings in the dashboard, but no restore action is executed until an administrator with the appropriate platform role explicitly approves and triggers it.

**Q: What happens to the existing configuration before a restore is applied?**\
A: 365TUNE captures a point-in-time snapshot of the current (drifted) state before applying any restore. This snapshot is retained in the audit trail so administrators can review what was changed, compare it to the baseline, and roll back if needed.

**Q: Why does `User.Read` use Delegated type while all other permissions are Application type?**\
A: Application permissions allow 365TUNE to operate as a background service without a signed-in user. `User.Read` is intentionally delegated so that every restore action is tied to a specific, authenticated administrator identity — creating a named audit record rather than an anonymous service-account action. This supports accountability and compliance requirements.

**Q: Can 365TUNE delete users, reset passwords, or access email as part of a restore?**\
A: No. Baseline Restore is scoped to security policy and configuration objects. Permissions for user password resets (`User-PasswordProfile.ReadWrite.All`), mailbox access (`Mail.Read`), and file access (`Files.Read.All`) are not requested by this module.

**Q: Does `Directory.ReadWrite.All` give 365TUNE access to everything in the directory?**\
A: At the Microsoft Graph API level, `Directory.ReadWrite.All` is a broad scope. However, 365TUNE only uses this permission in the context of active restore operations and does not perform background reads or writes outside of an administrator-triggered restore action. All operations performed under this scope are logged in the 365TUNE audit trail.

**Q: What is the difference between Baseline Drift Analysis and Baseline Restore?**\
A: Baseline Drift Analysis is a read-only monitoring module — it detects and reports configuration changes. Baseline Restore is the action layer — it enables administrators to remediate detected drift by reverting configurations to their approved baseline state. The two modules are designed to work together within the 365TUNE platform.

**Q: Is there an approval workflow before a restore is applied?**\
A: Yes. 365TUNE presents a pre-restore summary showing the current (drifted) configuration, the target (baseline) configuration, and the specific changes that will be applied. An administrator must review and confirm before the restore proceeds.

**Q: Are restore actions logged for compliance purposes?**\
A: Yes. Every restore action — including the initiating administrator, the timestamp, the before state, the after state, and the specific changes applied — is recorded in the 365TUNE audit trail. This log is available for review and export to support internal governance and external audit requirements.
