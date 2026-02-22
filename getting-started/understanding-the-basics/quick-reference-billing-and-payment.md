---
description: This guide explains how billing and payments work for the 365tune.
---

# Quick Reference: Billing & Payment

### Plans & Pricing

We offer two subscription options depending on your needs:

<table data-full-width="false"><thead><tr><th>Plan</th><th width="110">Platform Fee</th><th>Cost Per License</th><th width="113">Reporting Agents</th><th width="108">AI Agent Tokens</th><th>Tenants &#x26; Users</th></tr></thead><tbody><tr><td><strong>Standard</strong></td><td>$99</td><td>$0.02/License</td><td>5 Seats</td><td>1 Million</td><td>Unlimited</td></tr><tr><td><strong>Enterprise*</strong></td><td>$99</td><td>$0.05/License</td><td>5 Seats</td><td>1 Million</td><td>Unlimited</td></tr></tbody></table>

* **All costs are per month basis**
* **Platform Fee:** This fee covers All features, reports and dashboards
* **Reporting Agents:** Admin/Agents who can access the platform. Additional agents can be purchased if needed.

\*Enterprise Plan is currently in Private Preview, Estimated General Availability is Q3 2026.

### What Counts as a License?

Billing is based on the **total purchased Microsoft 365 licenses** in your tenant. Only primary licenses are considered for billing, these include:

* **Business Plans:** Business Basic, Business Standard, Business Premium, Office 365 Business Essentials (legacy), Office 365 Business Premium (legacy)
* **Enterprise Plans:** Microsoft 365 E1/E3/E5, Office 365 E1/E3/E5 (legacy)
* **Frontline Worker Plans:** F1, F3
* **Education Plans:** Office 365 Education (Faculty and Student versions)
* **Government Plans:** Office 365 GCC and GCC High

{% hint style="success" %}
<mark style="color:$primary;">License counts are taken</mark> <mark style="color:$primary;"></mark><mark style="color:$primary;">**directly from the Microsoft Graph API**</mark> <mark style="color:$primary;"></mark><mark style="color:$primary;">(</mark><mark style="color:$primary;">`subscribedSkus`</mark><mark style="color:$primary;">), ensuring transparency and accuracy.</mark>
{% endhint %}

### Add-ons

Optionally, Add-ons can be purchased to increase number of Admin seats and to purchase additional AI tokens to use with AI Agent.

<table data-full-width="false"><thead><tr><th>Add-ons</th><th>Cost Per Month</th></tr></thead><tbody><tr><td>Reporting Agents</td><td>$10 / Agent</td></tr><tr><td>AI Tokens</td><td>$25 / 1 Million Tokens</td></tr></tbody></table>

{% hint style="success" %}
<mark style="color:$primary;">All features are included in the platform fee. There are no feature, report or dashboard specific Add-ons.</mark>
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
