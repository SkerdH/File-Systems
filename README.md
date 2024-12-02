# Secure Windows File System with Automated Permissions Management

## **Project Objective**
The goal of this project is to implement security measures on a Windows file system, configure NTFS permissions, use PowerShell for automation, and ensure compliance with industry standards for data security.

---

## **Table of Contents**
1. [Set Up the Windows Environment](#1-set-up-the-windows-environment)
2. [Understand and Implement NTFS Permissions](#2-understand-and-implement-ntfs-permissions)
3. [Simulate Varonis-like Functionality](#3-simulate-varonis-like-functionality)
4. [Automate Permissions Management with PowerShell](#4-automate-permissions-management-with-powershell)
5. [Implement Data Transfer Security](#5-implement-data-transfer-security)
6. [Documentation and Compliance Checks](#6-documentation-and-compliance-checks)
7. [Reporting and Automation](#7-reporting-and-automation)
8. [Final Testing and Review](#8-final-testing-and-review)

---

## **1. Set Up the Windows Environment**

### **Objective**
Create a test environment that mirrors a corporate setup.

### **Steps**
1. Install Windows Server or Windows 10 on a Virtual Machine (VM) using tools like VMware or VirtualBox.
2. Create test users with different roles:
   - **Admin**
   - **Read-Only**
   - **Manager**
<img src="https://i.imgur.com/0vEZPN7.jpg" alt="Alt Text" width="500" />
3. Set up folder structures to demonstrate permission management:
   ```plaintext
   C:\Company\Public
   C:\Company\Finance
   C:\Company\HR
   ```
---

## **2. Understand and Implement NTFS Permissions**

### **Objective**
Demonstrate the management of NTFS file system security.

### **Steps**
1. Assign NTFS permissions for the folders:
   - **Admin**: Full Control
   - **Managers**: Modify permissions
   - **Employees**: Read-only access
2. Use File Explorer or Command Prompt to configure permissions:
   ```bash
   icacls "C:\Company\Finance" /grant Managers:(M)
   ```
<img src="https://i.imgur.com/Z8AMiuB.jpg" alt="Alt Text" width="500"/>
3. Test permissions by logging in as different users and verifying access levels.

---

## **3. Simulate Varonis-like Functionality**

### **Objective**
Simulate monitoring and reporting on file access using Windows built-in tools.

### **Steps**
1. Enable file auditing in the **Group Policy Editor**:
   ```
   Computer Configuration > Windows Settings > Security Settings > Advanced Audit Policy Configuration > Audit File System
   ```
<img src="https://i.imgur.com/FYEGXj1.jpg"  alt="Alt Text" width="500"/>
2. Configure auditing on sensitive folders:
   - Right-click the folder > Properties > Security > Advanced > Auditing.
   - Add users/groups and specify events to monitor.
<img src="https://i.imgur.com/UY2d8tC.jpg"  alt="Alt Text" width="500"/>
3. View logs in **Event Viewer**:
   - Navigate to `Security Logs` to review file access and permission changes.
<img src="https://i.imgur.com/PtASKYA.jpg"  alt="Alt Text" width="500"/>
---

## **4. Automate Permissions Management with PowerShell**

### **Objective**
Automate NTFS permissions management using PowerShell.

### **Example PowerShell Script**
```powershell
# Define folder path and user group
$folderPath = "C:\Company\Finance"
$userGroup = "Managers"

# Set permissions
Invoke-Expression "icacls `"$folderPath`" /grant `"$userGroup`:(M)`"

# Check and report permissions
icacls $folderPath
```
<img src="https://i.imgur.com/yqB2Nv5.jpg"  alt="Alt Text" width="500"/>
### **Steps**
1. Save and execute the script to assign and verify permissions.
2. Automate user group creation and folder permission assignment.

---

## **5. Implement Data Transfer Security**

### **Objective**
Demonstrate secure data transfer between systems.

### **Steps**
1. **Set up a VPN**:
   - Use Windows built-in VPN server or tools like OpenVPN.
2. **Encrypt files** using BitLocker or EFS:
   - Right-click folder > Properties > Advanced > Enable encryption.
3. Automate encryption with PowerShell:
   ```powershell
   $folderPath = "C:\Company\Sensitive"
   Add-EncryptionKey -Path $folderPath
   ```
4. Test encrypted file transfers and ensure successful decryption.

---

## **6. Documentation and Compliance Checks**

### **Objective**
Document configurations and ensure compliance with security standards.

### **Steps**
1. Document folder permissions, PowerShell scripts, and auditing setup.
2. Create a compliance checklist:
   - Are sensitive folders audited?
   - Are file permissions aligned with RBAC?
   - Is data transfer encrypted?

---

## **7. Reporting and Automation**

### **Objective**
Automate reporting for auditing and monitoring file access.

### **Example PowerShell Script**
```powershell
# Get and export audit logs
Get-WinEvent -LogName "Security" | Where-Object { $_.Message -like "*File Access*" } | Export-Csv "C:\reports\file_access_report.csv"
```
<img src="https://i.imgur.com/aDNw58X.jpg"  alt="Alt Text" width="500"/>
### **Steps**
1. Generate file access and permission change reports.
2. Include summary reports in your documentation.

---

## **8. Final Testing and Review**

### **Objective**
Ensure the system is functioning as expected.

### **Steps**
1. Test each feature:
   - Permissions
   - Encryption
   - Monitoring
   - Reporting
2. Verify compliance with simulated company policies.
3. Optimize and review all PowerShell scripts.

---

## **Project Outcome**
By completing this project, you will:
- Gain hands-on experience with NTFS permissions, PowerShell automation, and security measures.
- Demonstrate the ability to secure Windows file systems, manage permissions, and ensure compliance with data protection regulations.
- Showcase your expertise in working with security tools, audit logs, and automated solutions.

---


