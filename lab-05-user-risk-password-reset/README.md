## **Require Password Reset for High-Risk Users Using Conditional Access**

---
## Objective

The objective of this lab is to configure a Conditional Access policy in Microsoft Entra ID that automatically forces a password reset when a user is identified as high risk. Using Identity Protection risk signals, this policy demonstrates how organizations can rapidly remediate potentially compromised accounts, reduce account takeover risk, and enforce Zero Trust identity controls while validating the policy safely in report-only mode.

---
## Skills Demonstrated

- Microsoft Entra ID (Azure AD)

- Conditional Access policy design

- Identity Protection (User Risk detection)

- Risk-based access control

- Automated password reset enforcement

- Break-glass account protection

- Report-only policy validation

- Incident response and account remediation

- Zero Trust identity security principles

- Enterprise IAM best practices


---


**Screenshot 1 – Conditional Access Policy Creation (User Risk-Based Password Reset)**

This screenshot shows the creation of a Conditional Access policy named CA-UserRisk-RequirePasswordReset. The policy is designed to respond to elevated user risk, which Microsoft identifies when an account is likely compromised. The policy is scoped broadly to ensure protection across the tenant while remaining configurable through exclusions.




<img width="2290" height="1610" alt="Screenshot 2025-12-14 at 11 32 14 PM" src="https://github.com/user-attachments/assets/88fa44eb-8eb0-4e04-802c-afc6dc2e6b5d" />


**Screenshot 2 – User Scope and Exclusions (Break-Glass Protection)**

This screenshot shows All users included, with specific exclusions configured. The break-glass administrator account and a test user are excluded to prevent administrative lockout and allow safe testing. This reflects real-world operational best practices when deploying high-impact Conditional Access policies.

<img width="2294" height="1608" alt="Untitled design (1)" src="https://github.com/user-attachments/assets/f4e99cb0-aaf1-45d3-8db3-1fa7ccc0dbaf" />


**Screenshot 3 – Target Resources Set to All Resources**

In this screenshot, the policy is configured to apply to All resources (formerly “All cloud apps”). This is required because the Require password change control can only be enforced when all resources are targeted. Applying the policy tenant-wide ensures that a compromised user cannot bypass remediation by accessing a different application.



<img width="2276" height="1610" alt="Screenshot 2025-12-14 at 11 32 43 PM" src="https://github.com/user-attachments/assets/c0f8f11e-14c1-4ae8-8972-70d6bbc37eb4" />


**Screenshot 4 - User risk configuration**

This screenshot shows the User risk condition set to Medium and High, ensuring the policy only triggers when Microsoft Entra detects elevated risk.

<img width="3024" height="1606" alt="Untitled design" src="https://github.com/user-attachments/assets/8e54e8c4-6994-41b2-8227-6dd2862a4f4e" />


**Screenshot 5 – Grant Access with MFA Grant Controls Selection (Password Reset Remediation)**

MFA is shown here because Microsoft Entra requires strong authentication before allowing a password reset. When a user is flagged as high risk, MFA verifies the user’s identity first. After successful verification, the policy then forces a password change to remediate the risk.


<img width="3024" height="1608" alt="Untitled design (3)" src="https://github.com/user-attachments/assets/e2e751f3-c324-4204-b7f5-5366d79bb928" />

**Screenshot 6 – Force Password Reset to Remediate User Risk**

This screenshot shows the Require password change control enabled. After MFA verification, the user is forced to reset their password, which remediates the risk by invalidating potentially compromised credentials before access is fully restored.


<img width="3024" height="1610" alt="Untitled design" src="https://github.com/user-attachments/assets/683db89a-2e90-4d3e-a51d-4f5c4a60fa2a" />


## **Conclusion**

----
This Conditional Access policy is necessary to protect against account takeover scenarios where user credentials are suspected to be compromised. By automatically requiring a password reset when high user risk is detected, the organization can rapidly contain threats without relying on manual intervention. This approach reduces attacker dwell time, prevents lateral movement, and aligns with Zero Trust principles by continuously validating identity trust. Implementing this policy demonstrates a proactive, automated identity security control commonly used in enterprise environments.


