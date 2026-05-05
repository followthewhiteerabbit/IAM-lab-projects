← [Back to Portfolio](../README.md)

# Entra ID User Inventory with Microsoft Graph PowerShell

| | |
|---|---|
| **Difficulty** | Beginner–Intermediate |
| **Estimated Time** | 20–30 minutes |
| **SC-300 Exam Objective** | Implement and manage user identities (Domain 1) |

---

## Objective

The objective of this lab is to use the Microsoft Graph PowerShell SDK to connect to an Entra ID tenant, export a full user inventory to CSV, and validate the output. This exercise demonstrates how an IAM engineer can programmatically enumerate identities for auditing, access reviews, and data quality assessments — a core responsibility in enterprise identity governance.

---

## Prerequisites

- Microsoft Entra ID tenant with at least one active user account
- PowerShell 7+ installed
- Microsoft.Graph PowerShell module installed (`Install-Module Microsoft.Graph`)
- Permissions: `User.ReadWrite.All` (or `User.Read.All` for read-only)
- Global Administrator or User Administrator role (for consent)

---

## Steps

**Step 1 — Connect to Microsoft Graph**

Open PowerShell and authenticate to your tenant using the Microsoft Graph SDK. The `-Scopes` parameter requests delegated permissions for user read/write access.

```powershell
Connect-MgGraph -Scopes "User.ReadWrite.All"
```

A browser window will open prompting you to sign in and consent to the requested scope.

---

**Step 2 — Export All Users to CSV**

Use `Get-MgUser` with the `-All` flag to retrieve every user in the tenant. Pipe the results through `Select-Object` to limit the output to display name and UPN, then export to a CSV file.

```powershell
Get-MgUser -All | Select-Object DisplayName, UserPrincipalName | Export-Csv -Path "C:\users_report.csv" -NoTypeInformation
```

The `-NoTypeInformation` flag suppresses the `#TYPE` header line that PowerShell adds by default.

---

**Step 3 — Verify the File Was Created**

Confirm the CSV file exists at the expected path before attempting to open it.

```powershell
Test-Path "C:\users_report.csv"
```

A return value of `True` confirms the file was written successfully.

---

**Step 4 — Open and Review the CSV**

Launch the CSV in the default application (typically Excel) to visually inspect the user inventory.

```powershell
Invoke-Item "C:\users_report.csv"
```

---

## Full PowerShell Script

```powershell
# Lab 06 — Entra ID User Inventory via Microsoft Graph PowerShell
# SC-300 Objective: Implement and manage user identities

# Step 1: Connect to Microsoft Graph with required scope
Connect-MgGraph -Scopes "User.ReadWrite.All"

# Step 2: Export all tenant users to CSV
Get-MgUser -All | Select-Object DisplayName, UserPrincipalName | Export-Csv -Path "C:\users_report.csv" -NoTypeInformation

# Step 3: Verify the file was created
Test-Path "C:\users_report.csv"

# Step 4: Open the CSV for review
Invoke-Item "C:\users_report.csv"
```

---

## Expected Output

After running the script, the CSV file (`users_report.csv`) should contain a row for each user in the tenant. In this lab, **20 users** were returned, including:

- Named employee accounts (standard licensed users)
- Test accounts used for lab and policy validation
- A **Break Glass Admin** account (emergency access, excluded from Conditional Access)
- One **B2B guest user** identifiable by the `#EXT#` suffix in the UserPrincipalName (e.g., `partner_contoso.com#EXT#@tenant.onmicrosoft.com`)

**Sample CSV output:**

```
DisplayName,UserPrincipalName
Alex Johnson,alex.johnson@contoso.onmicrosoft.com
Break Glass Admin,breakglass.admin@contoso.onmicrosoft.com
Contractors.Tets,contractors.tets@contoso.onmicrosoft.com
ExternalUser,externaluser_partner.com#EXT#@contoso.onmicrosoft.com
```

> **Data Quality Finding:** One account was identified with a typo in its display name — `Contractors.Tets` instead of the expected `Contractors.Test`. This was flagged as a data quality issue, demonstrating the value of regular user inventory audits for detecting misconfigured or incorrectly provisioned accounts.

---

## What I Learned / Challenges

**Microsoft Graph vs. Azure AD Module:** This lab introduced the Microsoft Graph PowerShell SDK as the modern replacement for the deprecated `AzureAD` and `MSOnline` modules. Learning to authenticate with `Connect-MgGraph` and use `Get-MgUser` instead of `Get-AzureADUser` reflects where enterprise IAM tooling is heading.

**Scope-Based Consent Model:** Requesting `User.ReadWrite.All` through the `-Scopes` parameter initiates an OAuth 2.0 delegated consent flow. Understanding that permissions are explicitly requested per-session — rather than inherited — reinforced the principle of least privilege in API access.

**B2B Guest Identification:** The `#EXT#` pattern in a UPN is a reliable indicator of an Azure AD B2B guest account. Being able to identify and segregate these accounts from member users is important for access reviews and license management.

**Data Quality as a Security Signal:** The `Contractors.Tets` typo highlighted that user inventory exports aren't just for reporting — they're a tool for catching provisioning errors that could indicate a misconfigured account, a test account left in production, or an identity that has drifted from naming standards.

**Challenge — Output Scope:** `Get-MgUser` by default returns only a limited set of properties. Using `Select-Object` to scope the output and `-All` to paginate through large tenants are both important habits for production-scale identity work.

---

## Recruiter Value

> This lab demonstrates hands-on proficiency with the Microsoft Graph PowerShell SDK to programmatically audit Entra ID user identities — a directly transferable skill for identity governance, access reviews, and IAM automation in enterprise environments.
