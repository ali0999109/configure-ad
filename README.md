<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2> Step 1 High-Level Deployment and Configuration Steps For VM1 and VM2</h2

Virtual Machine 1 Set up. Go to resource groups in Azure, and create a resource group.

Type virtual machine and press create in the Azure portal. 

pick the 16 GiB memory and make sure to give the virtual machine a name and use the resource group you created.

  ![image](https://github.com/ali0999109/configure-ad/assets/145396907/8ecfb477-b3af-422b-b3c9-f221fd4d237f)

  Leave the default configuration on disks and click next to networking it should auto-generate
  ![image](https://github.com/ali0999109/configure-ad/assets/145396907/3de3fd33-cabe-478d-8a8d-570f342cee68)
  
  **Scroll down and click review and create and you should be done for the first VM**


  

  - VM2 use the same resource group and create another VM make sure its in the same region. 
  Select ubuntu. The rest of the config are the same

  ![image](https://github.com/ali0999109/configure-ad/assets/145396907/c2e4e1c2-e8f5-4fe2-b778-28e2d69b1bb5)

  # step 2 connecting to Windows VM1 with RDP
  - Go to your virtual machine in the azure portal and click on it
  it should like this
  
  - copy the public ip address in the right corner
  - type rdp in the windows search bar and paste the address into it

  ![image](https://github.com/ali0999109/configure-ad/assets/145396907/d9d975be-ad77-4d9a-a23a-d60148fde63c)

  
  ![image](https://github.com/ali0999109/configure-ad/assets/145396907/120040ae-9017-424c-9907-28abb624abb4) 

# Step 3 install Wireshark 
- install wireshark through the windows 10 VM, type download wireshark in the browser, click windows installer (64 bits)
![image](https://github.com/ali0999109/configure-ad/assets/145396907/d9f7626e-445a-4af7-acb1-57e99bbb3d05)

- Open up wireshark and type in ICMP to filter out traffic
- ![image](https://github.com/ali0999109/configure-ad/assets/145396907/1ee18477-757b-4ab0-9a81-623c77c3536d)

- ![image](https://github.com/ali0999109/configure-ad/assets/145396907/1c5d2bc4-c925-4a10-abb2-24e089735d51)

- Go to VM2 and get your Private IP address
- ![image](https://github.com/ali0999109/configure-ad/assets/145396907/5295d261-ff13-436f-98f7-66437eed5b09)

- Ping the private ip address through powershell in your windows 10 VM and you should get ICMP traffic showing up in wireshark.
- Continous Ping type Ping -t in powershell
- ![image](https://github.com/ali0999109/configure-ad/assets/145396907/dd886743-1cf0-4e48-ad10-6b534392adc9)

- # Step 4 Block icmp traffic on VM2
  







<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
