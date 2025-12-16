## **Require Password Reset for High-Risk Users Using Conditional Access**

---
## Objective

The objective of this lab is to configure a Conditional Access policy in Microsoft Entra ID that automatically forces a password reset when a user is identified as high risk. Using Identity Protection risk signals, this policy demonstrates how organizations can rapidly remediate potentially compromised accounts, reduce account takeover risk, and enforce Zero Trust identity controls while validating the policy safely in report-only mode.

---
## Skills Used

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



**Screenshot 2 – Target Resources Set to All Resources**

In this screenshot, the policy is configured to apply to All resources (formerly “All cloud apps”). This is required because the Require password change control can only be enforced when all resources are targeted. Applying the policy tenant-wide ensures that a compromised user cannot bypass remediation by accessing a different application.



<img width="2276" height="1610" alt="Screenshot 2025-12-14 at 11 32 43 PM" src="https://github.com/user-attachments/assets/c0f8f11e-14c1-4ae8-8972-70d6bbc37eb4" />



**Screenshot 3 – User Scope and Exclusions (Break-Glass Protection)**

This screenshot shows All users included, with specific exclusions configured. The break-glass administrator account and a test user are excluded to prevent administrative lockout and allow safe testing. This reflects real-world operational best practices when deploying high-impact Conditional Access policies.


<img width="2294" height="1608" alt="Untitled design (1)" src="https://github.com/user-attachments/assets/f4e99cb0-aaf1-45d3-8db3-1fa7ccc0dbaf" />

**Screenshot 4 – Grant Controls Configuration (Password Change Enforcement)**

Here, the Grant control is configured with Require password change. This control forces users identified as high risk to reset their password before regaining access. Microsoft Entra automatically lowers the user risk level once the password reset is completed, allowing access to resume securely.

<img width="3024" height="1608" alt="Untitled design (3)" src="https://github.com/user-attachments/assets/e2e751f3-c324-4204-b7f5-5366d79bb928" />

**Screenshot 5 – Grant Controls Configured with Password Reset (Policy in Report-Only Mode)**

This screenshot shows the final Conditional Access configuration where the Grant control is set to “Require password change” and the policy is enabled in Report-only mode. This confirms that users identified as high risk would be forced to reset their password, while report-only mode allows administrators to safely observe policy behavior and validate detections before enforcing the control in production.


<img width="3024" height="1610" alt="Untitled design" src="https://github.com/user-attachments/assets/683db89a-2e90-4d3e-a51d-4f5c4a60fa2a" />


## **Conclusion**

----
This Conditional Access policy is necessary to protect against account takeover scenarios where user credentials are suspected to be compromised. By automatically requiring a password reset when high user risk is detected, the organization can rapidly contain threats without relying on manual intervention. This approach reduces attacker dwell time, prevents lateral movement, and aligns with Zero Trust principles by continuously validating identity trust. Implementing this policy demonstrates a proactive, automated identity security control commonly used in enterprise environments.


