# Active Directory OU Structure Diagram

## Purpose

This document shows a professional Active Directory Organizational Unit structure for an IT support lab. Instead of using one large diagram that becomes too small on GitHub, this version separates the design into smaller readable diagrams.

---

# 1. High-Level Active Directory Structure

```mermaid
flowchart TB
    A["corp.example.local<br/>Active Directory Domain"]

    A --> B["OU=Users<br/>Employee user accounts"]
    A --> C["OU=Computers<br/>Workstations and servers"]
    A --> D["OU=Groups<br/>Security and distribution groups"]
    A --> E["OU=Admin Accounts<br/>Privileged accounts"]
    A --> F["OU=Service Accounts<br/>System and application accounts"]
    A --> G["OU=Disabled Objects<br/>Former users and retired devices"]

    classDef domain fill:#111827,stroke:#030712,color:#ffffff,stroke-width:2px;
    classDef ou fill:#dbeafe,stroke:#2563eb,color:#111827,stroke-width:1px;

    class A domain;
    class B,C,D,E,F,G ou;
```

## What This Shows

This high-level structure separates users, computers, groups, admin accounts, service accounts, and disabled objects. This makes Active Directory easier to manage, troubleshoot, and document.

---

# 2. Users OU Structure

```mermaid
flowchart TB
    U["OU=Users<br/>Employee Accounts"]

    U --> U1["OU=Administration<br/>Administrative staff"]
    U --> U2["OU=Finance<br/>Finance users"]
    U --> U3["OU=Human Resources<br/>HR users"]
    U --> U4["OU=IT<br/>IT support and technical users"]
    U --> U5["OU=Operations<br/>Operations users"]
    U --> U6["OU=Sales<br/>Sales users"]

    classDef parent fill:#1f2937,stroke:#111827,color:#ffffff,stroke-width:2px;
    classDef department fill:#dcfce7,stroke:#16a34a,color:#111827,stroke-width:1px;

    class U parent;
    class U1,U2,U3,U4,U5,U6 department;
```

## Support Use Cases

| Scenario               | OU Location                   |
| ---------------------- | ----------------------------- |
| New finance employee   | `OU=Users/OU=Finance`         |
| New IT support user    | `OU=Users/OU=IT`              |
| HR employee account    | `OU=Users/OU=Human Resources` |
| Sales employee account | `OU=Users/OU=Sales`           |

---

# 3. Computers OU Structure

```mermaid
flowchart TB
    C["OU=Computers<br/>Domain-Joined Devices"]

    C --> C1["OU=Desktops<br/>Office desktop computers"]
    C --> C2["OU=Laptops<br/>Assigned user laptops"]
    C --> C3["OU=Shared Workstations<br/>Front desk and shared PCs"]
    C --> C4["OU=Servers<br/>Windows servers"]
    C --> C5["OU=Test Devices<br/>Lab and testing machines"]

    classDef parent fill:#1f2937,stroke:#111827,color:#ffffff,stroke-width:2px;
    classDef device fill:#fef3c7,stroke:#d97706,color:#111827,stroke-width:1px;

    class C parent;
    class C1,C2,C3,C4,C5 device;
```

## Support Use Cases

| Scenario             | OU Location                           |
| -------------------- | ------------------------------------- |
| New staff laptop     | `OU=Computers/OU=Laptops`             |
| Office desktop       | `OU=Computers/OU=Desktops`            |
| Shared front desk PC | `OU=Computers/OU=Shared Workstations` |
| Lab testing device   | `OU=Computers/OU=Test Devices`        |

---

# 4. Groups OU Structure

```mermaid
flowchart TB
    G["OU=Groups<br/>Access and Communication Groups"]

    G --> G1["OU=Security Groups<br/>Folder and resource access"]
    G --> G2["OU=Distribution Groups<br/>Email distribution lists"]
    G --> G3["OU=Application Groups<br/>Software and application access"]
    G --> G4["OU=VPN Groups<br/>Remote access permissions"]

    classDef parent fill:#1f2937,stroke:#111827,color:#ffffff,stroke-width:2px;
    classDef group fill:#ede9fe,stroke:#7c3aed,color:#111827,stroke-width:1px;

    class G parent;
    class G1,G2,G3,G4 group;
```

## Support Use Cases

| Scenario                   | OU Location                        |
| -------------------------- | ---------------------------------- |
| Shared folder access       | `OU=Groups/OU=Security Groups`     |
| Department email list      | `OU=Groups/OU=Distribution Groups` |
| Application access request | `OU=Groups/OU=Application Groups`  |
| VPN access request         | `OU=Groups/OU=VPN Groups`          |

---

# 5. Admin, Service, and Disabled Account Structure

```mermaid
flowchart TB
    A["Privileged and Special Account Management"]

    A --> ADM["OU=Admin Accounts<br/>Privileged access"]
    A --> SVC["OU=Service Accounts<br/>System accounts"]
    A --> DIS["OU=Disabled Objects<br/>Inactive accounts and devices"]

    ADM --> ADM1["OU=Help Desk Admins<br/>Delegated support permissions"]
    ADM --> ADM2["OU=Server Admins<br/>Server administration access"]
    ADM --> ADM3["OU=Domain Admins<br/>Restricted privileged accounts"]

    SVC --> SVC1["svc-backup<br/>Backup service account"]
    SVC --> SVC2["svc-print<br/>Print service account"]
    SVC --> SVC3["svc-monitoring<br/>Monitoring service account"]

    DIS --> DIS1["OU=Disabled Users<br/>Former employee accounts"]
    DIS --> DIS2["OU=Disabled Computers<br/>Retired computer objects"]
    DIS --> DIS3["OU=Pending Review<br/>Objects awaiting cleanup"]

    classDef parent fill:#1f2937,stroke:#111827,color:#ffffff,stroke-width:2px;
    classDef admin fill:#fee2e2,stroke:#dc2626,color:#111827,stroke-width:1px;
    classDef service fill:#fce7f3,stroke:#db2777,color:#111827,stroke-width:1px;
    classDef disabled fill:#e5e7eb,stroke:#4b5563,color:#111827,stroke-width:1px;

    class A parent;
    class ADM,ADM1,ADM2,ADM3 admin;
    class SVC,SVC1,SVC2,SVC3 service;
    class DIS,DIS1,DIS2,DIS3 disabled;
```

## Support Use Cases

| Scenario                  | Recommended Location                        |
| ------------------------- | ------------------------------------------- |
| Help desk delegated admin | `OU=Admin Accounts/OU=Help Desk Admins`     |
| Backup service account    | `OU=Service Accounts`                       |
| Departed employee         | `OU=Disabled Objects/OU=Disabled Users`     |
| Retired workstation       | `OU=Disabled Objects/OU=Disabled Computers` |
| Account pending review    | `OU=Disabled Objects/OU=Pending Review`     |

---

# Why This Structure Is Professional

This OU structure is useful because it separates different account and device types. It also supports better onboarding, offboarding, access control, security review, and help desk troubleshooting.

## Best Practices Demonstrated

* Keep standard user accounts separate from admin accounts.
* Keep service accounts separate from employee accounts.
* Organize users by department.
* Organize computers by device type.
* Use groups for permissions and access control.
* Move disabled users and retired devices into a separate OU.
* Document account changes in a ticket.
* Follow least privilege for admin access.

## Portfolio Note

This diagram is part of an Active Directory and Windows Server lab designed to demonstrate IT Support, Service Desk, Desktop Support, and Junior Systems Administrator documentation skills.

## Disclaimer

This is a sample lab diagram for learning and portfolio purposes. Real organizations may use different OU naming standards, Group Policy designs, security models, and administrative procedures.
