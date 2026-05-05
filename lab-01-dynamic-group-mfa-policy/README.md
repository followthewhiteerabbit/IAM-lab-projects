# Creating a Dynamic Group for the IT Department and Applying an MFA Policy 
---
 
# Objective


In this lab, I created a dynamic group for the IT department and applied a Multi-factor Authentication (MFA) Conditional Access policy to it. IT staff often have elevated access, so requiring MFA adds a critical layer of security and supports a Zero Trust approach by making sure only verified users can access sensitive resources.
---
# Skills demonstrated

- Dynamic groups

- Conditional Access

- MFA enforcement

- Break-glass best practices

- Zero Trust concepts

---
<img width="3024" height="1604" alt="Untitled design" src="https://github.com/user-attachments/assets/0d33dccd-24e1-4f11-9d32-00dabd402cfd" />




**Screenshot 1 - IT Department Dynamic Group Membership**

We can see the dynamic group members in the IT department here, which are Daniel Carter and Liam Thompson.


<img width="1512" height="764" alt="1" src="https://github.com/user-attachments/assets/c0f651e1-fc24-4849-b655-5368e74ca757" />




**Screen Shot 2 - Conditional Access Policy Creation (Require MFA for IT Group)**

In this step, I created a Conditional Access policy that requires Multi-factor Authentication (MFA) for the IT department. I targeted the IT dynamic group so only IT staff are required to authenticate with MFA, ensuring stronger protection for accounts with elevated access.

<img width="3024" height="1608" alt="Untitled design-2" src="https://github.com/user-attachments/assets/c9ced4bc-a382-4e9e-8b64-e24f594eb807" />


**Screenshot 3 - User Exclusions (Break-Glass & Admin Accounts)**

In this step, I excluded my break-glass admin account and my own admin account from the MFA policy. This is a best practice so administrators don’t get locked out if MFA fails or if there’s an outage. Only the IT dynamic group is required to follow the MFA rule, while emergency and admin accounts remain accessible.

<img width="3024" height="1610" alt="Untitled design-3" src="https://github.com/user-attachments/assets/a244655f-f75f-4e03-8b3c-464ab35f8c61" />


**Screenshot 4 - Target Resources Set to All Cloud Apps**

In this step, I set the policy to apply to all cloud apps/resources. This means every sign-in attempt from an IT department user will require MFA, no matter which Microsoft service they access. I did this to make sure the MFA requirement is enforced consistently across the entire environment, not just a single app.

<img width="3024" height="1610" alt="Untitled design-4" src="https://github.com/user-attachments/assets/663cedf1-14e2-495f-a36b-e1135b63728f" />


**Screenshot 5 - Grant Controls: Require Multi-Factor Authentication**

In this step, I configured the Grant controls for the Conditional Access policy. I selected “Grant access” and enabled “Require multi-factor authentication”. This enforces that any IT department user must complete MFA before being allowed into any cloud resource. This is the final action that activates the security requirement we designed for this policy.

 <img width="3024" height="1606" alt="Untitled design-5" src="https://github.com/user-attachments/assets/06ed5d80-aae2-42b4-ad7d-917e60fc81f0" />

**Screenshot 6 - MFA Registration Prompt Triggered by Conditional Access**


In this screenshot, Daniel from the IT department attempts to sign in and is immediately prompted to set up an additional verification method. This happens because the MFA Conditional Access policy we applied to the IT dynamic group is being enforced. Since Daniel is a member of that group, the system requires him to configure MFA before he’s allowed access.

<img width="3024" height="1610" alt="Untitled design-6" src="https://github.com/user-attachments/assets/ba6f8fba-14fe-4560-992f-ad2c69e72e35" />

**Screenshot 7 - Microsoft Authenticator App Required for MFA Setup**


In this screenshot, Daniel is required to install the Microsoft Authenticator app because the MFA policy is enforcing setup. Since he hasn’t registered MFA yet, the system guides him to complete the setup before allowing access.

# Conclusion 

This lab demonstrates my ability to design and implement secure identity controls in Microsoft Entra ID. By using a dynamic group, applying MFA through Conditional Access, and following best practices like break-glass exclusions, I showed how to strengthen access security for high-privilege users. This is a fundamental skill in IAM and a core part of building a Zero Trust environment.
