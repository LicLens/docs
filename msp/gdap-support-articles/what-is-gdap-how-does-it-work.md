---
description: >-
  GDAP (Granular Delegated Admin Privileges) is Microsoft's security model that
  allows Managed Service Providers (MSPs) to access and manage their customers'
  Microsoft 365 tenants.
---

# What Is GDAP? How Does It Work?

#### Overview

GDAP (Granular Delegated Admin Privileges) is Microsoft's security model that allows Managed Service Providers (MSPs) to access and manage their customers' Microsoft 365 tenants with precise, time-limited, and role-based permissions.

#### What Problem Does GDAP Solve?

The legacy Delegated Admin Privileges (DAP) model gave MSPs broad, permanent Global Administrator access to customer tenants. This created several problems:

* **Over-privileged access:** MSPs had more permissions than needed for most tasks
* **No time limits:** Access never expired, creating ongoing security risk
* **No granularity:** All MSP users had the same level of access
* **Compliance concerns:** Customers couldn't restrict what MSPs could access
* **Audit challenges:** Difficult to track which MSP technician performed which action

GDAP replaces DAP with a more secure, granular approach.

#### How GDAP Works

**1. Role-Based Access**

Instead of blanket Global Administrator access, MSPs request specific Azure AD roles:

* **Helpdesk Administrator** - Reset passwords, manage basic support tickets
* **User Administrator** - Manage users and groups
* **Exchange Administrator** - Manage Exchange Online
* **Security Administrator** - Manage security settings
* **Global Reader** - Read-only access to everything

MSPs can request multiple roles based on their service agreement with each customer.

**2. Security Group Assignment**

MSPs assign GDAP permissions to Azure AD security groups, not individual users:

```
Example Structure:
├── Tier 1 Helpdesk (Security Group)
│   └── GDAP Roles: Helpdesk Administrator, Directory Readers
│
├── Tier 2 Support (Security Group)
│   └── GDAP Roles: User Administrator, Exchange Administrator
│
└── Senior Engineers (Security Group)
    └── GDAP Roles: Global Administrator, Security Administrator
```

**Key benefit:** Add or remove users from security groups to control their customer access - no need to modify GDAP relationships.

**3. Time-Limited Relationships**

GDAP relationships have expiration dates (maximum 2 years). This forces regular review of access needs and ensures terminated relationships don't persist indefinitely.

**4. Customer Approval Required**

Customers must explicitly approve GDAP relationships. They can:

* Review requested roles before approving
* Set custom expiration dates
* Terminate relationships at any time
* Monitor which MSP users are accessing their tenant

#### GDAP vs. DAP Comparison

| Feature                      | DAP (Legacy)                   | GDAP (Current)                         |
| ---------------------------- | ------------------------------ | -------------------------------------- |
| **Permission Level**         | Global Admin only              | 29+ granular Azure AD roles            |
| **Expiration**               | Never expires                  | Maximum 2 years, renewable             |
| **Access Control**           | All MSP users have same access | Role-based via security groups         |
| **Customer Control**         | None after initial consent     | Can review, approve, terminate anytime |
| **Audit Trail**              | Limited visibility             | Detailed per-user activity logs        |
| **Compliance**               | Difficult                      | Supports least-privilege principle     |
| **Microsoft Recommendation** | Deprecated (ends in 2024)      | Required for all new relationships     |

#### How GDAP Relationships Are Created

**Step 1: MSP Initiates Request**

The MSP creates a GDAP relationship request in the Microsoft Partner Portal:

* Specifies customer tenant
* Selects required Azure AD roles
* Assigns MSP security groups
* Sets duration (up to 2 years)

**Step 2: Customer Receives Invitation**

Customer receives an email with a link to review the request:

* Can see exactly which roles are requested
* Can modify the expiration date
* Can approve or reject

**Step 3: Active Relationship**

Once approved:

* Members of assigned MSP security groups gain the specified roles in the customer tenant
* Access is logged in Azure AD audit logs
* Relationship appears in both MSP and customer admin centers

**Step 4: Ongoing Management**

* MSP can add/remove users from security groups (no customer approval needed)
* Customer can monitor access activity
* Either party can terminate the relationship
* Both parties receive notifications before expiration

#### Key GDAP Concepts

**Access Containers**

An "access container" is the security group in the MSP tenant that's granted GDAP permissions. Only members of these groups can access the customer tenant.

**Relationship Duration**

* Minimum: 1 day
* Maximum: 730 days (2 years)
* Can be renewed before expiration
* Both parties notified 60 days before expiration

**Status Types**

* **Active:** Relationship is functioning, members can access customer tenant
* **Approved:** Customer approved but not yet active
* **Expiring:** Less than 60 days until expiration
* **Expired:** No longer valid, access revoked
* **Terminated:** Ended by either party

#### Why MSPs Should Use GDAP

1. **Customer trust:** Demonstrates commitment to security best practices
2. **Compliance:** Required for SOC 2, ISO 27001, and similar certifications
3. **Liability reduction:** Limits exposure from over-privileged access
4. **Operational efficiency:** Proper role assignment reduces security incidents
5. **Microsoft requirement:** DAP is being deprecated, GDAP is mandatory

#### Why Customers Should Require GDAP

1. **Control:** You decide which roles your MSP needs
2. **Visibility:** You can see exactly who accessed your tenant and when
3. **Security:** Least-privilege access reduces risk
4. **Auditability:** Full audit trail for compliance purposes
5. **Flexibility:** You can terminate access immediately if needed

#### Related Articles

* How 365TUNE Uses GDAP for Access Control
* Setting Up GDAP for 365TUNE
* Managing User Access with GDAP
* GDAP Best Practices for MSPs

Read more: [Introduction to granular delegated admin privileges (GDAP)](https://learn.microsoft.com/en-us/partner-center/customers/gdap-introduction)
