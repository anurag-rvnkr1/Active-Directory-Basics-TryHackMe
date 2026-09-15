# Active Directory Basics — TryHackMe Walkthrough

> **Room:** Active Directory Basics (TryHackMe)

## Overview
This repository documents my learning journey through the **Active Directory Basics** room on TryHackMe. It explains the concepts learned and the practical administrative tasks performed in a Windows Active Directory environment.

> **Note:** All challenge flags have been intentionally removed or redacted to avoid plagiarism.

## Objectives
- Understand Windows Domains and Active Directory.
- Explore Domain Controllers, Users, Groups, Machines, and Organizational Units.
- Manage users and computers inside Active Directory.
- Understand Group Policy Objects (GPOs), SYSVOL, Kerberos, NetNTLM, Trees, Forests, and Trusts.

## Lab Environment
- Platform: TryHackMe
- OS: Windows Server (Domain Controller)
- Access Method: Remote Desktop (RDP)
- Tools Used: Active Directory Users and Computers, PowerShell

## Task Summary
| Task | Description |
|------|-------------|
| Task 2 | Windows Domains and Active Directory |
| Task 3 | Users, Groups, Machines, OUs |
| Task 4 | Managing Users in AD |
| Task 5 | Managing Computers in AD |
| Task 6 | Group Policy Objects |
| Task 7 | Authentication Protocols |
| Task 8 | Trees, Forests, and Trust Relationships |

## Walkthrough

### Task 2 — Windows Domains
Active Directory stores domain credentials centrally on a Domain Controller.

### Task 3 — Active Directory Objects
Created and organized users and machines using Organizational Units.

### Task 4 — Managing Users
- Opened **Active Directory Users and Computers**.
- Navigated through Organizational Units.
- Modified a user account using delegated administrative privileges.
- Logged in as the updated user account to verify access.

**Flag:** `[REDACTED]`

### Task 5 — Managing Computers
- Created a new **Workstations OU**.
- Moved workstation objects into the OU.
- Separated workstations and servers into dedicated OUs.

### Task 6 — Group Policy Objects
- Learned how GPOs are linked to OUs.
- Identified the **SYSVOL** network share used for GPO distribution.

### Task 7 — Authentication
Compared Kerberos and NetNTLM authentication.

### Task 8 — AD Structure
Explored Trees, Forests, and Trust Relationships.

## Screenshots

Replace the placeholders with screenshots stored in the repository.

```md
![Task 4 - AD Users and Computers](Screenshots/task4-ad-users.png)
```

## Key Learning Outcomes
- Active Directory architecture.
- Domain administration basics.
- OU design and delegation.
- GPO management.
- Kerberos authentication workflow.
- Domain trust concepts.

## Disclaimer
This repository is for educational purposes only. Flags have been removed to respect TryHackMe policies.
