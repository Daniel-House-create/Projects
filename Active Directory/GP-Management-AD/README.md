<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Generate Users and choose one to work with
- Configure password lockout settings with chosen user and attempt to log in with a failed password until account is locked
- Unlock the account in DC-1 with Jane Doe and log in using bes.rik
- Disable/Enable account
- Observe logs in DC-1 and Client-1

<h2>Deployment and Configuration Steps</h2>

<p>
Within DC-1 Powershell ISE (running as administrator), I created a new file and ran this script to generate new users. While the users were random, for simplicity, the password was the same. The user I chose to work with is bes.rik.
This was the script I used. This is not my own but belongs to Josh Madakor. https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1
</p>


<p>
<img width="524" alt="Screenshot 2025-03-11 at 1 08 49 PM" src="https://github.com/user-attachments/assets/d1532b1a-ceee-48f7-8d5f-54b25989fd8b" />
<img width="647" alt="Screenshot 2025-03-11 at 1 11 34 PM" src="https://github.com/user-attachments/assets/8d606a35-8b3d-42ea-a344-6249a18c42f5" />
</p>
<p>
Using the command gpmc.msc, I went under the default domain policy, windows settings, security settings, and account lockout policy. I changed the account lockout threshold to 5 invalid login attempts. Account lockout duration would be 10 minutes. I went into Client-1 as Jane Doe and forced the update in the Command Prompt with gpupdate /force.
</p>
<br />

<p>
<img width="1215" alt="Screenshot 2025-03-11 at 1 20 21 PM" src="https://github.com/user-attachments/assets/7e28f6da-55a4-420b-8ebd-b151dc82b9f7" />
<img width="534" alt="Screenshot 2025-03-11 at 1 21 45 PM" src="https://github.com/user-attachments/assets/c01c6b61-a340-4116-b616-8c2b4f5922a3" />
<img width="856" alt="Screenshot 2025-03-11 at 1 23 02 PM" src="https://github.com/user-attachments/assets/a5546d40-1779-418d-916d-31fe26daf80d" />
</p>
<p>
After five failed login attempts, I couldn't access Client-1 with bes.rik. So, I went into DC-1 as Jane Doe and unlocked his account and successfully logged into Client-1 and ensured I was bes.rik via whoami command in Powershell.
</p>
<br />

</p>
<br />

<p>
<img width="728" alt="Screenshot 2025-03-13 at 3 18 26 PM" src="https://github.com/user-attachments/assets/8f56056e-ea89-4dd2-9b49-7647f8e4df75" />
</p>
<p>
In Active Directory User and Computers, using DC-1 as Jane Doe, I can disable and enable accounts at will. I chose to disable bes.rik and then enable account.
</p>
<br />

<p>
<img width="742" alt="Screenshot 2025-03-13 at 3 22 22 PM" src="https://github.com/user-attachments/assets/25d9ca9f-1233-4fc1-84a2-e9be89d985f0" />
</p>
<p>
In Client-1 as Jane Doe, in Event Viewer and under Windows Logs and Security Logs, I observed the login attempts of bes.rik. 4625 is the Windows protocol of a failed login and 4624 is the Windows protocol of a successful login.
</p>
<br />
