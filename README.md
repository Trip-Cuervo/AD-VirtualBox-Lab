# AD-VirtualBox-Lab
Guide to installing Active Directory on VirtualBox for a lab environment
# Installing Active Directory on VirtualBox for a Lab

## Overview
This guide walks you through setting up a VirtualBox virtual machine (VM) to run Windows Server with Active Directory (AD) for lab purposes. This is ideal for those preparing for certifications, learning AD administration, or testing a network environment.

---

## Prerequisites
1. **Hardware Requirements**:
   - A computer with at least:
     - 8 GB of RAM (16 GB recommended)
     - 50 GB of free disk space
   - Virtualization enabled in BIOS/UEFI.
   
2. **Software Requirements**:
   - [Oracle VirtualBox](https://www.virtualbox.org/) (latest version).
   - A Windows Server ISO file (e.g., Windows Server 2019 or 2022).
   - VirtualBox Extension Pack (optional, for USB or PXE features).

3. **Networking**:
   - Decide if the VM should use NAT, Bridged, or Internal networking based on your lab needs.

---

## Steps to Set Up Active Directory

### Step 1: Set Up the Virtual Machine
1. Open VirtualBox and click **New**.
2. Configure the VM:
   - **Name**: `AD-Lab`.
   - **Type**: Microsoft Windows.
   - **Version**: Windows Server (e.g., 2019 or 2022).
   - **Memory**: Allocate at least 4 GB (recommended: 8 GB).
   - **Hard Disk**: Create a new virtual hard disk (50 GB minimum).
3. Complete the wizard and click **Settings** for additional configuration:
   - Attach the Windows Server ISO under **Storage** > **Controller: IDE**.
   - Configure networking under **Network** (e.g., NAT or Bridged Adapter).

4. Start the VM and boot from the Windows Server ISO.

---

### Step 2: Install Windows Server
1. Follow the installation prompts:
   - Select the appropriate language and region.
   - Choose "Windows Server with Desktop Experience."
   - Partition the disk and complete the installation.
2. After installation, set a strong administrator password.

---

### Step 3: Configure Active Directory
1. **Install AD DS Role**:
   - Log in to the server and open **Server Manager**.
   - Click **Manage** > **Add Roles and Features**.
   - Select **Active Directory Domain Services** (AD DS) and follow the prompts.
   - Confirm the installation and restart if necessary.

2. **Promote the Server to a Domain Controller**:
   - In Server Manager, click the notification flag and select **Promote this server to a domain controller**.
   - Create a new forest and specify a domain name (e.g., `lab.local`).
   - Set the Forest and Domain Functional Levels (default: Windows Server 2016).
   - Configure DNS and provide a Directory Services Restore Mode (DSRM) password.
   - Complete the wizard and restart the VM.

---

## Testing the Active Directory Setup
1. Log in with domain credentials (e.g., `Administrator@lab.local`).
2. Open **Active Directory Users and Computers** to verify the domain setup.
3. Create a test user and group for further experimentation.

---

## Additional Tips
- **Snapshots**: Take a snapshot before major changes to revert easily.
- **Network Configuration**:
   - For testing multi-VM setups, configure the network adapter to **Internal Network** for AD communication.
- **Add Another VM**:
   - Set up a Windows client VM and join it to your AD domain for further practice.

---

## Troubleshooting
1. **Cannot Start the VM**:
   - Ensure virtualization is enabled in BIOS/UEFI.
   - Allocate more memory or disk space if needed.

2. **AD DS Installation Fails**:
   - Check the server's static IP and ensure DNS settings are correct.

3. **No Internet Connectivity**:
   - Configure the VirtualBox NAT adapter for internet access.

---

## Resources
- [Download VirtualBox](https://www.virtualbox.org/)
- [Windows Server ISO](https://www.microsoft.com/en-us/evalcenter/)
- [Microsoft Docs on AD DS](https://docs.microsoft.com/en-us/windows-server/identity/active-directory-domain-services)

---

## License
This guide is licensed under the MIT License. Feel free to modify and share.
