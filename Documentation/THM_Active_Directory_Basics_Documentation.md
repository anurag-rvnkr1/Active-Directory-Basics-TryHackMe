# 🛡️ Active Directory Basics — TryHackMe Lab Documentation

> **Platform:** TryHackMe  
> **Room:** Active Directory Basics  
> **Category:** Windows Active Directory Fundamentals  
> **Focus Area:** Identity & Access Management (IAM), Windows Domain Administration, Group Policy, Kerberos Authentication

---

## 📖 Executive Summary

This repository documents my hands-on completion of the **Active Directory Basics** room on **TryHackMe**, where I explored the fundamentals of Microsoft Active Directory and Windows Domain administration in a simulated enterprise environment.

The lab introduced core Active Directory concepts including Domain Controllers, Organizational Units (OUs), Users, Groups, Machine Accounts, Group Policy Objects (GPOs), Kerberos authentication, and Trust Relationships. Throughout the exercise, I performed administrative tasks commonly carried out by Windows System Administrators and Blue Team professionals.

> **Educational Notice**
>
> This documentation has been rewritten in original technical language for learning and portfolio purposes. All flags, passwords, credentials, and challenge answers have been removed or replaced with **`[REDACTED]`**.

---

# 🎯 Learning Objectives

After completing this lab, I gained practical understanding of:

- Windows Domain architecture and centralized authentication.
- Active Directory Domain Services (AD DS).
- Managing users, computers, and security groups.
- Creating and organizing Organizational Units (OUs).
- Delegating administrative privileges securely.
- Applying Group Policy Objects (GPOs).
- Understanding SYSVOL and policy distribution.
- Kerberos and NetNTLM authentication mechanisms.
- Trees, Forests, and Trust Relationships within Active Directory.

---

# 🧪 Lab Environment

| Component | Details |
|-----------|---------|
| **Platform** | TryHackMe |
| **Room** | Active Directory Basics |
| **Operating System** | Windows Server (Domain Controller) |
| **Environment Type** | Enterprise Windows Domain |
| **Access Method** | Remote Desktop Protocol (RDP) |
| **Primary Tools** | Active Directory Users and Computers (ADUC), Windows PowerShell |
| **Authentication Protocols** | Kerberos, NetNTLM |
| **Objective** | Learn Windows Domain Administration Fundamentals |

---

# 🏗️ Active Directory Architecture Overview

Active Directory (AD) is Microsoft's centralized directory service used to manage users, computers, groups, and network resources across an enterprise Windows environment.

Instead of storing credentials on every individual computer, Active Directory stores identities in a centralized database managed by one or more **Domain Controllers (DCs)**.

### Core Active Directory Components

| Component | Purpose |
|-----------|---------|
| **Domain Controller** | Authenticates users and computers. |
| **Users** | Represents people or service accounts within the domain. |
| **Groups** | Simplifies permission and access management. |
| **Machine Accounts** | Represents computers joined to the domain. |
| **Organizational Units** | Organizes users and computers logically for administration. |
| **Group Policy Objects** | Applies centralized security and configuration policies. |
| **SYSVOL** | Shares and distributes Group Policy Objects across the domain. |

---

# 📋 Task Summary

| Task | Topic | Practical Focus |
|------|-------|-----------------|
| **Task 2** | Windows Domains | Understanding Active Directory and Domain Controllers |
| **Task 3** | Active Directory Objects | Users, Groups, Computers, Organizational Units |
| **Task 4** | User Administration | Managing users and delegated permissions |
| **Task 5** | Computer Administration | Organizing workstation computer objects |
| **Task 6** | Group Policy Objects | Understanding GPO deployment and SYSVOL |
| **Task 7** | Authentication | Kerberos vs NetNTLM |
| **Task 8** | Active Directory Structure | Trees, Forests, and Trust Relationships |

---

# 🖥️ Task 2 — Windows Domains & Active Directory

## Objective

Understand how Windows Domains centralize authentication and resource management through Active Directory.

### What I Learned

A Windows Domain provides centralized identity management by storing authentication credentials inside Active Directory instead of individual computers.

The **Domain Controller (DC)** acts as the central authority responsible for:

- Authenticating users.
- Authenticating computers.
- Managing permissions.
- Enforcing security policies.
- Hosting Active Directory Domain Services (AD DS).

### Key Concepts Learned

| Concept | Description |
|---------|-------------|
| **Windows Domain** | Collection of users, computers, and resources managed centrally. |
| **Active Directory** | Central repository for domain identities and policies. |
| **Domain Controller** | Windows Server running Active Directory Domain Services. |

### Administrative Understanding

- Authentication becomes centralized.
- Users can log into any domain-joined machine.
- Security policies are managed centrally instead of per device.

---

## 📷 Screenshot Placeholder

**Figure 2.1 — Windows Domain Environment**

> Insert screenshot showing the Windows Server desktop or Domain Controller environment.

---

# 👥 Task 3 — Exploring Active Directory Objects

## Objective

Understand the primary objects stored inside Active Directory.

### Active Directory Objects Explored

#### Users

User objects represent employee or service identities inside the domain.

Typical user information includes:

- Username
- Password
- Department
- Email
- Group Membership
- Security Identifier (SID)

#### Groups

Groups simplify permission management.

Common security groups include:

- Domain Admins
- Server Operators
- Backup Operators
- Account Operators

#### Machine Accounts

Every computer joined to the domain automatically receives a machine account.

Example naming convention:

```text
COMPUTERNAME$
```

Example:

```text
TOM-PC$
```

#### Organizational Units (OUs)

Organizational Units logically organize users and computers.

Benefits include:

- Department separation.
- Policy inheritance.
- Administrative delegation.
- Easier management.

### Administrative Activity Performed

- Opened **Active Directory Users and Computers**.
- Navigated the Active Directory hierarchy.
- Viewed Users, Groups, Computers, and Organizational Units.

---

## 📷 Screenshot Placeholders

**Figure 3.1 — Active Directory Users and Computers Console**

> Insert screenshot showing the ADUC management console.

**Figure 3.2 — Organizational Unit Structure**

> Insert screenshot displaying the Organizational Unit hierarchy.

**Figure 3.3 — Domain Users Container**

> Insert screenshot showing available users inside Active Directory.

---

# 👤 Task 4 — Managing Users in Active Directory

## Objective

Manage user accounts using delegated administrative privileges.

### Administrative Workflow

The exercise simulated a helpdesk or administrator scenario where user account management was required.

### Steps Performed

1. Connected to the Domain Controller through Remote Desktop.
2. Opened **Active Directory Users and Computers**.
3. Navigated to the appropriate Organizational Unit.
4. Located the target user account.
5. Reset the user's password using delegated privileges.
6. Verified successful authentication using the updated account.

### PowerShell Administration

A PowerShell command was used to perform password administration.

```powershell
Set-ADAccountPassword -Identity <username> -Reset
```

### Security Concept Learned

**Delegation** allows administrators to grant limited administrative privileges without assigning full Domain Administrator permissions.

This follows the **Principle of Least Privilege (PoLP)**.

### Verification

User authentication was verified successfully after updating the account credentials.

**Flag:** `[REDACTED]`

---

## 📷 Screenshot Placeholders

**Figure 4.1 — Active Directory User Account Management**

> Insert screenshot showing the selected user inside ADUC.

**Figure 4.2 — Password Reset Using PowerShell**

> Insert screenshot showing the PowerShell password reset command.

**Figure 4.3 — Successful User Login Verification**

> Insert screenshot showing successful login into the user profile.

---

# 💻 Task 5 — Managing Computers in Active Directory

## Objective

Organize computer objects using Organizational Units.

### Why Organizational Units Matter

Separating workstations and servers allows different security policies to be applied.

### Administrative Tasks Performed

- Created a new **Workstations** Organizational Unit.
- Moved workstation computer objects into the OU.
- Left servers in separate administrative containers.

### Benefits of Separate OUs

| Workstations OU | Servers OU |
|-----------------|------------|
| User security policies | Server security policies |
| Desktop restrictions | Server configuration policies |
| USB policies | Firewall and service policies |
| Endpoint management | Infrastructure management |

### Administrative Outcome

A dedicated Organizational Unit structure improves scalability and policy management.

---

## 📷 Screenshot Placeholders

**Figure 5.1 — Creating the Workstations Organizational Unit**

> Insert screenshot showing the creation of the Workstations OU.

**Figure 5.2 — Moving Computer Objects into the OU**

> Insert screenshot showing workstation computers moved into the new OU.

---

# 📑 Task 6 — Group Policy Objects (GPOs)

## Objective

Understand how Group Policy Objects are applied inside Active Directory.

### What is a Group Policy Object?

A Group Policy Object (GPO) is a collection of Windows configuration settings applied to users or computers within an Active Directory domain.

### GPO Targets

- User Policies
- Computer Policies

### Examples of Policies

| User Policies | Computer Policies |
|---------------|-------------------|
| Password settings | Windows Firewall |
| Desktop restrictions | BitLocker |
| Login scripts | Windows Update |
| Control Panel restrictions | Defender Configuration |

### SYSVOL

Group Policy Objects are distributed using the **SYSVOL** shared folder hosted on Domain Controllers.

Default location:

```text
C:\Windows\SYSVOL\sysvol\
```

### What I Learned

- GPOs are linked to Organizational Units.
- Policies are automatically synchronized to domain-joined machines through SYSVOL.
- Users receive updated policies during Group Policy refresh cycles.

---

## 📷 Screenshot Placeholders

**Figure 6.1 — Group Policy Management Console**

> Insert screenshot showing the Group Policy Management Console.

**Figure 6.2 — SYSVOL Directory**

> Insert screenshot showing the SYSVOL folder structure.

---

# 🔐 Task 7 — Authentication in Active Directory

## Objective

Understand how Windows authenticates users inside a domain.

### Kerberos Authentication

Kerberos is the default authentication protocol in modern Windows Domains.

Authentication workflow includes:

1. User login request.
2. Authentication Service verification.
3. Ticket Granting Ticket (TGT) issuance.
4. Ticket Granting Service (TGS) request.
5. Service ticket issuance.
6. Access to requested resources.

### NetNTLM Authentication

NetNTLM is the legacy Windows authentication protocol retained for compatibility.

Instead of transmitting passwords, NetNTLM uses a challenge-response mechanism.

### Kerberos vs NetNTLM

| Kerberos | NetNTLM |
|----------|----------|
| Ticket-based authentication | Challenge-response authentication |
| Mutual authentication | Legacy compatibility |
| Preferred protocol | Backup compatibility protocol |
| More secure | Less secure than Kerberos |

### Key Learning

- Modern Windows Domains prefer Kerberos.
- Passwords are never transmitted over the network in plaintext.

---

## 📷 Screenshot Placeholder

**Figure 7.1 — Windows Authentication Concepts**

> Insert screenshot related to Kerberos authentication within the lab environment.

---

# 🌳 Task 8 — Trees, Forests, and Trust Relationships

## Objective

Understand how multiple domains communicate within Active Directory.

### Tree

A Tree is a collection of domains sharing a common namespace.

Example:

```text
company.local
 ├── sales.company.local
 ├── hr.company.local
 └── it.company.local
```

### Forest

A Forest combines multiple trees into one Active Directory environment.

### Trust Relationships

Trusts allow users from one domain to access resources in another domain.

Types include:

- One-Way Trust
- Two-Way Trust
- Transitive Trust
- Non-Transitive Trust

### Administrative Importance

Trust relationships enable secure resource sharing between domains while maintaining separate administrative boundaries.

---

## 📷 Screenshot Placeholder

**Figure 8.1 — Active Directory Tree and Forest Structure**

> Insert screenshot or diagram showing Tree and Forest relationships.

---

# 🛠️ PowerShell Commands Practiced

| Command | Purpose |
|---------|---------|
| `Set-ADAccountPassword` | Reset a user's password. |
| `Get-ADUser` | Retrieve user account information. |
| `Unlock-ADAccount` | Unlock a locked domain account. |
| `New-ADOrganizationalUnit` | Create a new Organizational Unit. |

> **Note:** Passwords and user credentials used during the lab have been intentionally removed.

---

# 🔒 Security Concepts Learned

## Least Privilege Principle

Grant users only the permissions necessary for their responsibilities.

## Administrative Delegation

Delegate permissions at the Organizational Unit level instead of granting Domain Admin privileges.

## Organizational Unit Design

Separate:

- Users
- Workstations
- Servers
- Service Accounts
- Administrative Accounts

This improves policy management and reduces attack surface.

---

# 🎓 Skills Demonstrated

## Windows Administration

- Active Directory Users and Computers (ADUC)
- Organizational Unit Management
- User Administration
- Computer Administration
- Group Management

## Identity & Access Management

- Authentication
- Authorization
- Delegation
- Group Policy Management

## PowerShell Administration

- Password Management
- Active Directory administrative commands

## Blue Team Fundamentals

- Active Directory architecture.
- Kerberos authentication workflow.
- Windows enterprise administration concepts.

---

# 📚 Key Learning Outcomes

- Understood how Windows Domains centralize authentication using Active Directory.
- Explored the architecture and hierarchy of Active Directory objects.
- Managed users, groups, and machine accounts within Organizational Units.
- Learned how Group Policy Objects are applied and distributed through SYSVOL.
- Understood Kerberos ticket-based authentication and NetNTLM challenge-response authentication.
- Explored Trees, Forests, and Trust Relationships used in enterprise Active Directory environments.

---

# 📌 Conclusion

The **Active Directory Basics** room provided a practical introduction to enterprise Windows identity management and domain administration. Through hands-on interaction with a Windows Domain Controller, I learned how Active Directory organizes users, computers, and security groups while enforcing centralized authentication and policy management.

This lab strengthened foundational knowledge required for Windows System Administration, Identity & Access Management (IAM), Blue Team operations, Security Operations Center (SOC) roles, and Active Directory security assessments.

---

# ⚠️ Educational Disclaimer

This documentation is intended for educational and portfolio purposes only.

- All TryHackMe challenge flags have been **redacted**.
- Passwords and credentials have been removed.
- The content focuses on Windows Active Directory concepts and administrative procedures rather than challenge solutions.
