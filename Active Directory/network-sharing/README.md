# network-sharing
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial goes through various network sharing options.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create four folders: read-access, write-access, no-access, and accounting
- Try to access each folder from Client-1
- Create ACCOUNTANTS group in Active Directory and give read/write access in the accounting folder
- Add permissions to user bes.rik.

<h2>Deployment and Configuration Steps</h2>

<p>
<img <img width="544" alt="Screenshot 2025-03-17 at 11 05 26 AM" src="https://github.com/user-attachments/assets/8ecb98b9-56c5-4026-8375-7132c3bed4bc" />
</p>
<p>
DC-1 is the domain controller and DNS server while Client-1 is the virtual machine within dc-1. In dc-1, logging in as Jane Doe (admin), I created four folders: read-access, write-access, no-access, and accounting. Read-access is to give users the ability to see files within the folder. Write-access gives users the ability to read and write in the folder. No-access gives no access to anyone. Accounting will be used for later.
</p>
<br />

<p>
<img <img width="546" alt="Screenshot 2025-03-17 at 11 12 50 AM" src="https://github.com/user-attachments/assets/d022f824-ade8-4c7b-b544-7b09c7978442"/>
<img width="546" alt="Screenshot 2025-03-17 at 11 13 25 AM" src="https://github.com/user-attachments/assets/9d1ce6fa-f5f6-4054-ae2a-f51860a345c9" />
<img width="546" alt="Screenshot 2025-03-17 at 11 13 34 AM" src="https://github.com/user-attachments/assets/b522ebfb-0c6c-4fbe-b3c0-506e68f2b2cc" />
</p>
<p>
Within Client-1 logged in as bes.rik, I tried to access each folder, excluding accounting. I can't access read-access. I can create a document into the write-access folder. I cannot access the no-access folder. This shows that the folders and the access protocols work.
</p>
<br />

<p>
<img <img width="546" alt="Screenshot 2025-03-17 at 11 15 29 AM" src="https://github.com/user-attachments/assets/4d253c4d-0e99-475d-aaa0-982ae7b55967"/>
<img width="546" alt="Screenshot 2025-03-17 at 11 16 13 AM" src="https://github.com/user-attachments/assets/2c0209fc-2fa0-4b2a-bed3-32bb986d1adb" />
<img width="546" alt="Screenshot 2025-03-17 at 11 17 31 AM" src="https://github.com/user-attachments/assets/a00f0bec-d66e-4b49-8d2b-1eaeddadb59e" />
</p>
<p>
I created a new object group called ACCOUNTANTS. In the accounting folder, I gave the ACCOUNTANTS group read/write access to the accounting folder. So, any user in the ACCOUNTANTS group can read and write within the accounting folder. Our user, bes.rik cannot access the folder because he does not have access and is not part of the ACCOUNTANTS group.
</p>
<br />

<p>
<img <img width="548" alt="Screenshot 2025-03-17 at 11 18 39 AM" src="https://github.com/user-attachments/assets/72dad5e2-1237-4293-9bfe-bd2934f94606" />
<img width="546" alt="Screenshot 2025-03-17 at 11 20 09 AM" src="https://github.com/user-attachments/assets/6ac51460-6332-44db-86f2-9543c79e8902" />
</p>
<p>
In dc-1, I went to Active Directory Users and Computers, found best.rik, and added him to the ACCOUNTANTS folder (in the first screenshot). Then, I went back into Client-1 as bes.rik and now could access the folder (in the second screenshot). I created a document and put it in the accounting folder.
</p>
<br />
