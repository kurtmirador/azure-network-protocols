<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration (Azure Setup)</h2>

- ### [YouTube: Azure Virtual Machines](https://www.youtube.com/watch?v=OCiN37sjXuw)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create Azure Virtual Machines and Network Resources
- Capture and Observe ICMP Traffic with Wireshark
- Block and Re-enable ICMP via Network Security Group (NSG)
- SSH Traffic Observation
- Monitor Other Traffic Types (DHCP, DNS, RDP)

<h2>Actions and Observations</h2>

<p>
<img width="1246" alt="Screenshot 2025-04-17 at 6 56 22 PM" src="https://github.com/user-attachments/assets/1c2b8e7a-8e99-44df-b495-4cc2e4eaa507" />
</p>
<p>
🔹 Step 1: Create Azure Virtual Machines and Network Resources

Description:
Start by creating a Resource Group, then deploy a Windows 10 VM and a Linux (Ubuntu) VM within the same Virtual Network and Subnet. This setup is crucial for capturing traffic between the two machines. Screenshot should show both VMs, the shared VNet, and subnet.
</p>
<br />

<p>
<img width="1251" alt="Screenshot 2025-04-17 at 6 58 31 PM" src="https://github.com/user-attachments/assets/04a087aa-93fd-4d40-9e76-8d8f4af7bd64" />
</p>
<p>
🔹 Step 2: Capture and Observe ICMP Traffic with Wireshark

Description:
Using Remote Desktop, connect to the Windows 10 VM and install Wireshark. Start capturing traffic and apply the ICMP filter. Then, ping the Ubuntu VM’s private IP. This lets you observe request and reply packets, verifying connectivity within the virtual network.
</p>
<br />

<p>
<img width="1090" alt="Screenshot 2025-04-17 at 7 01 22 PM" src="https://github.com/user-attachments/assets/7442185e-d632-4740-92a3-60cf3da998ab" />
</p>
<p>
🔹 Step 3: Block and Re-enable ICMP via Network Security Group (NSG)

Description:
Navigate to the NSG tied to the Ubuntu VM and disable inbound ICMP. While a continuous ping runs, watch how packets stop in both the command line and Wireshark. Then, re-enable ICMP, and watch traffic resume. Screenshot should capture the NSG rule list before and after the change.
<br />

<p>
<img width="1234" alt="Screenshot 2025-04-17 at 7 02 49 PM" src="https://github.com/user-attachments/assets/c92bce29-2a9f-4df0-932c-b9b77165bcca" />
</p>
<p>
🔹 Step 4: SSH Traffic Observation

Description:
From the Windows VM, initiate an SSH session to the Ubuntu VM using its private IP. Apply the SSH filter in Wireshark. As you authenticate and type commands, you'll see encrypted SSH packets flowing. Screenshot should capture the SSH session in progress with visible traffic.
</p>
<br />

<p>
<img width="1244" alt="Screenshot 2025-04-17 at 7 07 47 PM" src="https://github.com/user-attachments/assets/aab0209e-2aaa-40fc-8dc0-154107e05b22" />
<img width="1186" alt="Screenshot 2025-04-17 at 7 07 24 PM" src="https://github.com/user-attachments/assets/698bbe42-279d-4228-b230-17567a92fe75" />
<img width="1192" alt="Screenshot 2025-04-17 at 7 06 15 PM" src="https://github.com/user-attachments/assets/cc3c1a98-494d-4d2a-80e5-0807a0461680" />
<img width="1088" alt="Screenshot 2025-04-17 at 7 05 17 PM" src="https://github.com/user-attachments/assets/f49bdd5e-7e1f-46ad-8f39-dd1031c1e06d" />
<img width="1087" alt="Screenshot 2025-04-17 at 7 04 41 PM" src="https://github.com/user-attachments/assets/45cf34de-33aa-492e-bc89-5bcc280225f0" />
</p>
<p>
🔹 Step 5: Monitor Other Traffic Types (DHCP, DNS, RDP)

Description:

DHCP: Run ipconfig /renew on the Windows VM and capture new IP assignment requests in Wireshark.

DNS: Use nslookup google.com and disney.com to resolve domain names, observing DNS queries and responses.

RDP: Filter tcp.port == 3389 to see constant RDP stream traffic (continuous due to the live desktop session).
Screenshots should show each protocol’s filtered traffic individually.
</p>
<br />
