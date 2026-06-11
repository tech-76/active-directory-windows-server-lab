# Active Directory User Account Setup

## Overview

This document explains a basic process for creating and configuring a new user account in Active Directory. It is written as a lab-style support procedure for help desk, desktop support, and junior system administration practice.

Active Directory user account setup is commonly required during employee onboarding, account provisioning, department changes, and access management.

## Purpose

The purpose of this process is to:

- Create a new domain user account
- Assign the user to the correct organizational unit
- Set an initial password
- Require password change at first sign-in
- Add the user to the correct security groups
- Confirm the account works as expected

## Example Environment

This example assumes a Windows Server Active Directory environment.

Example lab setup:

- Domain Controller: Windows Server
- Domain: `company.local`
- User workstation: Windows 10 or Windows 11
- Management tool: Active Directory Users and Computers
- Admin role: Help Desk / Junior Administrator

## Required Information Before Creating the Account

Before creating the account, collect the following information:

| Information Needed | Example |
|---|---|
| First name | Jordan |
| Last name | Smith |
| Username | jsmith |
| Department | Sales |
| Job title | Sales Associate |
| Manager | Sarah Lee |
| Email format | jsmith@company.com |
| Required groups | Sales, SharedDrive-Sales, VPN-Users |
| Temporary password | Provided securely |

## Step 1: Open Active Directory Users and Computers

1. Sign in to the domain controller or an admin workstation.
2. Open **Server Manager**.
3. Go to **Tools**.
4. Select **Active Directory Users and Computers**.
5. Expand the domain name.
6. Navigate to the correct Organizational Unit, such as:

```text
company.local
└── Users
    └── Sales
```

## Step 2: Create the New User

1. Right-click the correct Organizational Unit.
2. Select **New**.
3. Select **User**.
4. Enter the user's first name and last name.
5. Enter the user logon name.

Example:

```text
First name: Jordan
Last name: Smith
User logon name: jsmith
```

6. Click **Next**.

## Step 3: Set the Initial Password

1. Enter a temporary password.
2. Confirm the password.
3. Select the following option:

```text
User must change password at next logon
```

4. Click **Next**.
5. Review the details.
6. Click **Finish**.

## Step 4: Configure User Properties

After creating the account, open the user object and review the following tabs.

### General Tab

Confirm:

- First name
- Last name
- Display name
- Email address
- Office phone number, if available

### Organization Tab

Add:

- Job title
- Department
- Company
- Manager

### Account Tab

Confirm:

- Username is correct
- Domain logon name is correct
- Account is enabled
- Password options are correct

## Step 5: Add the User to Security Groups

1. Open the user account.
2. Go to the **Member Of** tab.
3. Click **Add**.
4. Enter the required group names.
5. Click **Check Names**.
6. Confirm the correct groups are selected.
7. Click **OK**.
8. Apply the changes.

Example groups:

```text
Sales
SharedDrive-Sales
VPN-Users
Printer-Sales-Floor
Microsoft365-Basic
```

## Step 6: Verify the Account

To verify the account:

1. Confirm the account appears in the correct Organizational Unit.
2. Confirm the username follows company naming standards.
3. Confirm the account is enabled.
4. Confirm the correct security groups are assigned.
5. Test sign-in from a workstation, if available.
6. Confirm the user is required to change the password at first sign-in.

## Step 7: Document the Request

In a ticketing system, document:

- Date account was created
- Username created
- Department
- Groups assigned
- Any special access added
- Confirmation that the account was tested
- Whether the request was completed or escalated

Example ticket note:

```text
Created new Active Directory user account for Jordan Smith.
Username: jsmith
OU: Users/Sales
Added user to Sales, SharedDrive-Sales, VPN-Users, and Printer-Sales-Floor groups.
Set temporary password and enabled password change at next logon.
Account verified and ready for user sign-in.
```

## Common Issues

| Issue | Possible Cause | Resolution |
|---|---|---|
| User cannot sign in | Account disabled | Enable the account in Active Directory |
| User cannot access shared folder | Missing security group | Add user to the correct folder access group |
| User cannot print | Missing printer group or printer mapping | Add user to printer group or map printer manually |
| Password does not work | Temporary password typed incorrectly | Reset password and confirm with user |
| Account does not appear on workstation | Replication delay | Wait and confirm domain controller replication |

## Best Practices

- Follow the company naming convention.
- Use least privilege access.
- Add users to groups instead of assigning access directly.
- Require password change at first sign-in.
- Never send passwords in plain text email.
- Document all account changes in a ticket.
- Disable or remove access when the user leaves the organization.

## Skills Demonstrated

- Active Directory user administration
- Account provisioning
- Organizational Unit management
- Security group assignment
- Password policy awareness
- Help desk documentation
- Access control basics
