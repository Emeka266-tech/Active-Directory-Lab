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

They are two adapters, identify the host adapter (usually Ethernet 1), right click it, select properties, select ipv4, select use the following IP (to create a static IP) and set the following configuration:

. IP address: 192.168.56.10

. Subnet mask: 255.255.255.0

. Preffered DNS server: 192.168.56.10

<img width="1920" height="1080" alt="VirtualBox_Doc1_16_03_2026_14_03_02" src="https://github.com/user-attachments/assets/b36c3aba-6557-4ae8-b778-a9b6a2a13199" />

