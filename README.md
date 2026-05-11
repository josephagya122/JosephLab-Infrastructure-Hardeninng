# JosephLab-Infrastructure-Hardeninng
VBox Guest Additions iso in virtual machines
# JosephLab: Infrastructure Configuration
## Project: VirtualBox Guest Additions Implementation

### 1. Overview
This project documents the successful configuration of Guest Additions on a Windows Server 2019 Domain Controller (DC-Server-2-19). This was a critical step in establishing a functional SOHO network lab for CCNA and Defensive Security studies.

### 2. The Problem
Without Guest Additions, the virtual environment lacked:
* Full-screen resolution (difficult to manage Active Directory).
* Bidirectional Clipboard (unable to paste PowerShell scripts from the host).
* Proper driver support for integrated hardware.

### 3. Step-by-Step Configuration

#### Part A: Mounting the ISO (The "Hardware" Logic)
1. Shutdown the **DC-Server-2-19** VM.
2. Open **VirtualBox Manager** > **Settings** > **Storage**.
3. Under the **Controller: IDE**, click the Empty Optical Drive icon.
4. Click the blue disk icon and select **"Choose a disk file..."**
5. Locate the `VBoxGuestAdditions.iso` (usually in `C:\Program Files\Oracle\VirtualBox`).

#### Part B: The Installation (The "OS" Logic)
1. Start the VM and log in as **Administrator**.
2. Open **File Explorer** and go to **This PC**.
3. Double-click **CD Drive (D:) VirtualBox Guest Additions**.
4. Right-click `VBoxWindowsAdditions-amd64` and select **Run as Administrator**.
5. Click **Next** through the prompts and select **Install**.
6. **Important:** Select "Reboot Now" to finalize the driver installation.

### 4. Results
* **Resolution:** Scaled to 1920x1080 successfully.
* **Clipboard:** Verified by copying scripts from the HP Pavilion host to the VM.
* **Performance:** Noticed significant reduction in mouse lag.

---
**Author:** Joseph  
**Focus:** Networking Student | Entry-Level IT Support
