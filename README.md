# Hyper-V Deployment and Virtual Machine Configuration

## 📌 Project Title
Hyper-V Deployment and Virtual Machine Configuration on Windows Server 2022

---

## 📖 Project Summary

This project demonstrates how to install and configure the Hyper-V role on Windows Server and deploy a virtual machine using both GUI and PowerShell methods.

This lab simulates real-world system administration tasks related to virtualization and infrastructure setup.

- **Project Type:** Technical walkthrough / implementation lab  
- **Languages Used:** PowerShell  
- **Environment:** Windows Server 2022  
- **Technologies:** Hyper-V, Virtual Machines, Virtual Switch Manager  

---

## 🖼️ Media

### Step 1: Initial Server Environment
![Server Manager](images/step1-server-manager.png)

### Step 2: Installing Hyper-V (GUI)
![Install Hyper-V](images/step2-install-hyperv.png)

### Step 3: Installing Hyper-V (PowerShell)
![PowerShell Install](images/step3-powershell-install.png)

### Step 4: Hyper-V Manager
![Hyper-V Manager](images/step4-hyperv-manager.png)

### Step 5: Virtual Switch Configuration
![Virtual Switch](images/step5-virtual-switch.png)

### Step 6: Creating a Virtual Machine
![Create VM](images/step6-create-vm.png)

### Step 7: VM Created
![VM Created](images/step7-vm-created.png)

### Step 8: Running Virtual Machine
![VM Running](images/step8-vm-running.png)

### Step 9: Virtual Machine Desktop
![VM Desktop](images/step9-vm-desktop.png)

---

## ⚙️ Demonstration

### Step 1: Install Hyper-V Role (PowerShell)

```powershell
Install-WindowsFeature -Name Hyper-V -IncludeManagementTools -Restart
