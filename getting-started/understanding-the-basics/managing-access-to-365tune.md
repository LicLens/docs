---
description: >-
  Learn how to securely manage user access to the 365TUNE app. This step-by-step
  guide covers the process for an Administrators to grant app access, assign
  roles, and control permissions.
---

# Managing Access to 365TUNE

### Initial Setup and Default Administrator

#### Onboarding Process

During the initial onboarding of 365TUNE, a Microsoft Entra ID Global Administrator must grant consent to the application. This consent process:

1. Establishes the connection between your Entra ID tenant and 365TUNE
2. The **person who initially signs up** for the application becomes the **Default Administrator** in 365TUNE
3. This Default Administrator receives full administrative privileges within the platform

The key distinction is that:

* The **Global Administrator** grants the necessary permissions/consent for the application to integrate with the tenant
* The **person who signs up first** (which could be the same Global Admin or a different user) becomes the Default Administrator in 365TUNE

{% hint style="info" %}
The Default Administrator has complete control over the 365TUNE platform and is responsible for Appointing additional administrators as needed. Global Administrators will not have access to the platform by default.
{% endhint %}

### Step-by-Step: How to Grant Access to a User

#### Accessing User Management

To invite new users to the 365TUNE platform:

1. **Login** to 365TUNE with administrator credentials
2. **Navigate** to **Settings** > **Permissions and Roles**
3. **Click** the **+New User** button

<div align="left"><figure><img src="../../.gitbook/assets/image (7).png" alt="" width="304"><figcaption><p>Click on '+ New User' to invite a new user tot he platform</p></figcaption></figure></div>

4. Select the user and assign appropriate role

Only a user with Admin Role can perform this task.

#### Understanding Roles

The platform has four default roles;

1. Admin
2. All Report Access Users
3. IT Helpdesk Users
4. Financial Analyst Users

An Admin can create custom roles and assign appropriate access to each report category as required.

#### What Happens If a User Has No Role?

If a user attempts to access the 365Tune app **without a role assigned**, they will see the following error message:

> <img src="../../.gitbook/assets/2025-05-24 17_10_17-Microsoft 365 Reporting Tool _ 365Tune - Work - Microsoft​ Edge.png" alt="" data-size="original">

In such cases, the user must **reach out to an Administrator** and request role-based access via the steps above.

#### 💬 Support

If you're unsure which role to assign or encounter issues, contact the 365Tune support team at [support@365tune.com](mailto:support@365tune.com).

***
