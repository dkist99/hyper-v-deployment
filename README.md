# Hyper-V Deployment and Virtual Machine Configuration

---

## 📖 Project Summary

This project demonstrates how to install and configure the Hyper-V role on Windows Server and deploy a virtual machine using both GUI and PowerShell methods.

This lab simulates real-world system administration tasks related to virtualization and infrastructure setup.
 
- **Languages Used:** PowerShell  
- **Environment:** Windows Server 2022  
- **Technologies:** Hyper-V, Virtual Machines, Virtual Switch Manager  

---

## 🧰 Prerequisites / Setup Requirements

Before beginning, ensure the following:

- A system running Windows Server 2022  
- Administrator privileges  
- CPU virtualization enabled in BIOS (Intel VT-x or AMD-V)  
- At least:
  - 8 GB RAM (recommended)
  - 50+ GB free disk space  
- Installation ISO for guest OS (optional but recommended)

---

## ⚙️ Demonstration & Setup Steps

### Step 1: Verify Environment

Confirm you are logged into a Windows Server system and have administrative access.

![Server Manager](images/step1-server-manager.png)

---

### Step 2: Install Hyper-V Role

1. Open **Server Manager**
2. Click **Add Roles and Features**
3. Select **Role-based or feature-based installation**
4. Choose your server
5. Select **Hyper-V**
6. Complete the wizard and restart the server

![Install Hyper-V](images/step2-install-hyperv.png)

Alternatively, install Hyper-V using PowerShell:

```powershell
Install-WindowsFeature -Name Hyper-V -IncludeManagementTools -Restart
```
---

### Step 4: Open Hyper-V Manager
After reboot:
1. Open **Server Manager**
2. Go to **Tools → Hyper-V Manager**
3. Confirm your server is listed

![Install Hyper-V](images/step2-install-hyperv.png)

---

### Step 5: Create Virtual Switch (Networking Setup)
A virtual switch allows virtual machines to communicate on the network.

1. In Hyper-V Manager, click **Virtual Switch Manager**
2. Select **External**
3. Choose your **network adapter**
4. Enable **Allow management OS to share this adapter**
5. Click **Apply**
   
![Install Hyper-V](images/step2-install-hyperv.png)

PowerShell Method:
```powershell
New-VMSwitch -Name "ExternalSwitch" -NetAdapterName "Ethernet" -AllowManagementOS $true
```

---

### Step 6: Create Virtual Machine

1. In Hyper-V Manager, click **New → Virtual Machine**
2. Enter **VM name**
3. Assign **memory**
4. Select **virtual switch**
5. Create **virtual hard disk**
6. Attach **ISO (optional)**
7. Finish wizard
   
![Install Hyper-V](images/step2-install-hyperv.png)

PowerShell Method:
```powershell
New-VM -Name "TestVM" `
-MemoryStartupBytes 2GB `
-Generation 2 `
-NewVHDPath "C:\VMs\TestVM.vhdx" `
-NewVHDSizeBytes 40GB `
-SwitchName "ExternalSwitch"
```
---

### Step 7: Verify Virtual Machine Creation
Confirm the VM appears in Hyper-V Manager and is in an **Off** state.
   
![Install Hyper-V](images/step2-install-hyperv.png)

PowerShell Method:
```powershell
New-VMSwitch -Name "ExternalSwitch" -NetAdapterName "Ethernet" -AllowManagementOS $true
```
---

### Step 8: Start Virtual Machine
Right-click VM → Click **Start**

![Install Hyper-V](images/step2-install-hyperv.png)

PowerShell Method:
```powershell
Start-VM -Name "TestVM"
```
---

### Step 9: Connect to Virtual Machine

1. Right-click VM → **Connect**
2. Proceed with **OS installation** if ISO is attached
   
![Install Hyper-V](images/step2-install-hyperv.png)

---

### Step 10: Verify VM Status via PowerShell
This command confirms the VM is running successfully.

```powershell
Get-VM
```
---
