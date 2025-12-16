# Require Compliant Device Policy 

# Lab Goal / Objective

This lab demonstrates how I enforced a Conditional Access policy in Microsoft Entra ID that blocks access to Office 365 from any device that isn’t Intune-managed and compliant. I used a dynamic group for the Operations department, applied device-based conditions across all platforms, and validated the policy by testing a real user sign-in, confirming that unmanaged devices are denied access. This shows my ability to design, implement, and troubleshoot Zero Trust access controls in a real environment.

---
# Skills Demonstrated

- Conditional Access

- Device compliance enforcement

- Intune integration

- Zero Trust device governance

- Real-world access restriction troubleshooting

---

<img width="3020" height="1606" alt="Untitled design" src="https://github.com/user-attachments/assets/57327fb8-6a31-4660-98a2-975dd512fbe2" />




**Screenshot 1 - Conditional Access Policy Creation (Operations Group Targeting)**

In this screenshot, I am creating a Conditional Access policy scoped to users in the Operations dynamic group. This ensures that the policy is applied specifically to members of that department. I chose the Operations group because they regularly access key organizational resources, making it important to enforce device compliance and ensure they are signing in from secure, managed devices.

<img width="3024" height="1724" alt="Untitled design-2" src="https://github.com/user-attachments/assets/5dcbaf4a-5347-481e-aea6-80b2fa7b8aff" />


**Screenshot 2 -Target Cloud Application: Office 365**

In this screenshot, I’m selecting the specific cloud app that the policy will apply to—in this case, Office 365. By targeting Office 365 directly, I ensure that Operations users must be on a compliant, managed device before accessing any core productivity services. This keeps sensitive organizational data protected while still allowing the team to work normally, as long as they are using secure, compliant endpoints.

<img width="3024" height="1608" alt="Untitled design-3" src="https://github.com/user-attachments/assets/3a9efb48-edaa-4fb0-9025-3df0359a52be" />


**Screenshot 3 - Device Platform Conditions (All Platforms Selected)**

In this screenshot, I’m configuring the device platform conditions for the policy. By selecting all major platforms—Windows, macOS, iOS, Android, Linux, and Windows Phone—I ensure that the Operations department is required to use compliant, managed devices no matter what type of device they sign in from. This prevents users from bypassing security controls by switching to an unmonitored or unsupported platform.

<img width="3024" height="1608" alt="Untitled design-4" src="https://github.com/user-attachments/assets/33f06e66-9eb3-4879-84e4-e2cf33707760" />



**Screenshot 4 – Device Compliance Requirement (Intune-Managed & Compliant Devices Only)**

Here, I set the access requirement to “Require device to be marked as compliant.” This makes sure Operations users can only sign in from devices that meet Intune’s security standards. If the device isn’t managed or doesn’t pass compliance checks, access is blocked—keeping company data protected.


<img width="3018" height="1604" alt="Untitled design-5" src="https://github.com/user-attachments/assets/3cd2ee05-e4c5-4a2d-ac25-63b154b83949" />


**Screenshot 5 - Sign-In Blocked Due to Non-Compliant Device (Policy Enforcement Test)**


In this screenshot, I’m signing into one of the Operations users’ accounts to test the policy. Since the device isn’t compliant, the Conditional Access rule immediately kicks in and blocks the sign-in. This confirms the policy is working the way it should—only compliant, managed devices are allowed through

<img width="3024" height="1560" alt="Untitled design-8" src="https://github.com/user-attachments/assets/c8780da6-3f8b-4c90-919c-608438560cc1" />


**Screenshot 6 – Sign-In Logs Showing Device Compliance Failure (Error 530003)**

In this screenshot, we see the Conditional Access policy successfully blocking Ava Martinez (an Operations user) from signing in because her device is not compliant. The sign-in logs show error 530003, which indicates that access is denied due to the device not being managed by an approved MDM solution such as Intune. This confirms that the “Require device to be marked as compliant” control is working as expected.


# Conclusion


This lab demonstrates how Conditional Access strengthens a Zero Trust security posture by allowing only Intune-enrolled, compliant devices to access cloud resources. It shows my ability to design, implement, validate, and troubleshoot real-world IAM policies in Microsoft Entra ID.








