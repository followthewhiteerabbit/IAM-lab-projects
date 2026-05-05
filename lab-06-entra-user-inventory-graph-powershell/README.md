← [Back to Portfolio](../README.md)

# Entra ID User Inventory with Microsoft Graph PowerShell

| | |
|---|---|
| **Difficulty** | Beginner–Intermediate |
| **Time** | 20–30 min |
| **SC-300** | Implement and manage user identities |

## Objective
Connect to Microsoft Graph via PowerShell, export all tenant users to CSV, and validate the output.

## Prerequisites
- Microsoft Entra ID tenant
- PowerShell 7+ with `Microsoft.Graph` module installed
- `User.ReadWrite.All` scope / User Administrator role

## Steps

**1. Connect to Microsoft Graph**
```powershell
Connect-MgGraph -Scopes "User.ReadWrite.All"
```

**2. Export all users to CSV**
```powershell
Get-MgUser -All | Select-Object DisplayName, UserPrincipalName | Export-Csv -Path "C:\users_report.csv" -NoTypeInformation
```

**3. Verify the file exists**
```powershell
Test-Path "C:\users_report.csv"
```

**4. Open the CSV**
```powershell
Invoke-Item "C:\users_report.csv"
```

## Output
20 users returned, including named accounts, test accounts, a Break Glass Admin, and one B2B guest (`#EXT#` in UPN). Identified a data quality issue: `Contractors.Tets` (typo — should be `Contractors.Test`).

## What I Learned
- Microsoft Graph SDK replaces the deprecated `AzureAD` and `MSOnline` modules
- `-Scopes` triggers an OAuth 2.0 delegated consent flow — permissions are explicit, not inherited
- `#EXT#` in a UPN identifies a B2B guest account
- User inventory exports surface provisioning errors and naming standard drift

---
> **Recruiter Value:** Hands-on use of Microsoft Graph PowerShell to audit Entra ID identities — directly applicable to identity governance and access review workflows.
