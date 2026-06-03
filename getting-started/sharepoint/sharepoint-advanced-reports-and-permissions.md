---
description: >-
  To enable SharePoint management, reporting, and automation features, 365TUNE
  requires access to specific Microsoft Graph and SharePoint permissions.
---

# SharePoint Advanced Reports & Permissions

These permissions allow the platform to collect tenant-wide SharePoint configuration data, analyze security and governance settings, and perform administrative actions on SharePoint sites when automation features are used.

### Why These Permissions Are Required

365TUNE helps administrators gain visibility into SharePoint Online environments, automate administrative tasks, and ensure governance policies are consistently applied across all sites.

The required permissions allow 365TUNE to:

* Discover and inventory SharePoint sites across the tenant.
* Retrieve SharePoint tenant-level configuration settings.
* Analyze sharing, access, and governance configurations.
* Generate operational and compliance reports.
* Automate SharePoint administration tasks.
* Manage SharePoint sites, content, and permissions where authorized.

### Required Permissions

#### SharePointTenantSettings.Read.All

**Purpose:** Read SharePoint Online tenant settings.

This permission allows 365TUNE to retrieve tenant-wide SharePoint configuration information, including settings related to sharing, governance, storage, and site management.

**Used for:**

* SharePoint tenant reporting
* Governance assessments
* Configuration audits
* Security and compliance analysis

**Access Level:** Read-only

365TUNE cannot modify SharePoint tenant settings using this permission.

***

#### Sites.FullControl.All

**Purpose:** Manage SharePoint sites and content.

This permission grants 365TUNE administrative access to SharePoint sites across the tenant. It enables automation and management capabilities that require creating, updating, or managing SharePoint resources.

**Used for:**

* Site administration
* Permission management
* Content management
* Automation workflows
* Site provisioning and configuration
* Governance remediation actions

**Access Level:** Full Control

Because this permission provides broad administrative access, it should only be granted to trusted applications.

### Security & Privacy

365TUNE follows the principle of least privilege whenever possible and only requests permissions required to deliver SharePoint reporting and automation functionality.

The platform:

* Uses secure Microsoft OAuth authorization flows.
* Encrypts data in transit and at rest.
* Does not store user passwords.
* Maintains audit trails for administrative activities.
* Accesses SharePoint resources only after administrator consent is granted.

### Summary

#### SharePoint Management & Automation

Access SharePoint tenant settings and manage SharePoint sites across the organization.

**Permissions:**

* SharePointTenantSettings.Read.All – Read SharePoint tenant configuration settings.
* Sites.FullControl.All – Full control of SharePoint sites, content, and permissions.
* User.Read – Read basic profile information of the signed-in user.
