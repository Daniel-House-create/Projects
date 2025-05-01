<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Install IIS and activate CGI
- Install PHP manager for IIS, Rewrite Module, and MySQL
- Install OS Ticket and the necessary extensions

<h2>Installation Steps</h2>

<p>
First, I created a virtual machine using Microsoft Azure. I used the Windows 10 operating system with 2vcpus (virtual CPUs) and 8 GiB memory. After I signed in, I downloaded the osTicket-Installation-Files and unzipped it, placing it on the desktop 
</p>
<br />

<p>
<img width="600" alt="Screenshot 2025-03-02 at 4 13 07 PM" src="https://github.com/user-attachments/assets/c5ce4e69-60c7-4091-8482-a4273b35d766"/>
</p>
<p>
Second, I went and installed IIS, or Internet Information Services, and activating CGI, or Common Gateway Interface. IIS is used on Microsoft Windows to host websites, applications, and services. CGI acts as a bridge between a web server and applications running on it, allowing them to share data. 
</p>
<br />

<p>
<img <img width="843" alt="Screenshot 2025-03-02 at 4 25 17 PM" src="https://github.com/user-attachments/assets/f3ecc24a-43e1-43ef-9209-ddb91edd170a" />
 />
<img s<img width="786" alt="Screenshot 2025-03-02 at 4 20 17 PM" src="https://github.com/user-attachments/assets/90772bbe-e2df-46a1-8f0b-5510d86c49b1" />
<img <img width="782" alt="Screenshot 2025-03-02 at 4 20 57 PM" src="https://github.com/user-attachments/assets/6905c0c0-8a56-4f50-b525-726b6a301f82" />
/>
</p>
<p>
Third, I installed the PHP manager for IIS, the Rewrite Module, and MYSQL. With PHP, I registered it within IIS. MySQL required a username and password; root and root. I kept them simple for the sake of this lab.
</p>
<br />

<p>
<img sr<img width="1135" alt="Screenshot 2025-03-02 at 4 36 34 PM" src="https://github.com/user-attachments/assets/4e61fc7b-57a1-4bfa-91e9-a66665c991af" />
</p>
<p>
I then installed osTicket and installed the necessary extensions.
</p>
<br />
