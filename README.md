# Hyper-V Deployment and Virtual Machine Configuration

---

## 📖 Project Summary

This project demonstrates how to install and configure the Hyper-V role on Windows 11 Pro and deploy a virtual machine using both GUI and PowerShell methods.

This lab simulates real-world system administration tasks related to virtualization and infrastructure setup.
 
- **Languages Used:** PowerShell  
- **Environment:** Windows 11 
- **Technologies:** Hyper-V, Virtual Machines, Virtual Switch Manager  

---

## 🧰 Prerequisites / Setup Requirements

Before beginning, ensure the following:

- A system running Windows 11 Pro
- Administrator privileges  
- CPU virtualization enabled in BIOS (Intel VT-x or AMD-V)  
- At least:
  - 8 GB RAM (recommended)
  - 50+ GB free disk space  
- Installation ISO for guest OS (optional but recommended)

---

## ⚙️ Demonstration & Setup Steps

### Step 1: Install Hyper-V

1. Open **Control Panel**
2. Click **Programs**
3. Select **Turn Windows features on or off**
5. Select **Hyper-V**
6. Click **OK** and complete installation
7. **Restart** the machine 

![Install Hyper-V](images/step2-install-hyperv.png)

Alternatively, install Hyper-V using PowerShell:

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
```
---

### Step 2: Open Hyper-V Manager
After reboot:
1. Open **Hyper-V Manager**
2. Confirm your machine is listed

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
