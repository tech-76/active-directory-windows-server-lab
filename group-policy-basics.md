# Group Policy Basics

## Overview

Group Policy is a Windows Server feature used to manage settings for users and computers in an Active Directory environment.

Administrators use Group Policy Objects, also called GPOs, to apply settings such as password rules, mapped drives, desktop restrictions, printer deployment, and security configurations.

## Purpose

This document explains:

- What Group Policy is
- Why it is used
- How Group Policy Objects work
- How policies are linked to Organizational Units
- Basic commands for testing Group Policy
- Common troubleshooting steps

## What Is Group Policy?

Group Policy allows administrators to centrally manage settings across domain-joined computers and users.

Example uses:

- Enforce password complexity
- Map shared drives
- Deploy printers
- Set desktop wallpaper
- Block access to Control Panel
- Configure Windows Update settings
- Apply security settings

## Key Terms

| Term | Meaning |
|---|---|
| GPO | Group Policy Object |
| OU | Organizational Unit |
| Domain | A managed network environment |
| Link | Connects a GPO to a site, domain, or OU |
| Inheritance | Allows policies from higher levels to apply below |
| Security Filtering | Controls who the GPO applies to |
| WMI Filtering | Applies policy based on system conditions |

## Example Active Directory Structure

```text
company.local
├── Users
│   ├── HR
│   ├── Sales
│   └── IT
└── Computers
    ├── Desktops
    └── Laptops
```

A GPO can be linked to an OU such as `Sales`, `Desktops`, or `Laptops`.

## User Configuration vs Computer Configuration

Group Policy has two main sections.

### User Configuration

Applies to user accounts.

Examples:

- Desktop settings
- Folder redirection
- Drive mappings
- Start menu settings
- User restrictions

### Computer Configuration

Applies to computers.

Examples:

- Security settings
- Windows Update settings
- Firewall settings
- Startup scripts
- Local administrator settings

## Step 1: Open Group Policy Management

1. Sign in to the domain controller or management workstation.
2. Open **Server Manager**.
3. Select **Tools**.
4. Open **Group Policy Management**.

## Step 2: Create a New GPO

1. Expand the domain.
2. Right-click **Group Policy Objects**.
3. Select **New**.
4. Name the GPO clearly.

Example:

```text
GPO-Map-Sales-Drive
```

5. Click **OK**.

## Step 3: Edit the GPO

1. Right-click the new GPO.
2. Select **Edit**.
3. Choose the correct policy area.

Example path for drive mapping:

```text
User Configuration
└── Preferences
    └── Windows Settings
        └── Drive Maps
```

## Step 4: Link the GPO to an OU

1. Right-click the target OU.
2. Select **Link an Existing GPO**.
3. Choose the GPO.
4. Click **OK**.

Example:

```text
OU: Sales
GPO: GPO-Map-Sales-Drive
```

## Step 5: Test the Policy

On a client workstation, sign in as a user in the target OU.

Run:

```cmd
gpupdate /force
```

Then check applied policies:

```cmd
gpresult /r
```

For a detailed report:

```cmd
gpresult /h C:\Temp\gp-report.html
```

Open the report in a browser and review which policies applied.

## Example: Map a Shared Drive

Goal:

Map the Sales shared folder as drive `S:` for Sales users.

Example network path:

```text
\\FileServer01\Sales
```

Example GPO name:

```text
GPO-Map-Sales-Drive
```

Expected result:

```text
S: drive appears when Sales users sign in
```

## Common Troubleshooting

| Issue | Possible Cause | Resolution |
|---|---|---|
| GPO does not apply | GPO linked to wrong OU | Confirm the user or computer is in the correct OU |
| Drive does not map | Incorrect network path | Test the UNC path manually |
| Policy applies to wrong users | Security filtering issue | Review security filtering |
| Settings still not showing | User has not signed out/in | Ask user to sign out and sign back in |
| Computer policy not applying | GPO configured under user settings | Check User vs Computer Configuration |
| Policy blocked | Inheritance or permissions issue | Review inheritance and delegation |

## Useful Commands

### Force Policy Update

```cmd
gpupdate /force
```

### View Applied Policies

```cmd
gpresult /r
```

### Create HTML Policy Report

```cmd
gpresult /h C:\Temp\gp-report.html
```

### Check Current User

```cmd
whoami
```

### Check User Groups

```cmd
whoami /groups
```

## Best Practices

- Use clear GPO names.
- Test policies on a small OU first.
- Avoid linking too many GPOs at the domain level.
- Document the purpose of each GPO.
- Use security filtering carefully.
- Do not make unnecessary changes to default policies.
- Use separate GPOs for separate tasks when possible.
- Review applied policies with `gpresult`.

## Example Ticket Note

```text
Created and linked GPO-Map-Sales-Drive to Sales OU.
Configured drive mapping for \\FileServer01\Sales as S: drive.
Ran gpupdate /force on test workstation.
Confirmed policy applied using gpresult /r.
Sales drive mapping verified successfully.
```

## Skills Demonstrated

- Group Policy fundamentals
- GPO creation and linking
- Organizational Unit targeting
- Drive mapping basics
- Policy testing with command-line tools
- Windows Server administration
- Troubleshooting and documentation
