<h2>Active-Directory-Lab</h2>
Deployment and configuration of a Windows Server Active Directory environment including domain controller setup, user management, organizational units, group policies, and client domain joining.


<h2>This project demonstrates the deployment and configuration of a Windows Server Active Directory environment designed for a small business with multiple departments.
The lab simulates how an IT administrator would deploy a Domain Controller, manage users and organizational units, apply security policies, and connect client machines to the domain.</h2>


<h2>Technologies used</h2>

. Windows server

. Windows 10

. Active Directory Domain Service (AD DS)

. Group Policy Management

. VirtualBox


<h2>Lab Enviroment</h2>

Components     -        Configuration

Virtualization   -        VirtualBox

server OS         -       Windows Server 2019/2022

client OS          -      Windows 10 

Domain              -     Crepico.bh

Server IP         -       192.168.56.10

Client IP         --       192.168.56.11

<h2>Network Architecture</h2>

The environment consists of:

. 1 Domain Controller

. 1 Windows 10 client machine

. Internal network for domain communication

. NAT adapter for internet access


<h2>Step 1 - Install Windows Server</h2>

Create a new virtual machine and install windows server.

Recommended configuration:

. RAM: 4GB

. Storage: 50GB

. Adapter 1: Host only adapter/internal network

. Adapter 2: NAT

<img width="959" height="473" alt="image" src="https://github.com/user-attachments/assets/5adc0ba2-bc0d-4220-be47-6505e451a7e3" />


<img width="938" height="469" alt="image" src="https://github.com/user-attachments/assets/82e16a21-a2d5-4b84-b40e-724a575ecc9e" />

After installation:

. Rename the server to DC01 in server manager by selecting the local server option and changing the name. restart when prompted to.



<h2>Step 2 - Configure static IP address</h2>

Navigate to:

control panel -> network and sharing center -> change adapter settings.

They are two adapters, identify the host adapter (usually Ethernet 1). right click it, select properties, select ipv4, select use the following IP (to create a static IP) and set the following configurations:

. IP address: 192.168.56.10

. Subnet mask: 255.255.255.0

. Preffered DNS server: 192.168.56.10

<img width="1920" height="1080" alt="VirtualBox_Doc1_16_03_2026_14_03_02" src="https://github.com/user-attachments/assets/b36c3aba-6557-4ae8-b778-a9b6a2a13199" />


<h2>Step 3 - install active directory domain services</h2>

open server manager

select:

Add roles and features -> install active directory domain services.

after installatoin:

promote server to a domain controller

Domain name:

Crepico.bh

confirm domain and server name by clicking on local server in server manager


<img width="1920" height="892" alt="VirtualBox_Doc1_17_03_2026_11_08_29" src="https://github.com/user-attachments/assets/67fbe0ba-6430-4f5f-9d71-3fb16e617d04" />


<h2>Step 4 - Create Organizational Units (OUs)</h2>

Create department-based organizational units:

. HR

. Finance

. IT

. Sales

navigate to:

Active Directory Users and computers, in tools -> right click your Domain -> select new -> organizational unit


<img width="1920" height="892" alt="VirtualBox_Doc1_17_03_2026_11_29_59" src="https://github.com/user-attachments/assets/bccf2b32-a3e5-4f6c-b1e3-389d30090206" />


<h2>Step 5 - Create users</h2>

create users inside each department (OU):


<img width="1920" height="892" alt="VirtualBox_Doc1_17_03_2026_11_55_28" src="https://github.com/user-attachments/assets/892f5070-6d89-402b-97d6-a158b6fcb437" />


<h2>Step 6 - create security groups</h2>


create groups for each deparments and add users to the appropriate groups

. HR-Security-Group

. Finance_Group

. IT_Group

. Sales_Group


<img width="1920" height="892" alt="VirtualBox_Doc1_17_03_2026_12_11_33" src="https://github.com/user-attachments/assets/b9080032-654d-4be0-aa0a-208cc815ba3c" />


<h2>Step 7 - Configure Group Policy</h2>


Open Group Policy Management Control

Create policies such as:

<h2>Password Policy</h2>

. Enforce password complexity

. Minimum password length

<h2>Security Restrictions</h2>

. Disable USB storage

. Restrict control panel access


<img width="1920" height="892" alt="VirtualBox_Doc1_17_03_2026_12_36_00" src="https://github.com/user-attachments/assets/b822ee97-70a7-48b4-b8a1-dc0dda534a9b" />


<img width="1920" height="892" alt="VirtualBox_Doc1_17_03_2026_12_44_24" src="https://github.com/user-attachments/assets/6c16d401-574b-41db-b099-2dc8aa2e9342" />


<h2>Step 8 - Install Windows 10 Client</h2>

Create a windows 10 virtual machine.

Configuration:

. RAM: 2GB

. Network Adapter: Host only Adapter/internal Network


Assign IP settings:

. IP Address: 192.168.56.11

. DNS Server: 192.168.56.10


<img width="1024" height="768" alt="VirtualBox_windows 10 pro_17_03_2026_13_00_17" src="https://github.com/user-attachments/assets/370672e3-2cd0-4e6f-bb03-bbaa0cda4728" />


Test connectivity by pinging 192.168.56.10


<img width="1024" height="768" alt="VirtualBox_windows 10 pro_17_03_2026_13_03_54" src="https://github.com/user-attachments/assets/31174dd7-8988-4b99-870d-b6e2eeab74b1" />


<h2>Step 9 - Join Client Machine to Domain</h2>

Navigate to:

System -> Changing Settings -> Change

Join the domain:

Crepico.bh

Use Domain Administrator credentials.


Restart the computer.



<h2>Step 10 - Test Domain Login</h2>

Log into the client machine using a domain account:


<img width="1024" height="768" alt="VirtualBox_windows 10 pro_17_03_2026_13_32_45" src="https://github.com/user-attachments/assets/4f2cb553-0355-4a8b-a33f-22d43c154fdd" />


<img width="1024" height="634" alt="VirtualBox_windows 10 pro_17_03_2026_13_34_48" src="https://github.com/user-attachments/assets/9cb20204-192c-4244-a57c-b83c5916629c" />


<h2>Step 11 (final step) - Monitor Authentication Logs</h2>

Open Event Viewer 

Navigate to:

Windows Logs -> Security


Review:

. Successful Login events

. Failed login attempts


<img width="1920" height="892" alt="VirtualBox_Doc1_17_03_2026_13_42_33" src="https://github.com/user-attachments/assets/ef37a778-5574-4c19-bccf-388a73d4b0f1" />


<h2>Skills Demonstrated</h2>


. Active Directory Domain Services
. Windows Server Administration
. Organizational Unit Design
. User and Group Management
. Group Policy Configuration
. Domain Controller Deployment
. Client Machine Domain Joining
. Authentication Monitoring


<h2>Project Outcome</h2>


This project demonstrates the deployment and management of a centralized identity management system using Active Directory in a simulated business environment.
The infrastructure allows administrators to efficiently manage users, enforce security policies, and control access to network resources.


<h2>What I Learned</h2>


Through this project, I gained hands-on experience with deploying and managing a Windows-based directory service using Active Directory Domain Services.
I learned how to design and implement a structured domain environment by creating Organizational Units (OUs) to reflect real-world business departments. This improved my understanding of how to logically organize users, groups, and resources for efficient administration.
I developed practical skills in user and group management, including creating domain users, assigning them to security groups, and applying role-based access control. This helped me understand how permissions and access are managed in enterprise environments.
Using Group Policy Management Console, I configured and applied Group Policy Objects (GPOs) to enforce security settings such as password policies, restricting access to system features, and controlling user environments. I also learned the importance of linking GPOs correctly to Organizational Units.
I successfully joined a Windows client machine to the domain, which strengthened my understanding of domain-based authentication and centralized user management.
Additionally, I used Event Viewer to monitor authentication logs and analyze security events such as successful logons, logoffs, and administrative activities. This gave me insight into how system administrators track user activity and troubleshoot issues.
Overall, this project helped me understand how enterprise IT environments are structured and managed, and improved my confidence in working with Windows Server, Active Directory, and system administration tools.
