# Creating a Dynamic Group for the IT Department and Applying an MFA Policy (Lab 1)

In this lab, I created a dynamic group for the IT department and applied a Multi-factor Authentication (MFA) Conditional Access policy to it. IT staff often have elevated access, so requiring MFA adds a critical layer of security and supports a Zero Trust approach by making sure only verified users can access sensitive resources.

# Skills demonstrated

. Dynamic groups

. Conditional Access

. MFA enforcement

. Break-glass best practices

. Zero Trust concepts



<img width="1512" height="802" alt="0 1" src="https://github.com/user-attachments/assets/45819fd2-19d7-4ced-a591-e31d361bd1c4" />

STEP 1:
We can see the dynamic group members in the IT department here, which are Daniel Carter and Liam Thompson.





<img width="1512" height="805" alt="Screenshot 2025-12-11 at 9 43 06 PM" src="https://github.com/user-attachments/assets/fdc39d85-fe95-4bf5-a17f-0a0856bd52b0" />
STEP 2: 

In this step, I created a Conditional Access policy that requires Multi-factor Authentication (MFA) for the IT department. I targeted the IT dynamic group so only IT staff are required to authenticate with MFA, ensuring stronger protection for accounts with elevated access.

<img width="1512" height="804" alt="1" src="https://github.com/user-attachments/assets/66d4989a-edb1-4799-8cd7-da1f819e992e" />

STEP 3:

In this step, I excluded my break-glass admin account and my own admin account from the MFA policy. This is a best practice so administrators don’t get locked out if MFA fails or if there’s an outage. Only the IT dynamic group is required to follow the MFA rule, while emergency and admin accounts remain accessible.

<img width="1512" height="805" alt="3" src="https://github.com/user-attachments/assets/5e85e003-6c5f-458b-bde4-f263f7f69031" />

STEP 4: 

In this step, I set the policy to apply to all cloud apps/resources. This means every sign-in attempt from an IT department user will require MFA, no matter which Microsoft service they access. I did this to make sure the MFA requirement is enforced consistently across the entire environment, not just a single app.

<img width="1512" height="805" alt="4" src="https://github.com/user-attachments/assets/35ac73d1-7627-4c93-94fd-db6f9b414b9e" />

STEP 5:

In this step, I configured the Grant controls for the Conditional Access policy. I selected “Grant access” and enabled “Require multi-factor authentication”. This enforces that any IT department user must complete MFA before being allowed into any cloud resource. This is the final action that activates the security requirement we designed for this policy.

<img width="1512" height="803" alt="we can see daniel from the IT department login portal was triggered by the MFA conditional access rule we created for his dynamic group  (1)" src="https://github.com/user-attachments/assets/6bb6169d-2bea-49d1-8dc1-e08c4166690d" />

In this screenshot, Daniel from the IT department attempts to sign in and is immediately prompted to set up an additional verification method. This happens because the MFA Conditional Access policy we applied to the IT dynamic group is being enforced. Since Daniel is a member of that group, the system requires him to configure MFA before he’s allowed access.


<img width="1512" height="805" alt="Screenshot 2025-12-05 at 9 18 34 PM (1)" src="https://github.com/user-attachments/assets/6bd8814d-f768-496a-880b-9108b7bbbd30" />

In this screenshot, Daniel is required to install the Microsoft Authenticator app because the MFA policy is enforcing setup. Since he hasn’t registered MFA yet, the system guides him to complete the setup before allowing access.

# In conclusion 

This lab demonstrates my ability to design and implement secure identity controls in Microsoft Entra ID. By using a dynamic group, applying MFA through Conditional Access, and following best practices like break-glass exclusions, I showed how to strengthen access security for high-privilege users. This is a fundamental skill in IAM and a core part of building a Zero Trust environment.
