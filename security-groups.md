# Active Directory Security Groups

## Overview

Security groups in Active Directory are used to manage access to resources such as shared folders, printers, applications, VPN access, and administrative tools.

Instead of assigning permissions to each user individually, administrators add users to groups. This makes access easier to manage, audit, and troubleshoot.

## Purpose

This document explains:

- What security groups are
- Why they are used
- Common group types
- How users are added to groups
- How groups support access control
- Basic troubleshooting steps

## What Is a Security Group?

A security group is a collection of users, computers, or other groups that share access permissions.

Example:

```text
Group Name: SharedDrive-Sales
Members: Sales users
Access: Sales shared folder
Permission: Modify
```

If a user is added to the `SharedDrive-Sales` group, they receive access to the Sales shared folder based on that group's permissions.

## Why Security Groups Are Important

Security groups help administrators:

- Apply permissions consistently
- Reduce manual access errors
- Support least privilege access
- Improve security auditing
- Make onboarding and offboarding easier
- Troubleshoot access issues faster

## Common Security Group Examples

| Group Name | Purpose |
|---|---|
| HR-Users | Access to HR resources |
| Sales-Users | Access to Sales systems and folders |
| VPN-Users | Permission to connect to VPN |
| Printer-Floor1 | Access to a specific printer |
| SharedDrive-Finance-ReadOnly | Read-only access to Finance folder |
| SharedDrive-Marketing-Modify | Modify access to Marketing folder |

## Security Group Scope

Active Directory security groups can have different scopes.

### Domain Local Groups

Usually used to assign permissions to resources in the same domain.

Example:

```text
DL-Folder-Sales-Modify
```

### Global Groups

Usually used to group users based on role, department, or job function.

Example:

```text
GG-Sales-Users
```

### Universal Groups

Used in larger environments with multiple domains.

Example:

```text
UG-All-Company-VPN
```

## Basic Group Naming Convention

A clear naming convention helps support teams understand what a group does.

Example format:

```text
Resource-Department-Permission
```

Examples:

```text
SharedDrive-Sales-Read
SharedDrive-Sales-Modify
VPN-RemoteUsers
Printer-Accounting
```

## Step 1: Find the Correct Group

1. Open **Active Directory Users and Computers**.
2. Search for the group name.
3. Confirm the group description.
4. Review the group's purpose before adding users.

Avoid adding users to a group if the purpose is unclear.

## Step 2: Add a User to a Security Group

1. Open the user account in Active Directory.
2. Go to the **Member Of** tab.
3. Click **Add**.
4. Enter the group name.
5. Click **Check Names**.
6. Click **OK**.
7. Apply the changes.

## Step 3: Verify Group Membership

To verify group membership:

1. Open the user account.
2. Select **Member Of**.
3. Confirm the required group appears.
4. Ask the user to sign out and sign back in, if needed.
5. Test access to the resource.

You can also use Command Prompt:

```cmd
whoami /groups
```

This shows the groups applied to the current signed-in user session.

## Step 4: Remove a User from a Group

1. Open the user account.
2. Go to **Member Of**.
3. Select the group.
4. Click **Remove**.
5. Confirm the change.
6. Document the removal.

Removing group access is important when:

- A user changes departments
- A user no longer needs access
- A user leaves the company
- Access was added temporarily

## Troubleshooting Access Issues

| Issue | Possible Cause | Resolution |
|---|---|---|
| User cannot access shared folder | Missing group membership | Add user to correct group |
| User was added but access still fails | User has not signed out/in | Ask user to sign out and sign back in |
| User has too much access | User belongs to extra group | Review and remove unnecessary groups |
| Group name is unclear | Poor naming convention | Check group description or ask senior admin |
| Access works for others but not one user | Incorrect user account or permissions | Compare group membership with working user |

## Best Practices

- Use groups instead of assigning permissions directly to users.
- Follow the least privilege principle.
- Add descriptions to groups.
- Use clear naming conventions.
- Review group membership regularly.
- Remove access when it is no longer needed.
- Document group changes in tickets.
- Escalate unclear access requests.

## Example Ticket Note

```text
Reviewed access request for Jordan Smith.
Added user jsmith to SharedDrive-Sales-Modify and VPN-Users security groups.
Confirmed user signed out and signed back in.
User verified access to Sales shared folder and VPN.
Ticket completed.
```

## Skills Demonstrated

- Active Directory group management
- Access control basics
- Permission troubleshooting
- Least privilege security
- User access administration
- Help desk documentation
