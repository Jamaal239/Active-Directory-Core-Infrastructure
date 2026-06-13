# Automated and Manual Deployment of an Active Directory (AD DS) Infrastructure

## 📋 Project Overview
The objective of this project was to design, deploy, and configure a secure Active Directory Domain Services (AD DS) environment using Windows Server 2025 within a virtualized sandbox. This project simulates setting up a centralized enterprise Domain Controller, establishing a baseline network domain (`mydomain.local`), implementing core directory hierarchical structures, and managing user profiles alongside security groups.

### 🎯 Key Skills Demonstrated
* **Windows Server Administration:** Installation and management of Windows Server roles, dependencies, and core system features.
* **Network Infrastructure Configuration:** Implementation of static IPv4 networking schemes and local DNS loopback configurations (`127.0.0.1`) to reliably anchor directory services.
* **Identity & Access Management (IAM):** Structural design of Organizational Units (OUs), onboarding provisioned user profiles, and managing administrative security group memberships.

---

## 🏗️ Phase 1: Virtual Environment Setup & Local Server Configuration

### Steps 1-5: Hypervisor Provisioning & OS Setup
Configured a new virtual machine instance within Oracle VirtualBox, allocating baseline system memory and CPU core resources tailored for Windows Server performance parameters. The Windows Server Evaluation ISO installation media was mapped to the virtual storage controller to initiate the deployment phase. Selected the **Windows Server Standard Evaluation (Desktop Experience)** edition to ensure full access to the graphical user interface (GUI).

<details>
<summary>📸 View Phase 1 Setup Screenshots (Steps 1-5)</summary>

#### Step 1: Virtual Machine Container Creation
![Step 1: Creating the Virtual Machine Container](screenshots/screenshot_01.png)

#### Step 2: Allocating Virtual Storage Space
![Step 2: Allocating Virtual Storage Space](screenshots/screenshot_02.png)

#### Step 3: Mounting Installation Media
![Step 3: Mounting the Operating System Installation Media](screenshots/screenshot_03.png)

#### Step 4: Initiating Windows Server Installer
![Step 4: Initiating the Windows Server Installer](screenshots/screenshot_04.png)

#### Step 5: Selecting Operating System Edition
![Step 5: Selecting the Operating System Edition](screenshots/screenshot_05.png)
</details>

### Steps 6-13: Clean OS Installation & Guest Integration
Executed a clean custom OS installation by partitioning unallocated virtual storage space. Following the system file copy phase, the root security layer was established by assigning a hardened administrative password to the built-in local Administrator account. Post-installation, VirtualBox Guest Additions were integrated to enable advanced display scaling and optimized device driver baselines.

<details>
<summary>📸 View Phase 1 Installation Screenshots (Steps 6-13)</summary>

#### Step 6: Accepting Licensing Agreements
![Step 6: Accepting Licensing Agreements](screenshots/screenshot_06.png)

#### Step 7: Custom OS Installation Execution
![Step 7: Executing a Clean Custom OS Installation](screenshots/screenshot_07.png)

#### Step 8: Finalizing Windows File Copy Phase
![Step 8: Finalizing the Windows File Copy Phase](screenshots/screenshot_08.png)

#### Step 9: Creating Local Administrator Account
![Step 9: Creating the Local Administrator Account](screenshots/screenshot_09.png)

#### Step 10: Accessing Windows Server Desktop Environment
![Step 10: Accessing the Windows Server Desktop Environment](screenshots/screenshot_10.png)

#### Step 11: Locating Network Interfaces
![Step 11: Locating Network Interfaces](screenshots/screenshot_11.png)

#### Step 12: Completing Guest Additions and Rebooting
![Step 12: Completing Guest Additions and Rebooting](screenshots/screenshot_12.png)

#### Step 13: Reviewing Server Manager Dashboard
![Step 13: Reviewing the Server Manager Dashboard](screenshots/screenshot_13.png)
</details>

---

## 🌐 Phase 2: Server Network & Hostname Standardization

### Steps 14-17: Network Configurations & Hostname Remapping
Navigated to local network hardware properties to completely isolate network behaviors. Manually assigned a persistent static IPv4 network address to the server adapter and bound the primary DNS query field to the loopback address (`127.0.0.1`), forcing local resolution—a critical prerequisite for Domain Controller promotion. Finally, modified the computer name to a standardized enterprise nomenclature: `DC-01`.

* **Static IP assigned:** `172.16.0.10`
* **Subnet Mask:** `255.255.255.0`
* **DNS Loopback Server Pointer:** `127.0.0.1`
* **Target Hostname:** `DC-01`

<details>
<summary>📸 View Phase 2 Configuration Screenshots (Steps 14-17)</summary>

#### Step 14: Locating Server Network Adapter
![Step 14: Locating the Server Network Adapter](screenshots/screenshot_14.png)

#### Step 15: Configuring Static IP and DNS Loopback
![Step 15: Configuring the Static IP and DNS Loopback Address](screenshots/screenshot_15.png)

#### Step 16: Changing Server Hostname to DC-01
![Step 16: Changing the Server Hostname](screenshots/screenshot_16.png)

#### Step 17: Confirming Active Directory Role Staging
![Step 17: Confirming Active Directory Role Installation](screenshots/screenshot_17.png)
</details>

---

## 🚀 Phase 3: Active Directory Domain Services Configuration & Promotion

### Steps 18-24: Forest Creation & Directory Schema Validation
Triggered the AD DS Configuration Wizard to establish a completely new Active Directory forest under the root domain designation `mydomain.local`. Configured integrated DNS capabilities, validated automated NetBIOS path assignments (`MYDOMAIN`), and verified database storage paths for the active **NTDS database**, **transaction logs**, and **SYSVOL folders**. After clearing the prerequisite validation scan, the server was promoted to a functional Domain Controller and rebooted to initialize the directory schema.

<details>
<summary>📸 View Phase 3 Domain Promotion Screenshots (Steps 18-24)</summary>

#### Step 18: Specifying AD Root Domain Name
![Step 18: Specifying the Active Directory Root Domain Name](screenshots/screenshot_18.png)

#### Step 19: Configuring DC Options and DSRM Password
![Step 19: Configuring Domain Controller Options and DSRM Password](screenshots/screenshot_19.png)

#### Step 20: Verifying NetBIOS Domain Name
![Step 20: Verifying the NetBIOS Domain Name](screenshots/screenshot_20.png)

#### Step 21: Verifying AD DS Database and SYSVOL Paths
![Step 21: Verifying AD DS Database and SYSVOL Paths](screenshots/screenshot_21.png)

#### Step 22: Reviewing Deployment Configurations
![Step 22: Reviewing Deployment Configurations](screenshots/screenshot_22.png)

#### Step 23: Passing Prerequisite Validation Scan
![Step 23: Passing the Prerequisite Validation Scan](screenshots/screenshot_23.png)

#### Step 24: Domain Promotion Execution & System Reboot
![Step 24: Completing Domain Promotion and Enforcing System Reboot](screenshots/screenshot_24.png)
</details>

---

## 👥 Phase 4: Post-Promotion Directory Setup & User Provisioning

### Steps 25-32: IAM Hierarchy Design & Account Privilege Elevation
Authenticated into the domain for the first time using the root domain controller account (`MYDOMAIN\Administrator`). Launched the **Active Directory Users and Computers (ADUC)** management snap-in to establish a customized administrative Organizational Unit named `_Employees` to isolate corporate users from default system accounts. Provisioned a standard corporate user profile (`jdoe`), enforced rigorous initial password criteria, and modified group attributes to append memberships to the **Domain Admins** security group to complete baseline access provisioning configurations.

<details>
<summary>📸 View Phase 4 User Provisioning Screenshots (Steps 25-32)</summary>

#### Step 25: Initial Administrative Login to Domain
![Step 25: Initial Administrative Login to the New Domain](screenshots/screenshot_25.png)

#### Step 26: Launching Active Directory Users and Computers Console
![Step 26: Launching the Active Directory Users and Computers Console](screenshots/screenshot_26.png)

#### Step 27: Establishing Custom Organizational Unit (_Employees)
![Step 27: Establishing a Custom Organizational Unit (OU)](screenshots/screenshot_27.png)

#### Step 28: Creating Standard Domain User Profile
![Step 28: Creating a Standard Domain User Profile](screenshots/screenshot_28.png)

#### Step 29: Setting User Password Security Parameters
![Step 29: Setting User Password Security Parameters](screenshots/screenshot_29.png)

#### Step 30: Verifying Successful Directory Object Provisioning
![Step 30: Verifying Successful Directory Object Provisioning](screenshots/screenshot_30.png)

#### Step 31: Elevating Account Privileges to Domain Admin
![Step 31: Elevating Account Privileges via Group Membership](screenshots/screenshot_31.png)

#### Step 32: Finalizing Core Identity Infrastructure Configurations
![Step 32: Finalizing Directory Configurations](screenshots/screenshot_32.png)
</details>
