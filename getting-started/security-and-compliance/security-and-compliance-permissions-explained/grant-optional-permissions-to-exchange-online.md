---
description: >-
  If you want to assess Exchange Online security and configuration controls, you
  must grant the required permissions to Exchange.
---

# Grant Optional Permissions to Exchange Online

By default, 365TUNE connects to Microsoft Graph to assess identity, directory, and core Microsoft 365 security configurations.

However, Some Exchange Online configuration data exists outside of Microsoft Graph and requires additional workload-specific permissions.&#x20;

{% hint style="info" %}
Enable this Exchange connection if you want 365TUNE to assess:

* Anti-phishing policies
* Anti-malware configuration
* Mail flow (transport) rules
* Mailbox audit settings
* Exchange administrative role assignments

**These steps are optional. If you do not need these checks, you can skip this section.**
{% endhint %}

These permission can be granted by installing 365TUNE PowerShell module.

### What this step does:

This step will

1. Assign **Exchange.ManageAsApp** permission to the 365TUNE Service Principle in Entra ID. (Exchange.ManageAsApp is the authentication gate for Exchange Online PowerShell app-only connection&#x73;**.** It does not, by itself, grant read or write access to any Exchange data.)
2. Assigns Exchange’s built-in **View-Only** role to the to the 365TUNE Service Principle in Entra ID.

### Prerequisites

Before proceeding, ensure your account have one of the following roles:

* Global Administrator
* Exchange Administrator

### Step 1 - Login to Azure Cloud Shell

We recommend using  Azure Cloud Shell, alternatively you can use PowerShell v7+ locally.

Navigate to [https://portal.azure.com/#cloudshell/](https://portal.azure.com/#cloudshell/)

### Step 2 - Install 365TUNE module

Run command&#x20;

{% code title="PowerShell" %}
```powershell
Install-Module 365TUNE -Scope CurrentUser
```
{% endcode %}

### Step 3 - Invoke Exchange connect function

Run command

{% code title="PowerShell" %}
```powershell
Invoke-365TuneConnectExchange
```
{% endcode %}

***

## Alternative Options

These permission also can be granted manually:

1. [Add Exchange API Permissions](grant-optional-permissions-to-exchange-online.md#step-1-add-exchange-api-permissions)
2. [Connect to Exchange online](grant-optional-permissions-to-exchange-online.md#step-2-connect-to-exchange-online-powershell-module)
3. [Grant View-Only Access to the Application](grant-optional-permissions-to-exchange-online.md#step-3-grant-view-only-access-to-the-application)

### Manual Steps Prerequisites

Before proceeding, ensure:

1. You have one of the following roles:
   * Global Administrator
   * Exchange Administrator
2. Exchange Online PowerShell [module is installed](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps)
3. You know your "365TUNE Security and Compliance" Applications Object ID
   1. Login to [https://entra.microsoft.com/](https://entra.microsoft.com/)
   2. Navigate to "Enterprise Apps"
   3. Search and open "365TUNE Security and Compliance"
   4. Copy "Object ID" from Overview or Properties

### Step 1 - Add Exchange API Permissions

#### What this step does:

* Allows the application to authenticate directly with Exchange Online
* Enables app-only access

Further Explanation: Before assigning Exchange roles via PowerShell, you must first allow the application to authenticate directly against Exchange Online. This is done by granting the **Exchange.ManageAsApp** application permission. **Exchange.ManageAsApp** is the authentication gate for Exchange Online PowerShell app-only connection&#x73;**.** It does no, by itself, grant read or write access to any Exchange data.

To add Exchnage API Permissions, follow these Steps:

* Open the application "365TUNE Security and Compliance" (Refer Step 3 in prerequsites)
* Select **API permissions** > **Add a permission**
* Select **APIs that my organization uses** > search for **Office 365 Exchange Online** > **Application permissions**
* Search for `Exchange.ManageAsApp`
* Select **Add permissions**
* Select **Grant admin consent for \[your organization]**
* Select **Yes** to confirm

### Step 2 - Connect to Exchange Online PowerShell Module

#### What this step does:

* Establishes a secure remote PowerShell session
* Authenticates you to Exchange Online
* Enables management of Exchange role assignments

Open a Powershell window and run below commands;

{% code title="PowerShell" lineNumbers="true" %}
```powershell
Connect-ExchangeOnline
```
{% endcode %}

Login with your 'Global Administrator' or 'Exchange Online Administrator' Account.

### Step 3 - Grant View-Only Access to the Application

Grant View-Only Access for the 365TUNE - Security and Compliance application

#### What this step does:

* Assigns Exchange’s built-in View-Only role to the application.

This step follows the principle of least privilege. Mailbox content or configuration changes are not allowed with these permissions.

{% code title="PowerShell" overflow="wrap" lineNumbers="true" %}
```powershell
$AppId = "2f30a894-e110-497c-b4bf-21ffd0b86de9" 
$ObjectId = "<insert object ID from Entra Portal>" #refer step 3 in prerequsites
$DisplayName = "365TUNE - Security and Compliance"
New-ServicePrincipal -AppId $AppId -ObjectId $ObjectId -DisplayName $DisplayName 
New-ManagementRoleAssignment -Role "View-Only Configuration" -App $DisplayName
```
{% endcode %}

At this point, Exchange Online has been successfully configured for read-only assessment access. The 365TUNE - Security and Compliance application can securely authenticate to Exchange and retrieve configuration data based on the assigned View-Only role.
