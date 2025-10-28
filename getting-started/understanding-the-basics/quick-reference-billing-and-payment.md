---
description: This guide explains how billing and payments work for the 365tune.
---

# Quick Reference: Billing & Payment

### Plans & Pricing

We offer two subscription options depending on your needs:

<table><thead><tr><th>Plan</th><th width="131">Monthly Fee</th><th width="142">Users Included</th><th>Extra Users</th><th width="171">Reporting Agents</th><th>Data Retention</th><th>Support</th></tr></thead><tbody><tr><td><strong>Standard</strong></td><td>$99</td><td>300</td><td>$0.02/user</td><td>5 (add $10/agent)</td><td>12 months</td><td>Email &#x26; Chat (business hrs)</td></tr><tr><td><strong>Enterprise</strong></td><td>$99</td><td>300</td><td>$0.05/user</td><td>10 (add $10/agent)</td><td>36 months</td><td>Priority SLA</td></tr></tbody></table>

**Explanation of key terms:**

* **Users Included:** Number of Microsoft 365 licensed users covered by the base fee.
* **Extra Users:** Cost per user beyond the included limit.
* **Reporting Agents:** Admin/Agents who can access the platform. Additional agents can be purchased if needed.
* **Data Retention:** How long your reporting data is stored and accessible.

### Who Counts as a User?

Billing is based on the **total purchased Microsoft 365 licenses** in your tenant. Only primary licenses are considered for billing, these include:

* **Business Plans:** Business Basic, Business Standard, Business Premium, Office 365 Business Essentials (legacy), Office 365 Business Premium (legacy)
* **Enterprise Plans:** Microsoft 365 E1/E3/E5, Office 365 E1/E3/E5 (legacy)
* **Frontline Worker Plans:** F1, F3
* **Education Plans:** Office 365 Education (Faculty and Student versions)
* **Government Plans:** Office 365 GCC and GCC High

{% hint style="success" %}
<mark style="color:$primary;">License counts are taken</mark> <mark style="color:$primary;"></mark><mark style="color:$primary;">**directly from the Microsoft Graph API**</mark> <mark style="color:$primary;"></mark><mark style="color:$primary;">(</mark><mark style="color:$primary;">`subscribedSkus`</mark><mark style="color:$primary;">), ensuring transparency and accuracy.</mark>
{% endhint %}

### Billing Basics

* **Billing Frequency:**
  * Monthly subscriptions are billed on your signup anniversary date each month.
  * Annual subscriptions are billed on your signup anniversary date.
* **User Counts:**
  * Calculated at the **end of each billing cycle**.
  * Based on Microsoft Graph API data (`subscribedSkus`).
  * Mid-month/year license changes (additions/removals) do **not** trigger immediate billing; adjustments appear on the following bill.

### Plan Changes

* **Upgrades:** Apply immediately. You get access to the new features right away, and the remaining month/year is billed immediately at the new rate on prorated basis.
* **Downgrades:** Apply starting from the next billing cycle (no partial refunds).
* **Additional Agents:** Can be added anytime and the remaining month/year is billed immediately at the new rate on prorated basis.

### Policy Updates

This billing policy may be updated. Material changes will be communicated at least **30 days in advance**. Continued use of the service indicates acceptance of updated terms.
