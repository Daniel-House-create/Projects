# NetworkVLAN

<h1>Network VLAN Setup and Configuration</h1>
This project outlines the steps of creating and configuring a VLAN.<br />


<h2>Environments and Technologies Used</h2>

- Cisco Packet Tracer

<h2>Operating Systems Used </h2>

- Windows 11</b> (21H2)

<h2>VLAN Steps</h2>

- Create network topology
- Configure VLAN on Multi-layer switches
- Configure a trunk link on switches
- Create sub interfaces to allow the router to handle inter-VLAN traffic
- Set up DHCP in VLAN 10 and 20
- Test DHCP connection

<h2>Installation Steps</h2>

<p>
<img width="750" alt="Screenshot 2025-04-30 at 9 12 45 AM" src="https://github.com/user-attachments/assets/ca258ce3-0efc-4de2-b071-80b1e7ee5510" />

</p>
<p>
This is the network diagram I've constructed. It has one router, two multi-layered switches, and two VLANs, VLAN 10 and VLAN 20. VLANs allow networks to separate traffic and create better efficiency within a large organization. VLAN 10 is the HR department while VLAN 20 is the Management department. The multilayer switches can support multiple VLANs. This ensures that different networks can run on the same physical device, which can be useful in organizing networks in schools and offices. 
</p>
<br />

<p>
<img width="764" alt="Screenshot 2025-04-28 at 11 12 52 AM" src="https://github.com/user-attachments/assets/54d8f6c2-a9c9-4d10-9fe0-e563ffd9407d" />

</p>
<p>
These are the commands that I used to create the VLANs and assign them to their correct ports. VLAN 10's name is HR and is assigned to ports f0/1-3, which are the VLAN 10 ports. Using the switchport access command connects the PCs to one VLAN and that the ports will be under one VLAN only. The same goes for VLAN 20. Its name is Management and it is connected to ports f0/4-6. This screenshot shows only the first switch being configured, but both switches have to be configured.
</p>
<img width="850" alt="Screenshot 2025-04-30 at 9 26 41 AM" src="https://github.com/user-attachments/assets/7cb31311-bcb5-4d66-a506-e487ba828aa5" />
<p>
For VLAN 20, its ports for VLAN 10 are f0/1-7 and for VLAN 20 are f0/8-12. This screenshot is evidence that the ports are connected and running.
</p>
<br />

<p>
<img width="750" alt="Screenshot 2025-04-30 at 9 33 56 AM" src="https://github.com/user-attachments/assets/d456a324-8db3-4c6e-ac75-583391864533" 
/>
<img width="719" alt="Screenshot 2025-04-30 at 9 36 01 AM" src="https://github.com/user-attachments/assets/4ec199d3-e9c4-4974-95c0-51b0be58ecb9" />

</p>
<p>
Next, I created a trunk link. A trunk link allows a single connection to carry all traffic from the VLANs simultaneously, increasing bandwidth. This screenshot shows the commands used. I interfaced g0/2. Before setting trunk mode, I have to specify the encapsulation type. ISL or 802.1Q is acceptable and the industry standard to set up a trunk link. Cisco switches support 802.1Q, so that is the encapsulation command I went for. I then made sure that VLANs 10 and 20 are included in the trunk link.
</p>
<p>
The first screenshot shows the commands. The second screenshot shows that the VLANs are connected and the trunk link is established. The same commands are used on the other switch as well.
</p>
<br />

<p>
<img <img width="750" alt="Screenshot 2025-04-30 at 9 40 11 AM" src="https://github.com/user-attachments/assets/0cb78118-5411-4eb2-ad67-bccdb3b621c2" />
</p>
<p>
I then have to configure the router to handle inter-VLAN communication. Since the router can have only one IP address because of its physical interface, I can create sub interfaces to mitigate the issue. I created two sub interfaces: g0/0.10 and g0/1.20. I set the encapsulation to dot1q for g0/0.10 and added the IP address 192.168.1.1. This is the gateway address for all VLAN 10 PCs. For g0/1.20, I added the IP address 10.1.1.1. This IP address is the gateway address for all VLAN 20 PCs. The screenshot indicates the commands I used for both sub interfaces and that the interfaces are up and running with the correct IP addresses.
</p>
<br />

<p>
<img width="750" alt="Screenshot 2025-04-30 at 9 45 37 AM" src="https://github.com/user-attachments/assets/63269c1b-d6de-48c5-9b40-c2137a0baa98" />
</p>
<p>
Next, I have to make sure that the switches can pass traffic to the router. I configured trunking on the g0/1 interfaces. I set the switchport trunk encapsulation to dot1q and allow VLAN 10 and 20 to be added. The same has to be done on the other switch. This screenshot shows the commands and that both VLANs can now pass traffic to the router. 
</p>
<br />

<p>
<img<img width="635" alt="Screenshot 2025-04-30 at 9 48 48 AM" src="https://github.com/user-attachments/assets/a9195274-9717-43e7-80c1-740efcf8667c" />
</p>
<p>
I then set up DHCP so that the PCs in VLAN 10 and 20 automatically receive their correct IP addresses. Before creating the DHCP pool, I exclude the gateway addresses of both VLANs, 192.168.1.1 and 10.1.1.1. Then the pools are created with the names VLAN 10 and 20. For VLAN 10, the network address is 192.168.1.0. The default router address is 192.168.1.1 and I set the DNS server to 8.8.4.4, which is Google's DNS server. For VLAN 20, the network address is 10.1.1.0. The default router is 10.1.1.1 and the DNS server is 8.8.4.4.
</p>
<p>

</p>
<br />

<p>
<img width="750" alt="Screenshot 2025-04-30 at 9 53 29 AM" src="https://github.com/user-attachments/assets/785e8785-bf44-4276-9003-8372ecf9b1a9" />
</p>
<p>
Then we have to test if the DHCP is assigning IP addresses to the correct PCs on the correct VLANs. The screenshot above shows that they are. PC0 is assigned to VLAN 10 and has the correct IP address. PC4 is under VLAN 20 and has the correct IP address. DHCP and the trunk links between the switches are working properly.
</p>
<br />

<p>
<img <img width="450" alt="Screenshot 2025-04-30 at 9 57 10 AM" src="https://github.com/user-attachments/assets/b858e1df-0087-4f4e-9c55-00f77719ed75" />
<img width="450" alt="Screenshot 2025-04-30 at 9 57 18 AM" src="https://github.com/user-attachments/assets/235dff78-19f2-4d52-97ae-54aa5ea251e8" />
<img width="450" alt="Screenshot 2025-04-30 at 10 01 33 AM" src="https://github.com/user-attachments/assets/f916e7cb-e5f1-4b11-ac7b-bc4a092a055e" />
</p>
<p>
It's time to test and see if the PCs can communicate with one another between switches and between VLANS. The first screenshot shows communnication between VLAN 10 and 20. The second is the proven communication between VLAN 20 and VLAN 10. The third screeshot is communication within the same VLAN, VLAN 10, but on another switch. The router is allowing traffic between the two due to the configured sub interfaces. 
</p>
<br />

<p>
<img width="830" alt="Screenshot 2025-04-30 at 10 00 17 AM" src="https://github.com/user-attachments/assets/5eaecc1c-5797-4205-b161-b675616b6854" />
>
</p>
<p>
This is the updated network topolgy.
</p>
<br />
