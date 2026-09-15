# 🛡️ Active Directory Basics — TryHackMe Walkthrough

<div align="center">

![TryHackMe](https://img.shields.io/badge/TryHackMe-Active_Directory_Basics-red?style=for-the-badge&logo=tryhackme)
![Windows Server](https://img.shields.io/badge/Windows-Server_Active_Directory-0078D6?style=for-the-badge&logo=windows)
![Category](https://img.shields.io/badge/Category-Windows_Active_Directory-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

**Windows Active Directory Fundamentals • Identity & Access Management • Group Policy • Kerberos Authentication**

*A hands-on documentation of the "Active Directory Basics" room from TryHackMe.*

</div>

---

## 📖 Overview

This repository documents my practical completion of the **Active Directory Basics** room on **TryHackMe**. The lab focuses on understanding the core architecture of Microsoft Active Directory and performing common administrative operations within a Windows Domain environment.

Rather than providing challenge answers or captured flags, this repository explains the concepts, tools, workflows, and administrative tasks completed throughout the lab.

> **Disclaimer**
>
> This repository is intended for **educational and portfolio purposes only**. All flags, passwords, credentials, and challenge answers have been removed or redacted to respect TryHackMe's learning guidelines.

---

## 🎯 Lab Objectives

The objectives of this lab were to:

- Understand Windows Domains and Active Directory architecture.
- Learn the role of a Domain Controller.
- Explore Active Directory users, groups, and machine accounts.
- Create and organize Organizational Units (OUs).
- Perform user and computer administration.
- Understand Group Policy Objects (GPOs) and SYSVOL.
- Learn Windows authentication using Kerberos and NetNTLM.
- Understand Trees, Forests, and Trust Relationships.

---

## 🧪 Lab Environment

| Component | Details |
|-----------|---------|
| **Platform** | TryHackMe |
| **Room** | Active Directory Basics |
| **Operating System** | Windows Server (Domain Controller) |
| **Access Method** | Remote Desktop Protocol (RDP) |
| **Directory Service** | Microsoft Active Directory |
| **Administrative Tools** | Active Directory Users and Computers, PowerShell, Group Policy Management |
| **Authentication** | Kerberos & NetNTLM |
| **Skill Level** | Beginner → Intermediate |

---

## 🧩 Topics Covered

| Module | Concepts Learned |
|--------|------------------|
| Windows Domains | Centralized authentication and identity management |
| Domain Controller | Authentication, authorization, DNS integration |
| Active Directory Objects | Users, Groups, Computers, Organizational Units |
| User Administration | Password reset, delegated permissions, account management |
| Computer Administration | Creating and managing Workstation OUs |
| Group Policy | GPO creation, inheritance, SYSVOL distribution |
| Authentication | Kerberos, Ticket Granting Ticket (TGT), Ticket Granting Service (TGS), NetNTLM |
| Active Directory Structure | Trees, Forests, Trust Relationships |

---

## 📚 What I Learned

### Windows Domains

- Centralized user authentication.
- Identity and access management.
- Resource authorization across an enterprise network.

### Active Directory Administration

- Managing user accounts.
- Managing security groups.
- Working with machine accounts.
- Organizing resources using Organizational Units.

### Organizational Units (OUs)

- Creating departmental OUs.
- Delegating administration.
- Applying policies to groups of users and computers.

### Group Policy Objects (GPOs)

- Applying policies to users and computers.
- Understanding policy inheritance.
- SYSVOL synchronization across domain controllers.

### Authentication

- Kerberos authentication workflow.
- Ticket Granting Ticket (TGT).
- Service Tickets (TGS).
- NetNTLM legacy authentication.

### Active Directory Structure

- Domains
- Trees
- Forests
- Trust Relationships

---

## 🛠️ Administrative Tasks Performed

During this lab, I completed the following administrative operations inside Active Directory:

- Connected to a Windows Domain Controller through RDP.
- Explored Active Directory Users and Computers (ADUC).
- Identified users, groups, computers, and Organizational Units.
- Managed user accounts using delegated administrative privileges.
- Reset a user password using PowerShell.
- Verified successful user authentication.
- Created a new **Workstations** Organizational Unit.
- Moved workstation computer objects into the new OU.
- Learned Group Policy deployment through SYSVOL.
- Explored Active Directory authentication mechanisms.

---

## 🧠 Technical Concepts Explained

### Active Directory Objects

| Object | Description |
|--------|-------------|
| **Users** | Represents identities within the domain. |
| **Groups** | Used for centralized permission management. |
| **Machine Accounts** | Automatically created when computers join the domain. |
| **Organizational Units** | Containers used to organize objects and apply policies. |

### Authentication Protocols

| Kerberos | NetNTLM |
|----------|----------|
| Default Windows authentication protocol | Legacy authentication protocol |
| Ticket-based authentication | Challenge-response authentication |
| Mutual authentication | Compatibility-focused authentication |
| Preferred in modern domains | Used only when required |

---

## 🔐 Skills Demonstrated

### Windows Administration

- Active Directory Users and Computers (ADUC)
- User Management
- Organizational Unit Management
- Group Management
- Computer Object Management

### PowerShell

- Administrative user management commands.
- Password reset operations.
- Active Directory administration.

### Identity & Access Management (IAM)

- Authentication concepts.
- Authorization concepts.
- Delegation of administrative privileges.

### Blue Team Fundamentals

- Active Directory architecture.
- GPO management.
- Enterprise Windows security concepts.

---

## 📁 Repository Structure

```text
Active-Directory-Basics-TryHackMe/
│
├── README.md
├── LICENSE
│
├── Documentation/
│   ├── Active_Directory_Basics_Report.md
│   ├── Active_Directory_Basics_Report.pdf
│
├── Screenshots/
│   ├── task3-ou-structure.png
│   ├── task4-user-management.png
│   ├── task5-workstations-ou.png
│   ├── task6-gpo-management.png
│   ├── task7-authentication.png
│   └── task8-tree-forest-trust.png
│
└── Resources/
    └── notes.md
```

---

## 📄 Documentation

The complete documentation includes:

- Executive Summary
- Lab Environment
- Active Directory Fundamentals
- Windows Domain Architecture
- User & Computer Administration
- Organizational Units
- Delegation
- Group Policy Objects
- SYSVOL
- Kerberos Authentication
- NetNTLM Authentication
- Trees, Forests, and Trust Relationships
- Security Best Practices
- Learning Outcomes

> A professionally formatted **Word (.docx)** and **PDF** report is included in the `Documentation/` directory.

---

## 🛡️ Security Best Practices Covered

- Least Privilege Principle
- Organizational Unit design
- Administrative Delegation
- Password Management
- Group Policy Management
- Kerberos Authentication
- Windows Domain Security Fundamentals

---

## 💼 Skills Relevant for Cybersecurity Roles

This lab demonstrates foundational knowledge applicable to:

- SOC Analyst (L1/L2)
- Blue Team Analyst
- Windows System Administrator
- Identity & Access Management (IAM)
- Active Directory Security
- Cybersecurity Intern Roles

---

## 📚 References

- Microsoft Learn — Active Directory Documentation
- Microsoft Learn — Group Policy Documentation
- Microsoft Learn — Kerberos Authentication
- TryHackMe — Active Directory Basics Room

---

## ⚠️ Educational Use Notice

This repository contains documentation created after completing the TryHackMe **Active Directory Basics** learning room.

- No flags are published.
- No challenge answers are published.
- No credentials or sensitive information are included.
- Content has been rewritten in original documentation format for learning and portfolio purposes.

---

<div align="center">

### ⭐ If you found this documentation useful, consider giving the repository a star.

**Author:** Anurag Ravankar

*Cybersecurity • Active Directory • Blue Team Fundamentals*

</div>
