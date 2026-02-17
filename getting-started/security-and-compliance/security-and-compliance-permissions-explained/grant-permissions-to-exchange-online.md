---
description: >-
  If you want to assess Exchange Online security and configuration controls, you
  must grant the required permissions to Exchange.
---

# Grant Permissions to Exchange Online

By default, 365TUNE connects to Microsoft Graph to assess identity, directory, and core Microsoft 365 security configurations.

However, Some Exchange Online configuration data exists outside of Microsoft Graph and requires additional workload-specific permissions.&#x20;

Enable Exchange connection if you want 365TUNE to assess:

* Anti-phishing policies
* Anti-malware configuration
* Mail flow (transport) rules
* Mailbox audit settings
* Exchange administrative role assignments

These steps are optional. 365TUNE operates in read-only mode and does not modify your environment.

If you do not need these checks, you can skip this section.

### Prerequisites

Before proceeding, ensure:

1. You have one of the following roles:
   * Global Administrator
   * Exchange Administrator
2. Exchange Online PowerShell [module is installed](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps)
3. You know your Maester Application (Client) ID

### Step 1 – Connect to Exchange Online

Connect to Echange online

```powershell
Connect-ExchangeOnline
```

#### What This Step Does

* Establishes a secure remote PowerShell session
* Authenticates you to Exchange Online
* Enables management of Exchange role assignments

### Step 2 – Grant View-Only Access to the Application
