# Lab: Enterprise Automation via Group Policy (GPO)
## Focus: Automated Network Drive Mapping & Resource Provisioning

### 1. Objective
In a large-scale enterprise environment, manually mapping network drives for hundreds of users is inefficient and prone to error. This lab demonstrates the implementation of **Group Policy Objects (GPOs)** to automate the mapping of sensitive departmental shares (specifically the "Manager-Vault") to authorized users upon logon.

### 2. Technical Configuration
I utilized the **Group Policy Management Console (GPMC)** on Windows Server 2019 to create a standardized "Drive Map" policy.

*   **GPO Name:** `GPO_Map_Manager_Drive`
*   **Targeting:** Linked to the `Lab_Users` Organizational Unit (OU).
*   **Path:** `User Configuration > Preferences > Windows Settings > Drive Maps`
*   **Configuration Parameters:**
    *   **Action:** `Update` (Ensures persistence and refreshes the connection).
    *   **Remote Path:** `\\DC-Server-2-19\Manager-Vault$`
    *   **Drive Letter:** `Z:`
    *   **Label:** `Company Files`

### 3. Scalability & Efficiency
By using GPO Preferences instead of traditional logon scripts, I ensured:
1.  **Reduced Logon Times:** Preferences are processed faster than complex scripts.
2.  **Centralized Management:** Any change to the server path can be updated in one location and pushed to all users instantly.
3.  **User Experience:** Managers have immediate, consistent access to their files without needing technical assistance.

### 4. Verification & Proof of Work
The policy was verified on a **Windows 10 Client** workstation joined to the `josephlab.local` domain. 

*   **Login Identity:** `AutoTest` (Member of Manager Group)
*   **Verification Command:** `gpresult /r` (Confirmed GPO was applied).
*   **Visual Confirmation:** The screenshot below shows the successful mapping of the **Z: Drive** under "Network Locations" in File Explorer.

![Automated Z-Drive Mapping Success](./z-drive-verification.png)
