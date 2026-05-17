# Hyper-V Deployment and Virtual Machine Configuration

## 📌 Project Title
Hyper-V Deployment and Virtual Machine Configuration on Windows Server 2022

---

## 📖 Project Summary

This project demonstrates how to install and configure the Hyper-V role on Windows Server and deploy a virtual machine using both GUI and PowerShell methods.

This lab simulates real-world system administration tasks related to virtualization and infrastructure setup.

- **Languages Used:** PowerShell  
- **Environment:** Windows Server 2022  
- **Technologies:** Hyper-V, Virtual Machines, Virtual Switch Manager  

---

## ⚙️ Demonstration

### Step 1: Initial Server Environment

This is the baseline Windows Server environment before Hyper-V installation.

![Server Manager](images/step1-server-manager.png)

---

### Step 2: Install Hyper-V Role (GUI)

Using Server Manager, the Hyper-V role is installed through the Add Roles and Features Wizard.

![Install Hyper-V](images/step2-install-hyperv.png)

---

### Step 3: Install Hyper-V Role (PowerShell)

Hyper-V can also be installed using PowerShell:

```powershell
Install-WindowsFeature -Name Hyper-V -IncludeManagementTools -Restart
