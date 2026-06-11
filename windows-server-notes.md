# Windows Server Notes

## Overview

This document contains beginner-friendly Windows Server notes for IT support, help desk, desktop support, and junior system administrator practice.

Windows Server is commonly used to manage users, computers, permissions, file sharing, authentication, policies, and business network services.

## Common Windows Server Roles

| Role | Purpose |
|---|---|
| Active Directory Domain Services | Manages users, computers, groups, and authentication |
| DNS Server | Resolves names to IP addresses |
| DHCP Server | Assigns IP addresses to devices automatically |
| File and Storage Services | Hosts shared folders and file permissions |
| Print Services | Manages shared printers |
| Group Policy Management | Applies settings to users and computers |

## Active Directory Domain Services

Active Directory Domain Services, also called AD DS, is used to manage domain users, computers, groups, and access.

Common Active Directory tasks include:

- Creating user accounts
- Resetting passwords
- Unlocking accounts
- Disabling accounts
- Creating security groups
- Adding users to groups
- Moving users between Organizational Units
- Joining computers to the domain

## Organizational Units

Organizational Units, or OUs, help organize Active Directory objects.

Example OU structure:

```text
company.local
├── Users
│   ├── HR
│   ├── Sales
│   └── IT
├── Computers
│   ├── Desktops
│   └── Laptops
└── Servers
```

OUs are useful because Group Policy settings can be applied to them.

## Domain Controller

A domain controller is a server that authenticates users and manages domain resources.

A domain controller can handle:

- User sign-in
- Password validation
- Group membership
- Group Policy application
- Directory services

## DNS Basics

DNS stands for Domain Name System. It helps computers find resources by name instead of IP address.

Example:

```text
fileserver01.company.local -> 192.168.1.20
```

Common DNS troubleshooting commands:

```cmd
ipconfig /all
nslookup fileserver01
ping fileserver01
```

## DHCP Basics

DHCP stands for Dynamic Host Configuration Protocol. It automatically gives network devices IP addresses.

DHCP can provide:

- IP address
- Subnet mask
- Default gateway
- DNS server address

Common DHCP troubleshooting commands:

```cmd
ipconfig /release
ipconfig /renew
ipconfig /all
```

## File Server Basics

A file server stores shared folders that users access over the network.

Example share path:

```text
\\FileServer01\Sales
```

Access is usually managed using:

- Share permissions
- NTFS permissions
- Active Directory security groups

## Group Policy Basics

Group Policy allows administrators to apply settings to users and computers.

Examples:

- Password policy
- Drive mappings
- Desktop restrictions
- Printer deployment
- Security settings
- Windows Update settings

Group Policy is managed using:

```text
Group Policy Management Console
```

## Common Windows Server Tools

| Tool | Purpose |
|---|---|
| Server Manager | Manage server roles and features |
| Active Directory Users and Computers | Manage users, groups, and computers |
| Group Policy Management | Manage Group Policy Objects |
| Event Viewer | Review system and application logs |
| Services | Start, stop, and review services |
| Computer Management | Manage disks, users, shares, and events |
| DNS Manager | Manage DNS zones and records |
| DHCP Manager | Manage DHCP scopes and leases |

## Useful Commands

### Check IP Configuration

```cmd
ipconfig /all
```

### Test Network Connectivity

```cmd
ping 8.8.8.8
ping fileserver01
```

### Test DNS Resolution

```cmd
nslookup google.com
nslookup fileserver01
```

### View Current User

```cmd
whoami
```

### View User Groups

```cmd
whoami /groups
```

### Force Group Policy Update

```cmd
gpupdate /force
```

### View Applied Group Policy

```cmd
gpresult /r
```

## Common Support Scenarios

| Scenario | Possible Check |
|---|---|
| User cannot sign in | Check account status and password |
| User cannot access shared folder | Check security group membership |
| Computer cannot join domain | Check DNS and network connectivity |
| Group Policy not applying | Run `gpupdate /force` and `gpresult /r` |
| Printer not available | Check printer mapping or print server |
| User gets access denied | Review NTFS and share permissions |
| Device has no network access | Check IP address, gateway, and DNS |

## Basic Troubleshooting Process

A simple troubleshooting process:

1. Identify the issue.
2. Confirm the affected user or device.
3. Check recent changes.
4. Reproduce the problem, if possible.
5. Review account, network, and permission settings.
6. Test a fix.
7. Confirm with the user.
8. Document the result.

## Best Practices

- Use clear naming standards.
- Document all changes.
- Follow least privilege access.
- Use groups instead of direct user permissions.
- Keep servers updated.
- Review event logs when troubleshooting.
- Test changes before closing tickets.
- Escalate when the issue affects multiple users or critical systems.

## Skills Demonstrated

- Windows Server fundamentals
- Active Directory basics
- DNS and DHCP awareness
- File server support
- Group Policy basics
- Troubleshooting commands
- IT support documentation
