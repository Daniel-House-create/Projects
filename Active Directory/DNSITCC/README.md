# DNSITCC
This repository deals with DNS A-Record, local DNS cache, and CNAME

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines creating a DNS A-Record, flushing DNS cache, and creating a CNAME record.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Ping Mainframe and see that it doesn't work
- Go into dc-1 via Remote Desktop as an admin, access DNS and add new host. The IP address has to mamtch dc-1's private address of 10.0.0.4
- Ping Mainframe again
- For DNS flushing, change the IP address to 8.8.8.8
- ping Mainframe and notice that it doesn't show updated IP address
- type the command ipconfig /flushdns
- ping Mainframe again and the address should be updated
- For CNAME, got to mydomain in DNS manager and create a new CNAME called search.
- FDQN should be www.google.com and ping IP address

<h2>Deployment and Configuration Steps</h2>

<p>
<img <img width="570" alt="Screenshot 2025-03-16 at 2 55 53 PM" src="https://github.com/user-attachments/assets/0eaedaf0-700c-49cf-a4e7-550fc8cada8a" />
/>
</p>
<p>
I tried to ping mainframe, but it could not be found because the A-record hasn't been created.
</p>
<br />

<p>
<img <img width="753" alt="Screenshot 2025-03-16 at 3 02 48 PM" src="https://github.com/user-attachments/assets/10c221c2-b2fc-4b58-a86e-50be73c6a66f" />
</p>
<p>
Go into dc-1, which is the DNS server and domain controller, via Remote Desktop as an admin, access DNS manager, mydomain.com, and right click to add host. The IP address should match dc-1's private address of 10.0.0.4. 
</p>
<br />

<p>
<img <img width="570" alt="Screenshot 2025-03-16 at 3 03 27 PM" src="https://github.com/user-attachments/assets/13e318e2-e730-4c37-9fe1-00195298dae1" />
</p>
<p>
I pinged mainframe again and we were able to get access.
</p>
<br />

<p>
<img <img width="754" alt="Screenshot 2025-03-16 at 3 05 03 PM" src="https://github.com/user-attachments/assets/576d26b7-745a-43be-b55d-0c8026bcf486" />
</p>
<p>
This activity is about flushing DNS cache. When using ping, the local DNS cache is checked first, then the local host file, and then the DNS server, with DNS cache being the fastest. Back in the Mainframe properties, I changed the IP to 8.8.8.8.
</p>
<br />

<p>
<img <img width="567" alt="Screenshot 2025-03-16 at 3 05 26 PM" src="https://github.com/user-attachments/assets/3be4ba10-f206-4880-88fc-42149bd28ef2" />
</p>
<p>
I pinged mainframe, but it doesn't show the updated IP address. This is because DNS local cache is checked first, and 10.0.0.4 was the last one saved. 
</p>
<br />

<p>
<img <img width="564" alt="Screenshot 2025-03-16 at 3 09 09 PM" src="https://github.com/user-attachments/assets/2e65c19d-1872-4742-adf1-f1d0669a4538" />
</p>
<p>
I used the command ipconfig /flushdns to delete the local DNS cache. 
</p>
<br />

<p>
<img <img width="306" alt="Screenshot 2025-03-16 at 3 09 32 PM" src="https://github.com/user-attachments/assets/4324f404-28a6-4f3b-bccd-4cc2b141a49f" />
</p>
<p>
I then pinged mainframe again, and now the appropriate IP address is shown. This is because there is nothing in the DNS cache, nothing in the local host file, but the changed and correct IP address was in the DNS server.
</p>

<p>
<img <img width="752" alt="Screenshot 2025-03-16 at 3 14 23 PM" src="https://github.com/user-attachments/assets/bb585dcb-771f-45c6-a140-171681fa27e7" />
</p>
<p>
In this last activity, I created a CNAME called search. For the FDQN, or the fully qualified domain name, I used www.google.com. 
</p>
<br />

<p>
<img <img width="309" alt="Screenshot 2025-03-16 at 3 15 05 PM" src="https://github.com/user-attachments/assets/7c5a7736-a118-4f94-94f5-63bbb48f8f78" />
</p>
<p>
Then I pinged search in Powershell, and it pinged www.google.com, and I was able to connect. I then used the command nslookup search to see all the IPs that google has.
</p>
<br />
