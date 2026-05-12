# Lab: Privileged Access & Data Isolation (Manager-Vault)
## Focus: Secure File Shares and Restricted Admin Access

### 1. Objective
The goal of this lab was to implement a secure, restricted storage environment known as the **"Manager-Vault."** This lab demonstrates the ability to configure granular access controls where only authorized administrative and managerial identities can access sensitive data.

### 2. Architecture of the "Manager-Vault"
I created a dedicated directory structure on the Windows Server 2019 Domain Controller to simulate a high-security storage tier.
* **Storage Path:** `C:\Manager_Vault`
* **Network Share:** `\\DC-Server-2-19\Manager-Vault$` (Hidden Share)

### 3. Implementing the "Admin-Only" Posture
To secure the vault, I moved away from "Inherited Permissions" and applied explicit **NTFS Security Descriptors**:

* **Access Granted:** * `Domain Admins`: Full Control
    * `Manager_Group`: Read/Write/Modify
* **Access Denied:** * `Authenticated Users`: No access (Removed from ACL)
    * `Everyone`: No access (Removed from ACL)

### 4. Verification & Testing
To ensure the security posture was effective, I performed the following validation:
1. **Admin Verification:** Logged in as a Domain Admin and confirmed full read/write access to the vault.
2. **Standard User Restriction:** Logged in as the `AutomationTest` user and attempted to browse to the vault. 
3. **Result:** Access was explicitly denied with a "Windows cannot access" error, confirming the isolation was successful.

![Manager Vault Security Settings](./vault-permissions.png)
![Access Denied Verification](./access-denied.png)
