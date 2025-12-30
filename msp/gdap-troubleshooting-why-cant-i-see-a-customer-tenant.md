# GDAP Troubleshooting: Why Can't I See a Customer Tenant?

### Overview

If you can’t see a customer tenant in **365tune**, it’s usually due to **GDAP access**, **customer consent**, or **role assignment** issues.

365tune uses **Granular Delegated Admin Privileges (GDAP)** as the **authoritative access control** for MSP users. Even if a customer is onboarded to 365tune, **MSP users can view a tenant only when they have active GDAP permissions**.

Use this guide to identify and resolve the most common causes.

### How Access Is Determined

A customer tenant appears in 365TUNE **only if all conditions below are met**:

1. The customer tenant is onboarded to 365TUNE
2. A GDAP relationship exists between your MSP and the customer
3. You (the MSP user) have active GDAP roles for that tenant

If **any** condition fails, the tenant won’t be visible.

### Common Reasons and How to Fix Them

#### 1. No Active GDAP Relationship

**Symptom**

* Customer tenant does not appear at all

**Cause**

* No GDAP relationship exists, or it has expired

**How to Fix**

1. Sign in to **Microsoft Partner Center**
2. Go to **Customers → Relationships**
3. Verify the GDAP relationship is **Active**
4. Recreate or renew the GDAP relationship if needed

> Legacy DAP relationships are not sufficient.

#### 2. You Are Not Assigned to the GDAP Relationship

**Symptom**

* Other MSP users can see the customer, but you cannot

**Cause**

* You are not included in the GDAP relationship or security group

**How to Fix**

1. In Partner Center, open the customer’s GDAP relationship
2. Verify your user account or security group is assigned
3. Ensure the relationship includes you explicitly

#### 3. Missing or Insufficient GDAP Roles

**Symptom**

* Customer is visible, but reports or features are missing

**Cause**

* Your assigned GDAP roles don’t allow access to those features

**How to Fix**

* Ensure your GDAP assignment includes appropriate roles, such as:
  * Global Reader
  * Reports Reader
  * Security Reader

Role changes can take a few minutes to propagate.

#### 4. Customer Has Not Completed 365TUNE Consent

**Symptom**

* Customer does not appear for any MSP user

**Cause**

* The customer or a Privileged MSP user hasn’t granted application permissions to 365TUNE

**How to Fix**

1. Ask the customer to complete the 365TUNE onboarding flow
2. Confirm application consent was approved in their tenant
3. Once consent is granted, data collection will begin automatically

#### 5. GDAP Relationship Has Expired or Was Revoked

**Symptom**

* Customer was visible previously but disappeared

**Cause**

* The GDAP relationship expired or was manually revoked by the customer

**How to Fix**

* Create a new GDAP relationship in Partner Center
* Ask the customer to approve the new request

Access is restored once the relationship becomes active.

#### 6. New GDAP Changes Have Not Propagated Yet

**Symptom**

* GDAP was just assigned, but the tenant is still not visible

**Cause**

* Microsoft role propagation delay

**How to Fix**

* Wait 5–15 minutes
* Sign out and sign back in to 365tune
* Refresh the tenant list

### Quick Checklist

Before contacting support, verify:

* ✅ Customer or a Privileged MSP user has completed 365TUNE onboarding
* ✅ GDAP relationship is **Active**
* ✅ You are assigned to the GDAP relationship
* ✅ Required roles are included
* ✅ GDAP has not expired
* ✅ Changes have had time to propagate

### Important Notes

* Application permissions **do not** grant MSP user access
* GDAP expiration results in **immediate access removal**
* 365TUNE does not cache or retain access after GDAP changes
* Each MSP user is evaluated individually

### Summary

If you can’t see a customer in 365TUNE, the issue is almost always related to **GDAP status or role assignment**.

* 365TUNE relies exclusively on GDAP for MSP access
* Access is role-based, time-bound, and tenant-specific
* Fixing the GDAP relationship resolves most visibility issues
