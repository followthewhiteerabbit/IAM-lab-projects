# Block Legacy Authentication Using Conditional Access 

## Overview

In this lab, I configured a Conditional Access policy in Microsoft Entra ID to block legacy authentication methods. Legacy authentication does not support modern security controls such as MFA, making it a common attack vector for credential-based attacks like password spray and brute force attempts.

This policy helps strengthen an organization’s security posture by ensuring all sign-ins use modern authentication protocols that support MFA and Conditional Access enforcement.


## Skills Demonstrated

* Microsoft Entra ID (Azure AD)
* Conditional Access policy configuration
* Legacy authentication risk mitigation
* Identity and access management (IAM)
* Security posture hardening
* Zero Trust principles



**Screenshot 1 – Conditional Access Policy Creation (Operations Group Targeting)**


- Created a Conditional Access policy (“CA-Require-Block Legacy Auth”) to explicitly target and block legacy authentication sign-ins.
  
<img width="1301" height="806" alt="1" src="https://github.com/user-attachments/assets/2d1589fa-1aa9-481f-8d63-db20e01efc52" />


**Screenshot 2 – User Scope & Exclusions (Break-Glass Protection)**

- Configured user scope by including all users while excluding specific accounts (such as break-glass or emergency accounts) to prevent administrative lockout during enforcement.


<img width="2612" height="1612" alt="Untitled design" src="https://github.com/user-attachments/assets/4e3312d8-f82c-4c5f-8761-2f87f5c68144" />


**Screenshot 3 – Target Resources (All Cloud Apps)**


- Set target resources to “All cloud apps”, ensuring legacy authentication is blocked across the entire tenant rather than limited to a single application.

<img width="1308" height="805" alt="3" src="https://github.com/user-attachments/assets/07fb04a2-e607-425f-99c6-11ef5c04979c" />


**Screenshot 4 – Client App Condition (Legacy Authentication Clients)**

- Configured client app conditions to specifically include legacy authentication clients (such as Exchange ActiveSync and other legacy protocols), targeting only non-modern sign-in methods.

<img width="3024" height="1612" alt="4" src="https://github.com/user-attachments/assets/654a348a-c0d8-433a-bd18-356302097c07" />

**Screenshot 5 – Access Controls Configured to Block Legacy Authentication**


- Applied access controls to block access when legacy authentication is detected and enabled the policy, enforcing modern authentication and reducing exposure to credential-based attacks.

<img width="3024" height="1604" alt="5" src="https://github.com/user-attachments/assets/828edef7-0faa-49cf-b671-32b478dec0d8" />

## Conclusion

This configuration was necessary to remove legacy authentication, which cannot enforce MFA and is frequently exploited in credential-based attacks. By blocking legacy sign-ins with Conditional Access, the organization reduces its attack surface and strengthens its overall identity security posture.
