### 2. User Creation: Manual vs. Automation
To demonstrate technical versatility, I executed user onboarding using two distinct methodologies:

#### Method A: Manual GUI Configuration
* **Tool:** Active Directory Users and Computers (ADUC)
* **Process:** Manually defined account attributes, password policies, and OU placement.
* **Outcome:** Verified the standard "Help Desk" workflow for single-user onboarding.

#### Method B: PowerShell Automation (Scalable Approach)
* **Tool:** PowerShell / Active Directory Module
* **Process:** Developed a script to automate the creation of the `AutomationTest` account.
* **Key Command:** `New-ADUser -Name "AutomationTest" -Path "OU=Lab_Users,DC=josephlab,DC=local" -Enabled $true`
* **Outcome:** Demonstrated the ability to perform bulk operations, reducing human error and increasing efficiency.

![PowerShell Script Success](./powershell-creation.png)
