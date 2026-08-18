# Week 1 - FR1 & FR2

## Learning Objective

Understand the difference between:

- FR1: Identification and Authentication Control (IAC)
- FR2: Use Control (UC)

and apply both concepts in the OT Security Homelab.

---

# FR1 - Identification and Authentication Control (IAC)

## Purpose

Ensure that every user, device, or process is properly identified and authenticated before being granted access to a system.

The main question answered by FR1 is:

> Who are you?

---

## Examples

- Username and password
- SSH keys
- Multi-Factor Authentication (MFA)
- Active Directory authentication
- Digital certificates

---

## Homelab Implementation

### Asset

Jump Server

### Controls

- Unique user accounts
- Strong passwords
- SSH authentication
- Disabled root login

### Example

```text
jonathan
operator
engineer
```

Each account should be individually identifiable.

---

## Key Takeaways

- Authentication verifies identity.
- Shared accounts should be avoided.
- Every action should be traceable to a user.

---

# FR2 - Use Control (UC)

## Purpose

Ensure that authenticated users can only perform authorized actions.

The main question answered by FR2 is:

> What are you allowed to do?

---

## Examples

- User permissions
- Linux groups
- RBAC (Role-Based Access Control)
- Sudo privileges
- Access Control Lists (ACLs)

---

## Homelab Implementation

### Operator

Permissions:

- Read-only access
- No administrative privileges

### Engineer

Permissions:

- Access to OT assets
- Limited administrative privileges

### Administrator

Permissions:

- Full system administration
- Firewall management
- User management

---

## Example

```text
Operator
    Login: Yes
    sudo: No

Engineer
    Login: Yes
    sudo: Limited

Administrator
    Login: Yes
    sudo: Full
```

---

## Key Takeaways

- Authentication is not authorization.
- Users should receive only the permissions they need.
- Least Privilege is a core principle of FR2.

---

# FR1 vs FR2

| FR1 | FR2 |
|------|------|
| Who are you? | What can you do? |
| Authentication | Authorization |
| Identity verification | Permission enforcement |
| Passwords, SSH Keys, MFA | Roles, ACLs, RBAC, sudo |

---

# Homelab Mapping

Current Architecture:

```text
IT Zone
    |
pfSense
    |
Management Zone
    |
Jump Server
    |
OT Zone
```

FR1 Implementation:

- User accounts
- Passwords
- SSH access

FR2 Implementation:

- Firewall rules
- User privileges
- Access restrictions

---

# Lessons Learned

- FR1 focuses on identity verification.
- FR2 focuses on permission management.
- A secure OT environment requires both.
- Authentication without authorization is insufficient.
- Authorization without authentication is impossible.

---

# Interview Questions

## Question

What is the difference between FR1 and FR2?

## Answer

FR1 verifies the identity of a user, device, or process before access is granted.

FR2 controls what actions an authenticated user, device, or process is allowed to perform after access has been granted.

---

## Question

How is FR1 implemented in your homelab?

## Answer

Using unique user accounts, strong passwords, and SSH authentication on the Jump Server.

---

## Question

How is FR2 implemented in your homelab?

## Answer

Using firewall rules, role-based access controls, Linux permissions, and least-privilege principles.
