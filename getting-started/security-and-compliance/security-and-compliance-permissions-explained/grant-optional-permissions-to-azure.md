---
description: >-
  This guide explains why and how to grant the required Azure RBAC permissions
  for 365TUNE to securely validate your Azure and Microsoft Entra
  configurations.
---

# Grant Optional Permissions to Azure

Azure Role-Based Access Control (RBAC) uses hierarchical scopes defined by Uniform Resource Names (URNs), separated by `/`.

Some Azure configuration settings exist at the **tenant root scope (`"/"`)** and under the **Microsoft Entra ID provider (`Microsoft.aadiam`)**. Microsoft restricts interactions at these scopes.

To allow 365TUNE to:

* Read tenant-level configuration
* Validate security posture
* Execute compliance tests
* Perform Azure configuration assessments

You must assign **Reader** permissions at:

* Root scope (`"/"`)
* Microsoft Entra ID provider scope (`/providers/Microsoft.aadiam`)

{% hint style="info" %}
365TUNE only requires **read-only** access. No write or modification permissions are granted.
{% endhint %}

### Prerequisite:

**Global Administrator** Permissions is required to run the script to grant required permissions in Microsoft Entra ID

This is required only to temporarily elevate your own access to assign the role at root scop.

### What this script will do:

When executed by a Global Administrator, the script will:

1. Install required Azure PowerShell modules
2. Prompt you to sign in
3. Temporarily elevate your access to the root scope
4. Assign **Reader** role to 365TUNE at:
   * Root scope (`"/"`)
   * Microsoft Entra ID provider scope
5. Remove your temporary elevated root access

This follows security best practices and least-privilege principles.



```powershell
$servicePrincipal = "<Object ID of the Entra App>" 
$subscription = "<Any Subscription ID>" 
Install-Module Az.Accounts -Force 
Install-Module Az.Resources -Force 
Connect-AzAccount 

#Elevate to root scope access 
$elevateAccess = Invoke-AzRestMethod -Path "/providers/Microsoft.Authorization/elevateAccess?api-version=2015-07-01" -Method POST

#Assign permissions to Enterprise App 
New-AzRoleAssignment -ObjectId $servicePrincipal -Scope "/" -RoleDefinitionName "Reader" -ObjectType "ServicePrincipal" 
New-AzRoleAssignment -ObjectId $servicePrincipal -Scope "/providers/Microsoft.aadiam" -RoleDefinitionName "Reader" -ObjectType "ServicePrincipal"

#Remove root scope access 
$assignment = Get-AzRoleAssignment -RoleDefinitionId 18d7d88d-d35e-4fb5-a5c3-7773c20a72d9|?{$.Scope -eq "/" -and $.SignInName -eq (Get-AzContext).Account.Id} 
$deleteAssignment = Invoke-AzRestMethod -Path "$($assignment.RoleAssignmentId)?api-version=2018-07-01" -Method DELETE
```
