

# Require MFA Based on Sign-In Risk Using Conditional Access

## Objective

In this lab, I configured a Conditional Access policy in Microsoft Entra ID to require multifactor authentication (MFA) when a sign-in is detected as medium or high risk. This approach uses Microsoft’s real-time risk signals to dynamically enforce stronger authentication only when suspicious activity is identified.

---

## Skills Demonstrated

* Microsoft Entra ID (Azure AD)
* Conditional Access policy configuration
* Identity Protection (Sign-in risk)
* MFA enforcement
* Risk-based access control
* Zero Trust security principles

---

## Configuration Steps (Screenshot Breakdown)

### **Screenshot 1 – Policy Creation & User Scope**

Created a new Conditional Access policy named CA-SignInRisk-RequireMFA and configured it to apply to all users as the baseline assignment scope.


<img width="2286" height="1606" alt="1" src="https://github.com/user-attachments/assets/4ae88502-7c8f-4841-8b22-465c7bab4e75" />


### **Screenshot 2 – User Exclusions (Break-Glass & Test Account)**

Configured user exclusions by excluding the break-glass admin account and a test user account. This ensures emergency administrative access is preserved and allows safe validation of the policy without risking tenant lockout.

<img width="2284" height="1606" alt="2" src="https://github.com/user-attachments/assets/e17a7bb7-6cb0-41ab-b16d-d816042fa254" />


### **Screenshot 3 – Target Resources**

Set Target resources to All resources (formerly “All cloud apps”), ensuring the policy applies tenant-wide and protects access to all applications and services.


<img width="2284" height="1612" alt="3" src="https://github.com/user-attachments/assets/d969c9b8-eb80-431f-9a42-aed41adda045" />


### **Screenshot 4 – Sign-In Risk Condition**

Enabled the **Sign-in risk** condition and selected **Medium** and **High** risk levels. This ensures the policy is triggered only when Microsoft detects suspicious sign-in behavior, such as unfamiliar locations or anomalous activity.

<img width="3024" height="1604" alt="4" src="https://github.com/user-attachments/assets/5b7cf7c6-c111-462c-ab12-139fa5ff81e9" />


### **Screenshot 5 – Grant Controls**

Configured **Grant access** with **Require multifactor authentication**, enforcing MFA when the defined risk conditions are met. The policy was left in **Report-only** mode for safe validation before full enforcement.

<img width="3024" height="1614" alt="5" src="https://github.com/user-attachments/assets/7695bc00-974e-437f-806b-279824e1f4a8" />


## Conclusion

This configuration is necessary to protect user accounts from compromised credentials by responding dynamically to risky sign-in behavior. By requiring MFA only when medium or high risk is detected, the organization reduces the likelihood of account takeover while maintaining a balance between security and user experience. This aligns with Zero Trust principles and represents a real-world identity protection control used in enterprise environments.

