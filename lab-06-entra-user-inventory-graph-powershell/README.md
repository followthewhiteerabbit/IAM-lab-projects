[← Back to Portfolio](../README.md)

# Automating Entra ID User Inventory with Microsoft Graph PowerShell



---

# Lab Overview

In any organization, knowing exactly who has access to your environment is the foundation of identity security. Over time, tenants accumulate stale accounts, misconfigured identities, orphaned guest users, and test accounts that were never cleaned up — all of which represent security risk. This lab simulates a real-world identity audit using Microsoft Graph PowerShell to programmatically export a full user inventory from Microsoft Entra ID. This is typically one of the first tasks an IAM engineer performs when onboarding to a new environment or preparing for an access review.

---

# Objective

In this lab, I used Microsoft Graph PowerShell to connect to a Microsoft Entra ID tenant and export a complete user inventory to a CSV file. The goal was to demonstrate how to programmatically audit identities in an organization — a key step in access reviews, onboarding to a new environment, and identifying stale or orphaned accounts.

---

## Skills Demonstrated

- Microsoft Graph PowerShell SDK
- Microsoft Entra ID (Azure AD)
- Identity auditing and user inventory
- Principle of least privilege (scoped API permissions)
- PowerShell scripting for IAM automation
- Access review preparation
---

**Screenshot 1 — Connecting to Microsoft Graph**

Note: Tenant ID has been redacted for security purposes.

Using Connect-MgGraph -Scopes "User.Read.All" to authenticate to the Entra ID tenant. The -Scopes parameter requests only the permissions needed for this task — User.Read.All is the appropriate scope for a read-only audit, following the principle of least privilege. Using User.ReadWrite.All in this context would be over-permissioned since no write operations are performed.

<img width="2884" height="1822" alt="1" src="https://github.com/user-attachments/assets/68ee65cb-17e6-4a6f-9c86-57d196a5ba38" />

**Screenshot 2 — Exporting User Inventory to CSV**

After authenticating to the tenant, I ran Get-MgUser -All piped into Select-Object DisplayName, UserPrincipalName and exported the results to C:\users_report.csv using Export-Csv -NoTypeInformation. Running Test-Path "C:\users_report.csv" returned True, confirming the file was successfully created and written to disk.

<img width="2880" height="1658" alt="2" src="https://github.com/user-attachments/assets/e01417b8-60b2-457f-9b03-ff86c5065963" />

**Screenshot 3 — Opening the CSV File**

I ran Invoke-Item "C:\users_report.csv" to open the exported file in the default application. This step confirms the file is accessible, properly formatted, and ready for review or handoff as part of an access audit.

<img width="2880" height="1656" alt="3" src="https://github.com/user-attachments/assets/8c55728c-5894-42d1-918a-4e71ea9265d6" />

**Screenshot 4 — Reviewing the User Inventory Output**

The exported CSV displays 20 users from the tenant, including named employee accounts, department test accounts (HR.Test, IT.Test, Finance.Test, Operations.Test), a Break Glass Admin account, and one B2B guest user identifiable by the #EXT# suffix in the UPN. Notably, one account named Contractors.Tets appears to be a typo — a data quality finding that would be flagged for remediation in a real access review.

<img width="2882" height="1654" alt="4" src="https://github.com/user-attachments/assets/a5854a85-a2b9-4339-b288-34942e9cdc41" />

# Conclusion

This lab demonstrates my ability to use Microsoft Graph PowerShell to programmatically audit user identities in Microsoft Entra ID. By scoping permissions to User.Read.All and exporting only the fields needed. User.ReadWrite.All was used here for lab flexibility, but the correct least-privilege scope for a read-only operation is User.Read.All — granting write permissions when only read is needed violates least privilege and unnecessarily expands the attack surface in a production environment.
