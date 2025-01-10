# On-premises-Active-Directory-Deployed-in-the-Cloud-Azure-
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used</h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Domain Controller in Azure
- Setup Client Machine in Azure
- Install and Configure Active Directory
- Configure Users, OUs, and Group Policies

<h2>Deployment and Configuration Steps</h2>

---

### **1. Setup Domain Controller in Azure**
<p align="center">
<img src="https://imgur.com/BZ1K4nY.png" alt="Active Directory Lab Image" height="80%" width="80%">
</p>
<p align="center">
<img src="https://imgur.com/UYPBf11.png" alt="Active Directory Lab Image" height="80%" width="80%">
</p>

<p>
To begin, a resource group, virtual network, and subnet were created in Azure. A virtual machine named "DC-1" (Windows Server 2022) was provisioned with a static private IP address, and the Windows Firewall was disabled to allow connectivity for testing purposes.
</p>

---

### **2. Setup Client Machine in Azure**
<p align="center">
<img src="https://imgur.com/0Ycs7ps.png" alt="Active Directory Lab Image" height="80%" width="80%">
</p>
<p align="center">
<img src="https://imgur.com/0OPxPjP.png" alt="Active Directory Lab Image" height="80%" width="80%">
</p>

A second virtual machine, "Client-1" (Windows 10), was created in the same virtual network as DC-1. The DNS settings of Client-1 were configured to use the private IP address of DC-1, enabling communication between the two machines. Connectivity was verified using PowerShell and `ping` commands, ensuring Client-1 could communicate with DC-1.
</p>

---

### **3. Install and Configure Active Directory**
<p align="center">
<img src="https://imgur.com/cHlL2C4.png" alt="Active Directory Lab Image" height="80%" width="80%">
</p>
<p align="center">
<img src="https://imgur.com/7mTnRmX.png" alt="Active Directory Lab Image" height="80%" width="80%">
</p>

<p>
Active Directory Domain Services was installed on DC-1, and the server was promoted as a domain controller for a new forest (e.g., mydomain.com). A domain admin user, "jane_admin," was created and added to the Domain Admins security group. Client-1 was then joined to the domain, and its computer object was moved into a newly created OU named "_CLIENTS."
</p>

---

### **4. Configure Remote Desktop for Non-Administrative Users**
<p align="center">
<img src="https://imgur.com/d2CvJtP.png" alt="Active Directory Lab Image" height="80%" width="80%">
</p>

<p>
Remote Desktop access was enabled for non-administrative users on Client-1. The "domain users" group was granted access, allowing standard users to connect via Remote Desktop. This configuration demonstrates how to manage remote access for non-admin users efficiently.
</p>

---

### **5. Create Multiple Users and Manage Account Lockouts**

<p>
Using PowerShell, multiple user accounts were created within the "_EMPLOYEES" OU in Active Directory. Account lockout policies were configured to lock accounts after 5 failed login attempts. A locked account was observed and later unlocked, demonstrating effective account management within Active Directory. Additional steps included enabling and disabling accounts and observing system logs for insights into authentication events.
</p>
<p align="center">
<img src="https://imgur.com/R1CRss4.png" alt="Active Directory Lab Image" height="80%" width="80%">
</p>
<p align="center">
<img src="https://imgur.com/q9fIEwL.png" alt="Active Directory Lab Image" height="80%" width="80%">
</p>

---

<h2>Summary</h2>
This lab demonstrates the deployment and configuration of Active Directory in a cloud environment using Azure. It includes setting up a domain controller, joining a client machine to the domain, configuring Active Directory, managing user accounts, and enforcing security policies. These exercises provide foundational knowledge for managing on-premises Active Directory and preparing for cybersecurity operations.
