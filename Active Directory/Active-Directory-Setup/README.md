<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the steps of implementing on-premise Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create virtual machines, set DC-1 private IP to static, and connect Client-1 to DC-1
- Ping test from Client-1 to DC-1 to ensure connectivity
- Install Active Directory Services, set up a new forest as mydomain.com
- Create new organizational units named _EMPLOYEES and _ADMINS.
- Create user Jane Doe and add her to the Domain Admins security group
- Ensure everyone can access remote desktop and create users

<h2>Deployment and Configuration Steps</h2>

<p>
One virtual machine was created with Windows 10 Pro, Client-1. A virtual network was created with Windows Server 2022, DC-1.
</p>
<br />

<p>
<img width="500" alt="Screenshot 2025-02-26 at 9 24 47 AM" src="https://github.com/user-attachments/assets/41b63640-773c-46a5-bf5f-ae9f8525df10" />
<img width="500" alt="Screenshot 2025-02-26 at 9 35 54 AM" src="https://github.com/user-attachments/assets/8d284384-1055-425e-8d72-cee5e30d5c96" />
</p>
<p>
DC-1's NIC private address was set to be static because Client-1 will use DC-1 as the DNS server. If IP address changes, then CLient-1 will have to keep switching its private IP address. This is to prevent the server's private IP address from changing if it's turned off or if something wrong occurs. Then, in Client-1's DNS Server settings, it will have the same private IP address as DC-1. Windows Firewall was also disabled to ensure connectivity.
</p>
<br />

<p>
<img width="500" alt="Screenshot 2025-03-10 at 3 28 35 PM" src="https://github.com/user-attachments/assets/69cf47e1-430c-4929-87f7-9c364e4e6258" />
</p>
<p>
A ping test was done in Powershell to ensure Client-1 and DC-1 were connected and could communicate. I used the command ipconfig /all to check if Client-1's DNS Servers IP matched DC-1 (10.0.0.4). It did. Windows Firewall was also disabled to ensure connectivity.
</p>
<br />

<p>
<img width="500" alt="Screenshot 2025-03-10 at 5 10 56 PM" src="https://github.com/user-attachments/assets/ae4c88d5-f082-4ffa-999e-a5aecea90207" />
</p>
<p>
Active Directory Services was installed through Service Manager by adding new features and roles. Then a new forest was set up and it was named mydomain.com. This will be used when we have to log back into the virtual machine later.
</p>
<br />

<p>
<img width="500" alt="Screenshot 2025-03-10 at 5 30 16 PM" src="https://github.com/user-attachments/assets/48fc8131-dc62-494a-9b8a-f5aeeba49712" />
</p>
<p>
Within Active Directory, two organization units were created, _EMPLOYEES AND _ADMINS under mydomain.com
</p>
<br />

<p>
<img width="500" alt="Screenshot 2025-03-10 at 5 22 35 PM" src="https://github.com/user-attachments/assets/05b12231-5fda-46a8-826f-f024ae633272" />
<img width="500" alt="Screenshot 2025-03-10 at 5 23 42 PM" src="https://github.com/user-attachments/assets/7274115f-cb0f-46c2-94d3-5323fadcafff" />
</p>
<p>
A new employee, Jane Doe, was created and added to the Domain Admins Security Group. She will now be what we will sign in with when we log back into the virtual machine. 
</p>
<br />

<p>
<img width="500" alt="Screenshot 2025-03-10 at 5 27 51 PM" src="https://github.com/user-attachments/assets/5e6feffc-6f6d-4ad9-9e7a-6b651ef891c5" />
</p>
<p>
Then remote desktop was enabled for everyone so that all future employees will be able to use it. 
</p>
<br />
