# Managing Access to 365TUNE

Learn how to securely manage user access to the 365TUNE app using Microsoft Entra ID (formerly Azure AD). This step-by-step guide covers the process for Global Administrators to grant app access, assign roles, and control permissions. Understand the different user roles—All Reports User, Finance User, and IT User—and ensure only authorized personnel can view sensitive reports.

***

### 🔐 How to Grant User Access to 365Tune via Microsoft Entra ID (formerly Azure AD)

#### 🔎 Overview

365Tune is a secure Microsoft 365 reporting tool designed with strict access control. By default, **only Global Administrators** and **Global Admin-approved users** can access the app. This ensures sensitive data such as license usage, productivity, and financial reports are accessible only to authorized users.

***

#### 🛡️ Who Can Access 365Tune?

| User Type                           | Access                                                       |
| ----------------------------------- | ------------------------------------------------------------ |
| **Global Administrators**           | ✅ Full access by default once consent is granted             |
| **Finance Users, IT Staff, Others** | ❌ Must be manually assigned a role by a Global Administrator |

***

#### ✅ Step-by-Step: How to Grant Access to a User

Only a **Global Administrator** can perform this task.

1. **Login to Microsoft Entra ID (Azure Active Directory)**\
   Go to the [Microsoft Entra Admin Center](https://entra.microsoft.com/) and log in with your Global Administrator credentials.
2. **Navigate to Enterprise Applications**
   * In the left-hand menu, select **“Enterprise applications”**.
   * In the list of applications, search for and select **365TUNE**.
3. **Go to Users and Groups**
   * In the 365TUNE app overview, click **“Users and groups”** from the side panel.
4. **Add a New User**
   * Click **“Add user/group”**.
   * Search and select the desired user (e.g., a finance or IT team member).
5. **Assign a Role**
   * Choose the appropriate **app role** for the user:
     * **All Reports User** – Full read-only access to all reports.
     * **Finance User** – Access only to financial/license cost reports.
     * **IT User** – Access to all reports **except** financial reports.
   * Click **“Assign”**.
6. **Save and Confirm**
   * The user now has access based on the role assigned.
   * You can always edit or remove roles from this menu later.

***

#### 🚦 Understanding 365Tune App Roles

| Role Name            | Access Scope                               | Editable Config?  | Use Case                                      |
| -------------------- | ------------------------------------------ | ----------------- | --------------------------------------------- |
| **All Reports User** | ✅ All reports                              | ❌ No – Read-only  | Senior IT and Finance leadership              |
| **Finance User**     | ✅ Financial reports only                   | ❌ No  – Read-only | Finance team members                          |
| **IT User**          | ✅ All reports **except** financial reports | ❌ No – Read-only  | System admins, helpdesk, infrastructure teams |

***

#### ❌ What Happens If a User Has No Role?

If a user attempts to access the 365Tune app **without a role assigned**, they will see the following error message:

> <img src="../../.gitbook/assets/2025-05-24 17_10_17-Microsoft 365 Reporting Tool _ 365Tune - Work - Microsoft​ Edge.png" alt="" data-size="original">

In such cases, the user must **reach out to a Global Administrator** and request role-based access via the steps above.

***

#### 💬 Support

If you're unsure which role to assign or encounter issues, contact the 365Tune support team at [support@365tune.com](mailto:support@365tune.com).

***
