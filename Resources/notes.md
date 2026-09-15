# 📚 Active Directory Basics — Technical Notes

> Companion notes for the **TryHackMe – Active Directory Basics** room.

These notes summarize the most important Active Directory concepts, Windows Domain terminology, authentication mechanisms, and administrative practices learned during the lab. They are written as a technical reference rather than a walkthrough.

> **Purpose:** Learning reference, interview revision, and cybersecurity portfolio documentation.

---

# Table of Contents

- Windows Domains
- Active Directory Overview
- Domain Controller
- Active Directory Objects
- Organizational Units
- Security Groups
- Machine Accounts
- Group Policy Objects
- SYSVOL
- Kerberos Authentication
- NetNTLM Authentication
- Trees, Forests, and Trust Relationships
- Administrative Delegation
- PowerShell Notes
- Active Directory Security Best Practices
- Cybersecurity Interview Notes
- Key Takeaways

---

# Windows Domains

A **Windows Domain** is a centralized network administration model used in enterprise Windows environments. Instead of storing credentials and permissions on each computer individually, authentication and authorization are managed centrally through **Active Directory**.

## Why Organizations Use Domains

- Centralized authentication.
- Centralized user management.
- Policy enforcement.
- Resource access control.
- Simplified administration across hundreds or thousands of computers.

## Components of a Windows Domain

| Component | Purpose |
|-----------|---------|
| Domain Controller | Authenticates users and computers. |
| Active Directory | Stores domain objects and credentials. |
| DNS | Allows clients to locate services in the domain. |
| Group Policy | Applies security and configuration settings. |
| SYSVOL | Distributes Group Policy Objects. |

---

# Active Directory Overview

Active Directory (AD) is Microsoft's **directory service** for Windows environments.

It stores information about:

- Users
- Groups
- Computers
- Organizational Units
- Printers
- Shared folders
- Service Accounts
- Policies

## Core Functions

- Identity Management
- Authentication
- Authorization
- Policy Management
- Resource Discovery

## Active Directory Benefits

- Single Sign-On (SSO)
- Central administration
- Scalability
- Security policy enforcement
- Delegated administration

---

# Domain Controller (DC)

A **Domain Controller** is a Windows Server responsible for running Active Directory Domain Services (AD DS).

## Responsibilities

- Authenticate users.
- Authenticate computers.
- Store Active Directory database.
- Issue Kerberos tickets.
- Replicate directory information.
- Store SYSVOL.
- Integrate DNS services.

## Services Running on a DC

- Active Directory Domain Services
- Kerberos Key Distribution Center
- DNS Server
- LDAP
- SYSVOL Share
- NetLogon

## Why Multiple Domain Controllers?

Organizations deploy multiple Domain Controllers for:

- High Availability.
- Fault Tolerance.
- Replication.
- Disaster Recovery.

---

# Active Directory Objects

Everything inside Active Directory is stored as an **Object**.

## User Objects

Represent identities inside the organization.

Examples

- Employees
- Interns
- Administrators
- Service Accounts

Common attributes

- Username
- SID
- Password
- Email
- Department
- Group Membership

---

## Group Objects

Groups simplify permission management.

### Security Groups

Used for assigning permissions.

Examples

- Domain Admins
- Server Operators
- Backup Operators
- Account Operators

### Distribution Groups

Used for communication (email distribution).

---

## Computer Objects

Created automatically when computers join the domain.

Examples

```
DESKTOP-01$
HR-PC$
WEB-SERVER01$
```

Machine accounts end with **$**.

---

## Organizational Units (OU)

Organizational Units are containers used to organize objects logically.

### Why OUs Matter

- Apply Group Policies.
- Delegate administration.
- Organize departments.
- Separate workstations and servers.

### Example OU Structure

```text
Company.local
│
├── Management
├── Sales
├── IT
├── HR
├── Finance
│
├── Workstations
├── Servers
├── Service Accounts
└── Domain Controllers
```

### Benefits

- Easier administration.
- Better security.
- Policy inheritance.
- Scalability.

---

# Security Groups

Groups assign permissions to multiple users simultaneously.

## Common Built-in Groups

| Group | Purpose |
|-------|---------|
| Domain Admins | Full administrative control over the domain. |
| Enterprise Admins | Administrative rights across the forest. |
| Account Operators | Manage user and group accounts. |
| Backup Operators | Backup and restore permissions. |
| Print Operators | Printer administration. |
| Server Operators | Manage servers. |

## Best Practice

Assign permissions to groups instead of individual users.

---

# Machine Accounts

Every computer joined to Active Directory receives its own identity.

## Naming Convention

```
COMPUTERNAME$
```

Example

```
LAPTOP-01$
```

## Purpose

- Mutual authentication.
- Trust relationship with the domain.
- Secure communication.

## Machine Password

Windows automatically rotates machine account passwords periodically.

---

# Organizational Units (OU)

## Administrative Uses

- Department separation.
- Geographic locations.
- Security tiers.
- Workstations vs Servers.

## Delegation

Instead of making someone a Domain Admin:

- Delegate permissions to one OU.
- Allow password resets.
- Allow user creation.
- Restrict scope.

This follows the **Principle of Least Privilege**.

---

# Group Policy Objects (GPO)

A Group Policy Object is a collection of Windows configuration settings.

## Targets

- Users
- Computers

## Common Policies

### User Policies

- Desktop wallpaper.
- Password policy.
- Control Panel restrictions.
- Login scripts.

### Computer Policies

- Firewall.
- Windows Updates.
- BitLocker.
- USB restrictions.
- Defender settings.

---

## GPO Processing Order

Remember **LSDOU**

| Order | Meaning |
|-------|---------|
| L | Local Policy |
| S | Site |
| D | Domain |
| OU | Organizational Unit |

Later policies override earlier ones unless enforced.

---

## GPO Inheritance

Policies applied to parent containers flow to child OUs.

Inheritance can be:

- Allowed.
- Blocked.
- Enforced.

---

# SYSVOL

SYSVOL is a shared folder on Domain Controllers.

## Default Location

```text
C:\Windows\SYSVOL\sysvol\
```

## Contents

- Group Policy Objects.
- Login Scripts.
- Policy Templates.

## Why SYSVOL Matters

Clients periodically synchronize policies from SYSVOL.

---

# Kerberos Authentication

Kerberos is the default authentication protocol in modern Windows Domains.

## Goals

- Secure authentication.
- Mutual authentication.
- Ticket-based access.

## Components

| Component | Purpose |
|-----------|---------|
| KDC | Key Distribution Center |
| AS | Authentication Service |
| TGS | Ticket Granting Service |
| TGT | Ticket Granting Ticket |

---

## Kerberos Workflow

1. User logs in.
2. Authentication request sent.
3. KDC verifies identity.
4. User receives TGT.
5. User requests service ticket.
6. TGS issues ticket.
7. Service validates ticket.
8. Access granted.

---

## Ticket Granting Ticket (TGT)

Purpose

- Initial authentication.
- Used to request additional service tickets.

Without a valid TGT, additional Kerberos services cannot be requested.

---

## Ticket Granting Service (TGS)

Provides tickets for accessing resources such as:

- File Shares
- SQL Servers
- Web Servers
- Print Servers

---

## Kerberos Advantages

- Password not transmitted.
- Mutual authentication.
- Replay protection.
- Time synchronization requirement.

---

# NetNTLM Authentication

Legacy Windows authentication protocol.

## Authentication Model

Challenge-response.

### Workflow

1. Server sends challenge.
2. Client encrypts challenge using password hash.
3. Server validates response.

Password is never sent over the network.

---

## Kerberos vs NetNTLM

| Kerberos | NetNTLM |
|----------|----------|
| Default authentication protocol | Legacy protocol |
| Ticket-based | Challenge-response |
| Mutual authentication | Server authentication only |
| More secure | Compatibility-focused |

---

# Trees

A Tree is a collection of domains sharing a common namespace.

Example

```text
company.local

sales.company.local

it.company.local

hr.company.local
```

Domains trust each other automatically.

---

# Forests

A Forest is the highest-level Active Directory structure.

Contains multiple trees.

Example

```text
company.local

research.local

subsidiary.local
```

Each tree can have its own namespace.

---

# Trust Relationships

Trusts allow users from one domain to access resources in another.

## Types

### One-Way Trust

Users in Domain A can access Domain B.

### Two-Way Trust

Users in both domains can access shared resources.

### Transitive Trust

Trust extends automatically.

### Non-Transitive Trust

Trust remains between only two domains.

---

# Administrative Delegation

Delegation grants permissions without giving Domain Admin rights.

## Examples

Helpdesk Team

- Reset passwords.
- Unlock accounts.

HR Team

- Create users.
- Disable accounts.

IT Support

- Join computers to domain.
- Manage workstation OU.

---

## Benefits

- Reduced attack surface.
- Least privilege.
- Easier auditing.
- Better operational security.

---

# PowerShell Notes

Useful Active Directory administrative commands.

## View User

```powershell
Get-ADUser username
```

Returns Active Directory user information.

---

## Reset Password

```powershell
Set-ADAccountPassword
```

Used by delegated administrators.

---

## Unlock Account

```powershell
Unlock-ADAccount username
```

Unlocks locked domain account.

---

## Disable User

```powershell
Disable-ADAccount username
```

Temporarily disables user.

---

## Enable User

```powershell
Enable-ADAccount username
```

Re-enables disabled account.

---

## Create Organizational Unit

```powershell
New-ADOrganizationalUnit
```

Creates a new OU.

---

# Active Directory Security Best Practices

## Least Privilege

Grant only required permissions.

---

## Separate Administrative Accounts

Use dedicated administrator accounts instead of everyday accounts.

---

## Separate Servers and Workstations

Different policies reduce attack surface.

---

## Strong Password Policies

- Complexity enabled.
- Minimum length.
- Password expiration.
- Account lockout policy.

---

## Multi-Factor Authentication

Use MFA wherever possible.

---

## Audit Policies

Enable auditing for:

- Logon Events
- Account Management
- Object Access
- Privilege Use
- Policy Changes

---

## Protect Privileged Groups

Monitor:

- Domain Admins
- Enterprise Admins
- Administrators

---

## Secure SYSVOL

Restrict write permissions.

---

## Disable Legacy Protocols

Reduce NetNTLM usage where possible.

---

# Active Directory Attack Surface (Awareness)

Understanding these attacks helps defenders recognize risks.

| Technique | Description |
|-----------|-------------|
| Kerberoasting | Extracting service tickets for offline cracking. |
| AS-REP Roasting | Attacking accounts without Kerberos pre-authentication. |
| Pass-the-Hash | Using NTLM hashes for authentication. |
| Pass-the-Ticket | Reusing Kerberos tickets. |
| Golden Ticket | Forged TGT using KRBTGT hash. |
| Silver Ticket | Forged service ticket. |
| DCSync | Replicating password hashes from Domain Controller. |

> These techniques are referenced for defensive awareness only.

---

# Blue Team Detection Ideas

Monitor:

- Failed logins.
- Account lockouts.
- Privileged group changes.
- Kerberos ticket anomalies.
- GPO modifications.
- SYSVOL changes.
- Machine account creation.

Useful Windows Event IDs include:

| Event ID | Description |
|----------|-------------|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4720 | User account created |
| 4722 | User enabled |
| 4725 | User disabled |
| 4728 | Added to security group |
| 4732 | Added to local security group |

---

# Interview Revision Notes

## What is Active Directory?

A Microsoft directory service providing centralized identity management and authentication for Windows Domains.

---

## Difference Between Authentication and Authorization

Authentication verifies identity.

Authorization determines access permissions.

---

## What is SYSVOL?

A shared folder on Domain Controllers used to distribute Group Policy Objects and login scripts.

---

## What is an Organizational Unit?

A logical container for organizing users, groups, and computers while allowing policy application and delegated administration.

---

## Why Kerberos Instead of NetNTLM?

Kerberos provides ticket-based mutual authentication and is more secure than legacy NetNTLM authentication.

---

## What is a Trust Relationship?

A configured relationship allowing users from one domain to access resources in another domain.

---

# Key Takeaways

- Active Directory centralizes identity and access management.
- Domain Controllers authenticate users and computers.
- Organizational Units simplify administration and policy management.
- Group Policy Objects enforce consistent security configurations.
- SYSVOL distributes Group Policies across the domain.
- Kerberos is the preferred authentication protocol in modern Windows domains.
- Delegation enables secure administration without excessive privileges.
- Trees, Forests, and Trust Relationships enable scalable enterprise Active Directory deployments.

---

# Revision Checklist

- [x] Windows Domains
- [x] Active Directory Architecture
- [x] Domain Controller Responsibilities
- [x] Users, Groups, and Computers
- [x] Organizational Units
- [x] Security Groups
- [x] Group Policy Objects
- [x] SYSVOL
- [x] Kerberos Authentication
- [x] NetNTLM Authentication
- [x] Trees and Forests
- [x] Trust Relationships
- [x] Administrative Delegation
- [x] Active Directory Security Best Practices
- [x] Blue Team Detection Concepts

---

## Author Notes

These notes were created after completing the **Active Directory Basics** room on TryHackMe and are intended as a personal cybersecurity knowledge base and interview revision resource.

The content has been rewritten in original language and does not contain challenge flags, credentials, or proprietary solutions.
