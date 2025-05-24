---
description: This article explains the permission requirements of 365TUNE.
---

# Permission Requirements

365TUNE is a secure and powerful reporting tool designed to assist IT administrators, IT leaders, and finance teams in gaining valuable insights into license usage, generating financial reports, and ensuring security compliance. To securely access the necessary data, 365TUNE requires specific permissions, which are granted through a one-time setup process by a Microsoft 365 Global Administrator.

## 1. Role of the Global Administrator

365TUNE relies on secure, Microsoft-managed authentication to establish a connection with your Microsoft 365 environment. During the onboarding, the app seamlessly connects to the Microsoft 365 environment using the Enterprise Application registration process in Azure Active Directory.

To begin using 365TUNE, a Global Administrator must log into the Microsoft 365 Admin Portal and **grant** **consent** for 365TUNE to access certain Microsoft 365 data required for reporting purposes. This is a one-time process, and it is the only time Global Admin credentials are needed.

The permissions requested by 365TUNE are minimal, and the Global Admin will only approve the access necessary for the application to work. After this one-time consent, 365TUNE can function with the permissions granted, without requiring further involvement from the Global Admin.

{% hint style="success" %}
Global Admin will login only one-time into Microsoft portal for the Entra ID App registration process. 365TUNE does **not** access, store or retain Global Administrator credentials
{% endhint %}

## 2. Permissions for Data Access

365TUNE operates with **read-only** permissions, which means it can access but not modify any data. This approach helps minimize any security risks and ensures that the tool can only view, analyze, and generate reports on the necessary data. Example of the permissions granted during setup include:

* **User.Read.All**: Allows 365TUNE to read user profile information, such as license assignments and user details, which is necessary for the reporting tool to generate accurate license usage reports.
* **Reports.Read.All**: Grants access to Microsoft 365 usage reports, so 365TUNE can compile data on license usage patterns and help organizations monitor compliance.

{% hint style="info" %}
To Learn more about permission requirements refer [this article](permissions-explained.md)
{% endhint %}

These permissions ensure that 365TUNE can read and analyze data but cannot make changes to the environment, helping to maintain the integrity and security of your Microsoft 365 tenant.

## 3. How 365TUNE Uses Permissions

365TUNE uses **Application permissions** to access Microsoft 365 data. This means that the application can function without requiring a signed-in user and can perform tasks in the background, such as collecting and analyzing data for reports. This method of access is secure and operates independently of any user sessions, allowing 365TUNE to gather data autonomously, without needing to authenticate users each time.

Since 365TUNE operates with read-only permissions, the application cannot modify or delete data, ensuring that any data analysis is conducted in a secure and non-intrusive manner.

## 4. Step-by-Step Process for Granting Permissions

Here’s a breakdown of the process involved in Application registration:

1. **Global Admin Logs In**: When prompted during the onboarding process, The Global Administrator logs into the Microsoft 365 Admin Portal.
2. **Review Permissions**: The Global Admin reviews the permissions 365TUNE will request.
3. **Grant Consent**: The Global Admin grants consent for 365TUNE to access the necessary data with the approved permissions.
4. **App Registration**: 365TUNE completes the registration in Microsoft’s identity platform, creating a secure connection for ongoing data access.

This process ensures that only authorized applications have access to your Microsoft 365 environment, and it is designed to be transparent and secure.

## 5. Ongoing Management and Data Security

Once the setup is complete, 365TUNE can run independently, using the permissions granted during the initial setup. It does not require additional admin involvement unless changes are needed.

{% hint style="success" %}
Administrators can review, modify, or revoke 365TUNE’s permissions at any time through the Microsoft 365 Admin Center.
{% endhint %}

The application will continue to work securely with the read-only permissions it has been granted, and it will not store any sensitive information, such as Global Admin credentials, at any stage.

#### Conclusion

365TUNE is a secure and powerful reporting tool that simplifies license management and compliance tracking within Microsoft 365. By requiring only read-only access to specific data, it minimizes security risks and ensures that no data is modified or deleted. The initial setup requires Global Administrator consent, but the credentials are not stored by 365TUNEE, ensuring that your organization’s security remains intact. Once set up, 365TUNEE operates autonomously with the necessary permissions, providing valuable insights while maintaining strict data security and compliance standards.
