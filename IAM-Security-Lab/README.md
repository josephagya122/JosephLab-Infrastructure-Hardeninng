# Lab: Identity & Access Management (IAM) Hardening
## Environment: josephlab.local (Windows Server 2019)

### 1. Executive Summary
The goal of this lab was to transition a standard Active Directory environment from a "Default-Open" posture to a "Secured-Access" posture. I implemented a **Deny-by-Default** strategy for laboratory users to minimize the attack surface of the domain controller.

### 2. Technical Objectives
* **Organizational Unit (OU) Optimization**: Moving objects to align with administrative boundaries.
* **Temporal Access Control**: Configuring logon hour restrictions via PowerShell and GUI.
* **Security Auditing**: Performing a port-level audit to verify a hardened state.

### 3. Implementation: Temporal Access Control
To enforce the **Principle of Least Privilege**, the `AutomationTest` account was restricted to standard business hours.

**Steps Taken:**
1. **Initial State:** User was configured with 0 allowed logon hours (Deny All).
2. **Configuration:** Modified the `logonHours` attribute to permit access only between **Monday - Friday (08:00 - 18:00)**.
3. **Validation:** Verified the change in the Active Directory Users and Computers (ADUC) interface.

![Logon Hours Configuration](./logon-hours-grid.png)

### 4. Security Audit: Port Analysis
I performed a host-based audit to ensure only required services were listening on the network.

**Command Used:**
`Get-NetTCPConnection -State Listen | Select-Object LocalPort, OwningProcess`

**Findings:**
Confirmed critical services such as **DNS (53)**, **Kerberos (88)**, and **LDAP (389)** are active, while unauthorized ports remain closed.

![Port Audit Results](./port-audit.png)
