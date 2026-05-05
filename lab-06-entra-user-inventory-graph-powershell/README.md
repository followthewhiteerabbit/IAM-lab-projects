[← Back to Portfolio](../README.md)

# Automating Entra ID User Inventory with Microsoft Graph PowerShell

---

# Lab Overview

In any organization, knowing exactly who has access to your environment is the foundation of identity security. Over time, tenants accumulate stale accounts, misconfigured identities, orphaned guest users, and test accounts that were never cleaned up — all of which represent security risk. This lab simulates a real-world identity audit using Microsoft Graph PowerShell to programmatically export a full user inventory from Microsoft Entra ID. This is typically one of the first tasks an IAM engineer performs when onboarding to a new environment or preparing for an access review.

---

# Objective

In this lab, I used Microsoft Graph PowerShell to connect to a Microsoft Entra ID tenant and export a complete user inventory to a CSV file. The goal was to demonstrate how to programmatically audit identities in an organization — a key step in access reviews, onboarding to a new environment, and identifying stale or orphaned accounts.

---

# Skills Demonstrated

- Microsoft Graph PowerShell
- - Microsoft Entra ID (Azure AD)
  - - Identity auditing and user inventory
    - - Principle of least privilege (scoped API permissions)
      - - PowerShell scripting for IAM automation
        - - Access review preparation
         
          - ---

          **Screenshot 1 — Connecting to Microsoft Graph**

          Note: Tenant ID has been redacted for security purposes.

          Using Connect-MgGraph -Scopes "User.Read.All" to authenticate to the Entra ID tenant. The -Scopes parameter requests only the permissions needed for this task — User.Read.All is the appropriate scope for a read-only audit, following the principle of least privilege. Using User.ReadWrite.All in this context would be over-permissioned since no write operations are performed.

          <img width="2884" height="1822" alt="1" src="https://github.com/user-attachments/assets/68ee65cb-17e6-4a6f-9c86-57d196a5ba38" />

          **Screenshot 2 — Exporting the User Inventory to CSV**

          Get-MgUser -All retrieves every user in the tenant and pipes the results into Select-Object to limit output to DisplayName and UserPrincipalName only — avoiding unnecessary data collection. The -NoTypeInformation flag keeps the CSV clean by removing the PowerShell type header. Test-Path returning True confirms the file was successfully written to C:\users_report.csv.

          <img width="2880" height="1658" alt="2" src="https://github.com/user-attachments/assets/e01417b8-60b2-457f-9b03-ff86c5065963" />

          <img width="2880" height="1656" alt="3" src="https://github.com/user-attachments/assets/8c55728c-5894-42d1-918a-4e71ea9265d6" />

          <img width="2882" height="1654" alt="4" src="https://github.com/user-attachments/assets/a5854a85-a2b9-4339-b288-34942e9cdc41" />

          # Conclusion

          This lab demonstrates my ability to use Microsoft Graph PowerShell to programmatically audit user identities in Microsoft Entra ID. By scoping permissions to User.Read.All and exporting only the fields needed, I applied the principle of least privilege while producing a clean, usable inventory. This is a foundational skill in IAM engineering and a practical first step in any access review or tenant onboarding process.
