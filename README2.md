# Require Compliant Device Policy (LAB)

# Lab Goal / Objective

This lab demonstrates how I enforced a Conditional Access policy in Microsoft Entra ID that blocks access to Office 365 from any device that isn’t Intune-managed and compliant. I used a dynamic group for the Operations department, applied device-based conditions across all platforms, and validated the policy by testing a real user sign-in, confirming that unmanaged devices are denied access. This shows my ability to design, implement, and troubleshoot Zero Trust access controls in a real environment.

# Skills Demonstrated

- Conditional Access

- Device compliance enforcement

- Intune integration

- Zero Trust device governance

- Real-world access restriction troubleshooting



<img width="3020" height="1606" alt="Screenshot 2025-12-07 at 2 43 13 PM something" src="https://github.com/user-attachments/assets/41cbafc5-7f37-41dc-8a25-21728ddde7ed" />

**STEP 1:**

In this screenshot, I am creating a Conditional Access policy scoped to users in the Operations dynamic group. This ensures that the policy is applied specifically to members of that department. I chose the Operations group because they regularly access key organizational resources, making it important to enforce device compliance and ensure they are signing in from secure, managed devices.

<img width="3024" height="1724" alt="Screenshot 2025-12-07 at 3 39 18 PM" src="https://github.com/user-attachments/assets/395b9068-7684-4be3-972f-1a90e1ba6e13" />

**STEP 2:**

In this screenshot, I’m selecting the specific cloud app that the policy will apply to—in this case, Office 365. By targeting Office 365 directly, I ensure that Operations users must be on a compliant, managed device before accessing any core productivity services. This keeps sensitive organizational data protected while still allowing the team to work normally, as long as they are using secure, compliant endpoints.

<img width="3024" height="1608" alt="Screenshot 2025-12-07 at 2 52 28 PM" src="https://github.com/user-attachments/assets/511e295b-dda0-4714-99a8-7c9b1bd16788" />

**STEP 3:**

In this screenshot, I’m configuring the device platform conditions for the policy. By selecting all major platforms—Windows, macOS, iOS, Android, Linux, and Windows Phone—I ensure that the Operations department is required to use compliant, managed devices no matter what type of device they sign in from. This prevents users from bypassing security controls by switching to an unmonitored or unsupported platform.


<img width="3024" height="1608" alt="Screenshot 2025-12-07 at 3 40 09 PM" src="https://github.com/user-attachments/assets/15f32062-f47f-4868-8b04-5f302c6d56e1" />

**STEP 4:**

Here, I set the access requirement to “Require device to be marked as compliant.” This makes sure Operations users can only sign in from devices that meet Intune’s security standards. If the device isn’t managed or doesn’t pass compliance checks, access is blocked—keeping company data protected.

<img width="3018" height="1604" alt="Screenshot 2025-12-07 at 4 06 12 PM" src="https://github.com/user-attachments/assets/c1c4d5c7-9aad-462a-a9f5-7d42fe615a8c" />

# Policy Testing

In this screenshot, I’m signing into one of the Operations users’ accounts to test the policy. Since the device isn’t compliant, the Conditional Access rule immediately kicks in and blocks the sign-in. This confirms the policy is working the way it should—only compliant, managed devices are allowed through

<img width="3024" height="1560" alt="Screenshot 2025-12-07 at 4 15 32 PM" src="https://github.com/user-attachments/assets/af95bb7f-58e7-40be-ae0c-b23a8433e0be" />

In this screenshot, we see the Conditional Access policy successfully blocking Ava Martinez (an Operations user) from signing in because her device is not compliant. The sign-in logs show error 530003, which indicates that access is denied due to the device not being managed by an approved MDM solution such as Intune. This confirms that the “Require device to be marked as compliant” control is working as expected.


# In Conclusion


This lab demonstrates how Conditional Access strengthens a Zero Trust security posture by allowing only Intune-enrolled, compliant devices to access cloud resources. It shows my ability to design, implement, validate, and troubleshoot real-world IAM policies in Microsoft Entra ID.








