<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Post-Install Configuration</h1>
This outlines the post-install configuration of osTicket.<br />

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Post-Install Configuration Objectives</h2>

- Create Roles, Departments, and Teams
- Configure Agents
- Configure Users
- Configure SLA
- Configure Help Topics

<h2>Configuration Steps</h2>

<p>
<img <img width="641" alt="Screenshot 2025-03-03 at 2 05 00 PM" src="https://github.com/user-attachments/assets/4705b220-0045-4564-8f7c-f0b4e26c3b8a" />
<img src<img width="565" alt="Screenshot 2025-03-03 at 2 06 42 PM" src="https://github.com/user-attachments/assets/a9bb759d-f67a-4b08-b7b1-546fd1a4c5b4" />
<img width="565" alt="Screenshot 2025-03-12 at 9 53 11 AM" src="https://github.com/user-attachments/assets/3d403887-03ab-4876-9879-cfeb3054b8fd" />
</p>
<p>
I created a Role called the Supreme Admin. This gave all privileges to the user assigned, from assigning a ticket to transferring it between departments. For Departments, I added a SysAdmins department. For Teams, I created a new team called Online Banking. 
</p>
<br />

<p>
<img width="424" alt="Screenshot 2025-03-12 at 9 52 57 AM" src="https://github.com/user-attachments/assets/3c131fa9-7f79-4be7-b966-b4b6e5234a8c" />
</p>
<p>
I created two agents named Ray and Wendy. They have their personal logins. Ray works in Support while Wendy works in Support/SysAdmins.
</p>
<br />

<p>
<img width="424" alt="Screenshot 2025-03-03 at 2 17 19 PM" src="https://github.com/user-attachments/assets/a6a2ea3b-db52-47c9-84b6-3455ae438139" />
</p>
<p>
I created two users named Karen and Ken. These two will be the people who will create and submit tickets that the agents, Wendy, Ray, and myself, will have to answer.
</p>
<br />

<p>
<img width="524" alt="Screenshot 2025-03-12 at 9 53 57 AM" src="https://github.com/user-attachments/assets/f3b7ab01-529d-483d-a30d-5556babbf9f0" />
</p>
<p>
I created and configured three tiers of SLAs, or Service Level Agreement. Sev-A is the most severe, and tickets are labeled this if it would business on the highest level, like a network-wide power outage or cyber attack. The grace period is an hour and has to be worked on 24/7 until it is resolved. Sev-B is the second. The grace period is four hours and has to be worked on 24/7 until it is resolved. Sev-C is the least severe. The grace period is eight hours and is only to be worked on during business days and hours, excluding holidays. This could be like a printer problem.
</p>
<br />

<p>
<img width="524" alt="Screenshot 2025-03-12 at 9 54 12 AM" src="https://github.com/user-attachments/assets/75d29cbe-a9f5-4bd1-bc2b-cee45976ce1e" />
</p>
<p>
I created five Help Topics: Business Critical Outage, Personal Computer Issues, Equipment Request, Password Reset, and Other. The rest in the screenshot were the default Help Topics.
</p>
<br />
