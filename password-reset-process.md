# Password Reset Process

## Overview

This document explains a standard password reset process for an Active Directory user account. Password reset requests are common in help desk and desktop support environments.

The goal is to restore user access while protecting the security of the account and the organization.

## Purpose

This process helps support staff:

- Verify the user's identity
- Reset the user's password safely
- Require the user to change the password at next sign-in
- Unlock the account if needed
- Document the support request properly

## Example Environment

Example lab setup:

- Domain Controller: Windows Server
- Directory service: Active Directory
- Management tool: Active Directory Users and Computers
- User workstation: Windows 10 or Windows 11
- Support role: Help Desk / Desktop Support

## Step 1: Confirm the User's Identity

Before resetting a password, verify the user.

Possible verification methods include:

- Employee ID
- Manager confirmation
- Security questions, if approved by company policy
- Multi-factor authentication confirmation
- Callback to a phone number already on file

Do not reset a password without confirming the request is legitimate.

## Step 2: Locate the User Account

1. Open **Active Directory Users and Computers**.
2. Search for the user by:
   - First name
   - Last name
   - Username
   - Email address
3. Confirm the correct account.

Example username:

```text
jsmith
```

## Step 3: Check Account Status

Before resetting the password, check whether the account is:

- Disabled
- Locked out
- Expired
- Using an expired password
- In the correct Organizational Unit

In **Active Directory Users and Computers**:

1. Right-click the user account.
2. Select **Properties**.
3. Go to the **Account** tab.
4. Review the account settings.

## Step 4: Reset the Password

1. Right-click the user account.
2. Select **Reset Password**.
3. Enter a temporary password.
4. Confirm the temporary password.
5. Select:

```text
User must change password at next logon
```

6. If the account is locked, select:

```text
Unlock the user's account
```

7. Click **OK**.

## Step 5: Provide the Temporary Password Securely

Share the temporary password using an approved secure method.

Avoid:

- Sending passwords by plain text email
- Sending passwords through public chat
- Sharing passwords with unauthorized users
- Leaving passwords in ticket notes without protection

A better approach is to provide the temporary password verbally or through an approved secure password-sharing method.

## Step 6: Ask the User to Sign In

Ask the user to sign in using the temporary password.

The user should then be prompted to create a new password.

A strong password should:

- Meet company complexity requirements
- Not reuse previous passwords
- Not include the user's name
- Not be shared with anyone
- Be stored securely using an approved password manager if allowed

## Step 7: Confirm Access

Confirm the user can access required services, such as:

- Windows workstation
- Microsoft 365
- Email
- VPN
- Shared folders
- Internal applications
- Printers, if needed

## Step 8: Document the Ticket

Example ticket note:

```text
Verified user identity according to support process.
Reset Active Directory password for jsmith.
Unlocked account.
Enabled password change at next logon.
User confirmed successful sign-in and access to email.
Ticket resolved.
```

## Common Issues

| Issue | Possible Cause | Resolution |
|---|---|---|
| User is still locked out | Multiple failed sign-in attempts | Unlock account and check saved passwords on devices |
| Password reset works but email fails | Cached old password | Update password in Outlook, phone, or saved credentials |
| User cannot connect to VPN | Old password saved in VPN client | Remove saved credentials and reconnect |
| Account keeps locking | Mobile device using old password | Check phones, tablets, mapped drives, and services |
| User forgot username | Wrong account searched | Confirm identity and search by email or employee record |

## Security Considerations

Password resets are sensitive because they can give access to company systems. Support staff should always:

- Verify identity before making changes
- Follow company password policy
- Avoid sharing passwords insecurely
- Watch for suspicious reset requests
- Escalate unusual requests to a supervisor or security team
- Document actions clearly

## Skills Demonstrated

- Active Directory support
- Password reset procedure
- Account unlock process
- Identity verification awareness
- User support
- Ticket documentation
- Security best practices
