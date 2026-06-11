# Shared Folder Permissions

## Overview

Shared folders allow users to access files over a network. In Windows Server environments, shared folder access is usually controlled using share permissions, NTFS permissions, and Active Directory security groups.

This document explains the basics of creating a shared folder and assigning permissions in a safe and organized way.

## Purpose

This process helps demonstrate:

- Creating a shared folder
- Applying share permissions
- Applying NTFS permissions
- Using security groups for access
- Testing access from a workstation
- Troubleshooting common permission issues

## Example Environment

Example lab setup:

- File Server: Windows Server
- Domain: `company.local`
- Shared folder path: `D:\Shares\Sales`
- Network path: `\\FileServer01\Sales`
- Security group: `SharedDrive-Sales-Modify`

## Share Permissions vs NTFS Permissions

Windows shared folder access is controlled by two permission layers.

### Share Permissions

Share permissions apply when users access the folder over the network.

Common share permissions:

| Permission | Description |
|---|---|
| Read | View files and folders |
| Change | Add, edit, and delete files |
| Full Control | Change permissions and take ownership |

### NTFS Permissions

NTFS permissions apply to the folder on the disk.

Common NTFS permissions:

| Permission | Description |
|---|---|
| Read & Execute | Open and run files |
| List Folder Contents | View folder contents |
| Read | View files |
| Write | Create and edit files |
| Modify | Read, write, edit, and delete files |
| Full Control | Complete control including permissions |

The most restrictive permission usually applies when both share and NTFS permissions are involved.

## Recommended Permission Approach

A common approach is:

- Set share permission to allow broad access for authenticated users or a specific group.
- Use NTFS permissions for more detailed control.
- Assign permissions to Active Directory groups, not individual users.

Example:

```text
Folder: D:\Shares\Sales
Share name: Sales
Security group: SharedDrive-Sales-Modify
Permission: Modify
```

## Step 1: Create the Folder

1. Sign in to the file server.
2. Open File Explorer.
3. Create a folder.

Example:

```text
D:\Shares\Sales
```

4. Right-click the folder.
5. Select **Properties**.

## Step 2: Configure Sharing

1. Go to the **Sharing** tab.
2. Click **Advanced Sharing**.
3. Select **Share this folder**.
4. Enter the share name.

Example:

```text
Sales
```

5. Click **Permissions**.
6. Add the required group.
7. Assign the correct share permission.
8. Click **Apply**.

Example share permission:

```text
SharedDrive-Sales-Modify: Change
```

## Step 3: Configure NTFS Permissions

1. Go to the **Security** tab.
2. Click **Edit**.
3. Add the required security group.
4. Assign the correct NTFS permission.

Example NTFS permission:

```text
SharedDrive-Sales-Modify: Modify
```

5. Remove unnecessary permissions only if approved by policy.
6. Click **Apply**.

## Step 4: Test Access from a Workstation

On a domain-joined workstation:

1. Sign in as a test user or assigned user.
2. Open File Explorer.
3. Enter the network path.

Example:

```text
\\FileServer01\Sales
```

4. Test the expected access:
   - Can the user open the folder?
   - Can the user create a test file?
   - Can the user edit the test file?
   - Can the user delete the test file, if Modify access is expected?

## Step 5: Map the Shared Folder

The folder can be mapped manually or through Group Policy.

Manual mapping:

1. Open File Explorer.
2. Right-click **This PC**.
3. Select **Map network drive**.
4. Choose a drive letter.
5. Enter the folder path.

Example:

```text
S: -> \\FileServer01\Sales
```

## Step 6: Document the Configuration

Example documentation:

```text
Created shared folder: D:\Shares\Sales
Share path: \\FileServer01\Sales
Security group: SharedDrive-Sales-Modify
Share permission: Change
NTFS permission: Modify
Tested access with user jsmith.
Folder access confirmed.
```

## Common Issues

| Issue | Possible Cause | Resolution |
|---|---|---|
| User cannot open folder | Missing group membership | Add user to correct security group |
| User can open but cannot edit | NTFS permission is read-only | Update NTFS permission if approved |
| User was added but still cannot access | User session has old token | Ask user to sign out and sign back in |
| Access denied for everyone | Incorrect share or NTFS permissions | Review both permission layers |
| Folder path does not open | Incorrect server or share name | Confirm network path and DNS |
| User can access wrong folder | User is in extra group | Review group membership |

## Best Practices

- Use Active Directory groups for folder access.
- Avoid assigning permissions directly to individual users.
- Follow least privilege.
- Use clear group names.
- Separate read-only and modify access groups.
- Test access after changes.
- Document permission changes.
- Review folder permissions regularly.

## Skills Demonstrated

- Windows Server file sharing
- NTFS permission management
- Share permission configuration
- Active Directory group-based access
- Network path testing
- Access troubleshooting
- Documentation and support process
