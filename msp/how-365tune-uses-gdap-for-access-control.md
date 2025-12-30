---
description: >-
  365TUNE integrates with Granular Delegated Admin Privileges (GDAP) to provide
  secure, role-based, and time-bound access to customer tenants.
---

# How 365TUNE Uses GDAP for Access Control

### Overview

365tune integrates with **Granular Delegated Admin Privileges (GDAP)** to provide secure, role-based, and time-bound access to customer tenants.

Customer data collected by 365tune is protected by Microsoft’s partner access framework. MSP users can access customer data **only when they have active GDAP permissions** for the corresponding tenant.

This design aligns with Microsoft security best practices, including **least privilege**, **Zero Trust**, and **customer-controlled access**.

### What Is GDAP?

**Granular Delegated Admin Privileges (GDAP)** is Microsoft’s modern partner access model that replaces legacy Delegated Admin Privileges (DAP).

GDAP enables MSPs to:

* Assign **specific Microsoft Entra roles** instead of broad administrative access
* Configure **time-limited access** with automatic expiration
* Reduce security exposure by limiting over-privileged accounts
* Improve compliance and auditability

GDAP relationships are created and managed in **Microsoft Partner Center** and enforced across customer tenants by **Microsoft**.

### How 365TUNE Integrates with GDAP

365TUNE uses GDAP as the **authoritative access control mechanism** for MSP users.

#### Access Flow

1. **Customer Consent**
   * The customer grants application permissions to the 365TUNE platform
   * This enables secure, background data collection using **Microsoft Graph**
2. **GDAP Relationship**
   * The MSP establishes a GDAP relationship with the customer tenant
   * Roles are scoped per tenant and configured with an expiration period
3. **MSP User Authentication**
   * MSP users sign in to 365TUNE using their individual identities
   * 365TUNE evaluates their GDAP assignments at sign-in
4. **Authorization Enforcement**
   * MSP users can access customer data **only if** they have active GDAP permissions
   * Access is limited to the roles assigned in Partner Center
5. **Continuous Validation**
   * If GDAP permissions expire or are revoked, access is automatically removed
   * No persistent or cached access is retained

{% hint style="info" %}
Important: 365TUNE's read-only Application permissions enable background data collection from a Customer Tenant. GDAP controls MSP user access to this data based on their access level.
{% endhint %}

Granting application permissions to 365TUNE does not grant MSP users unrestricted access to customer data. All MSP user access is evaluated and enforced based on GDAP relationships and assigned roles.

### Role-Based Access Alignment

365TUNE aligns user capabilities with Microsoft Entra roles granted through GDAP.

<table><thead><tr><th width="261">GDAP Role (Example)</th><th>Access in 365TUNE</th></tr></thead><tbody><tr><td>Global Reader</td><td>Tenant-wide read-only insights</td></tr><tr><td>Reports Reader</td><td>Usage and adoption reporting</td></tr><tr><td>Security Reader</td><td>Security and compliance insights</td></tr></tbody></table>

### Access Changes and Expiration

365TUNE automatically responds to GDAP lifecycle events:

* **GDAP expires** → MSP user access is removed
* **GDAP revoked** → Tenant access is blocked immediately
* **Role removed** → Feature access is adjusted automatically

No manual intervention is required.

### Benefits for MSPs

Using GDAP with 365TUNE enables MSPs to:

* Reduce operational and security risk
* Maintain strong tenant isolation
* Support customers with clear access boundaries
* Improve audit readiness and customer trust
* Advances dashboard and insights from 365TUNE

### Summary

365tune is designed to work natively with Microsoft GDAP.

* Customers grant application permissions for secure data collection
* MSP user access is governed exclusively by GDAP
* Access is role-based, time-bound, and continuously enforced
* MSP users cannot access customer data without Microsoft-approved delegated access

[Unable to see a Customer Tenant in 365TUNE?](gdap-troubleshooting-why-cant-i-see-a-customer-tenant.md)
