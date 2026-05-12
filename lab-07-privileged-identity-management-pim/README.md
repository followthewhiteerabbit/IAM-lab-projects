# Lab: Configuring Privileged Identity Management (PIM) in Microsoft Entra ID

![Microsoft Entra ID](https://img.shields.io/badge/Microsoft%20Entra%20ID-P2-blue?logo=microsoft)
![PIM](https://img.shields.io/badge/Feature-Privileged%20Identity%20Management-blueviolet)
![Zero Trust](https://img.shields.io/badge/Principle-Zero%20Trust-green)
![License](https://img.shields.io/badge/License-Entra%20ID%20P2-orange)

---

## Lab Overview

This lab demonstrates how to configure **Microsoft Entra Privileged Identity Management (PIM)** to enforce **Just-in-Time (JIT) access** for an HR employee using the **Security Reader** role. The goal is to eliminate standing admin access and follow the **Zero Trust principle of least privilege**.

Rather than granting permanent role assignments that sit dormant and create unnecessary attack surface, PIM ensures users must actively request time-bound access — with full audit logging, MFA enforcement, and required business justification at every activation.

---

## Tools Used

| Tool | Purpose |
|------|---------|
| **Microsoft Entra Admin Center** | Configure PIM, role assignments, and audit logs |
| **Microsoft Azure Portal** | Supporting portal for identity management |
| **Microsoft Authenticator** | MFA verification during PIM role activation |

---

## License Required

> **Microsoft Entra ID P2** — Required to access Privileged Identity Management features.

---

## Lab Walkthrough

### Screenshot 1 — PIM Overview

<img width="3024" height="1584" alt="1 blur" src="https://github.com/user-attachments/assets/e106eadb-39a7-493b-89f1-b1f52dd1a6cc" />


The **Privileged Identity Management (PIM) Quick Start** page inside the Microsoft Entra admin center. Shows the three core capabilities: **Manage access**, **Activate just in time**, and **Discover and monitor**.

PIM is a Microsoft Entra ID P2 feature that enforces Just-in-Time access to privileged roles — significantly reducing the attack surface if an account is compromised.

---

### Screenshot 2 — Microsoft Entra Roles

![Screenshot 2](screenshots/2.png)

The **PIM Microsoft Entra roles Quick Start** page for the Salient Cloud tenant. Shows the 4 core PIM functions: **Assign**, **Activate**, **Approve**, and **Audit**.

This is the control center for managing privileged access — ensuring no user holds standing admin access permanently, directly supporting the Zero Trust principle of least privilege.

---

### Screenshot 3 — My Roles / Eligible Assignments

![Screenshot 3](screenshots/3.png)

Before configuring PIM role assignments, I first assigned myself the **Privileged Role Administrator** role as an eligible assignment. This role grants the ability to manage PIM configurations while following least privilege — using a scoped role instead of Global Administrator.

---

### Screenshot 4 — Search Security Reader

![Screenshot 4](screenshots/4.png)

Inside **PIM → Microsoft Entra roles → Roles**, I searched for the **Security Reader** role to configure it for assignment.

Security Reader provides global read-only access across Microsoft Entra and Identity Protection — appropriate for HR personnel who need to review access reports without making changes.

---

### Screenshot 5 — Select Emma Rodriguez

![Screenshot 5](screenshots/5.png)

Inside **PIM → Add assignments**, I selected **Emma Rodriguez** (HR employee) as the member to assign the Security Reader role to.

Emma was chosen to simulate a real-world scenario where an HR team member requires read-only access to review user access reports for compliance purposes — without needing permanent standing access.

---

### Screenshot 6 — Role Assignment Configuration

![Screenshot 6](screenshots/6.png)

- **Role:** Security Reader
- **Member:** Emma Rodriguez
- **Scope:** Directory level (applies across the entire tenant)
- **Assignment type:** Eligible

By setting the assignment to **Eligible**, Emma must activate through PIM when access is needed rather than having permanent standing access.

---

### Screenshot 7 — Assignment Settings

![Screenshot 7](screenshots/7.png)

- **Assignment type:** Active
- **Start date:** 05/10/2026
- **Business justification:** *"HR personnel require security reader access to review user access reports and support compliance audits and offboarding processes."*

Justification is required to maintain a clear audit trail of why access was granted.

---

### Screenshot 14 — Assignment Tab Settings

![Screenshot 14](screenshots/14.png)

| Setting | Value |
|---------|-------|
| Allow permanent eligible assignment | Yes |
| Expire eligible assignments after | 1 Year |
| Expire active assignments after | 6 Months |
| Require justification on active assignment | Yes |

The annual review cadence and 6-month active expiration ensure access is regularly re-evaluated, while mandatory justification ensures all access is documented.

---

### Screenshot 15 — Notification Tab

![Screenshot 15](screenshots/15.png)

Notification settings ensure full visibility into role activity:

- Admin notified on eligible and active assignments
- Assignee notified when assigned
- Admin and requestor notified on activation

This supports governance and compliance by ensuring the security team is always aware of privileged role activity.

---

### Screenshot 16 — Authenticator MFA Setup

![Screenshot 16](screenshots/16.png)

Before Emma could activate her PIM role, **MFA registration was required**. Microsoft Authenticator was successfully added to Emma's account — confirming she can complete MFA verification during role activation as configured in the role settings.

---

### Screenshot 18 — Emma's Eligible Assignments

![Screenshot 18](screenshots/18.png)

Signed in as **Emma Rodriguez**, **PIM → My roles → Eligible assignments** shows the **Security Reader** role is available to activate for the Salient Cloud tenant.

No standing privileges exist — Emma must click **Activate** to request Just-in-Time access.

---

### Screenshot 19 — Activation Request + Justification

![Screenshot 19](screenshots/19.png)

Emma initiates role activation by clicking **Activate** on the Security Reader eligible assignment. A justification is required before activation can proceed:

> *"Reviewing user access reports for HR compliance audits."*

- **Duration:** 8 hours (the maximum configured in the role settings)

---

### Screenshot 21 — All Activation Stages Complete

![Screenshot 21](screenshots/21.png)

PIM processes the activation request through **3 stages** — all completed successfully:

| Stage | Status |
|-------|--------|
| Stage 1: Request processed | ✅ Complete |
| Stage 2: Activation validated | ✅ Complete |
| Stage 3: Activation completed | ✅ Complete |

Confirms the Just-in-Time activation workflow completed successfully for Emma Rodriguez.

---

### Screenshot 22 — Active Assignments Confirmed

![Screenshot 22](screenshots/22.png)

Back in the admin portal, **PIM → Assignments → Active assignments** confirms:

- **User:** Emma Rodriguez
- **Role:** Security Reader
- **State:** Activated
- **Start time:** 5/11/2026, 12:40:10 PM
- **End time:** 5/11/2026, 8:40:09 PM *(exactly 8 hours)*

Confirms time-bound JIT access is working correctly.

---

### Screenshot 23 — Audit History

![Screenshot 23](screenshots/23.png)

The **PIM Resource audit log** shows the complete activity trail for this lab:

- Role settings updated
- Eligible assignment added
- Activation requested and completed by Emma Rodriguez

All entries are logged with **timestamp**, **requestor**, **action type**, and **status** — critical for security investigations and compliance reporting.

---

## Conclusion

This lab demonstrated a complete end-to-end configuration of **Microsoft Entra Privileged Identity Management (PIM)** — from initial setup through to successful Just-in-Time role activation.

### What Was Accomplished

- Enabled and navigated the PIM Quick Start dashboard in Microsoft Entra admin center
- Assigned the **Privileged Role Administrator** role to myself as an eligible assignment (avoiding Global Admin)
- Configured the **Security Reader** role with an **Eligible assignment** for Emma Rodriguez (HR)
- Set scope to **Directory level** to apply access across the full tenant
- Enforced **MFA registration** (Microsoft Authenticator) as a prerequisite for activation
- Configured assignment settings: 1-year eligible expiry, 6-month active expiry, mandatory justification
- Set up **notifications** for admin and assignee on all assignment and activation events
- Successfully activated the Security Reader role as Emma Rodriguez with business justification
- Verified **time-bound access** (8-hour window) in the Active Assignments tab
- Reviewed the **audit log** confirming full traceability of all PIM actions

### Security Principles Applied

| Principle | Implementation |
|-----------|---------------|
| **Zero Trust / Least Privilege** | Emma has no standing admin access — access is granted only when needed and for a defined duration |
| **Just-in-Time (JIT) Access** | Eligible assignments require active activation with justification and MFA |
| **Time-Bound Access** | Active assignments expire after 8 hours; eligible assignments reviewed annually |
| **Auditability** | Full audit trail in PIM logs — requestor, timestamp, justification, and outcome recorded |
| **MFA Enforcement** | Microsoft Authenticator required before any PIM role can be activated |
| **Separation of Duties** | Used Privileged Role Administrator instead of Global Admin to manage PIM |

By implementing PIM, the Salient Cloud tenant significantly reduces its **privileged access attack surface** — ensuring that even if an account like Emma's is compromised, the attacker gains no persistent admin capabilities.

---

*Lab completed in Microsoft Entra Admin Center | Entra ID P2 | May 2026*
