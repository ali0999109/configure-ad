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

 # Connecting to Windows VM1 with RDP
  - Go to your virtual machine in the azure portal and click on it
  it should like this
  
  - copy the public ip address in the right corner
  - type rdp in the windows search bar and paste the address into it

  ![image](https://github.com/ali0999109/configure-ad/assets/145396907/d9d975be-ad77-4d9a-a23a-d60148fde63c)

  
  ![image](https://github.com/ali0999109/configure-ad/assets/145396907/120040ae-9017-424c-9907-28abb624abb4) 

# install Wireshark on VM1 and ping VM2 through powershell
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

- # Block icmp traffic on VM2 through NSG
- go to network security group on the Azure portal
- click on vm2 security group 
- click on inbound security rules, click add on the top left, and put in the following configurations to block ICMP traffic (picture 2)
- check back on your Windows 10 VM and look at the traffic on Wireshark and PowerShell, it should say request timed out and the Wireshark traffic should pause ( picture 3)
- you can go back and delete the security rule and clean up in the azure portal
  ![image](https://github.com/ali0999109/configure-ad/assets/145396907/d2637340-802c-49ea-8463-bcfcf6ce7a20)
  ![image](https://github.com/ali0999109/configure-ad/assets/145396907/46d62233-f5dc-4560-9cef-ffe1fe140679)
  ![image](https://github.com/ali0999109/configure-ad/assets/145396907/7cfc4688-1630-453b-9b86-1ce025097a3c)
# SSH from VM1 into VM2
- Filter out wireshark traffic by typing SSH
- type in SSH, username, and @ the private IP address of VM2 (which was shown previously)
- click yes and enter the password for VM2
- type in some Linux commands in PowerShell like ls, pwd, id it will show up in wireshark
- to stop the SSH connection type in Exit
- another way to filter out SSH traffic on wireshark is to type tcp.port == 22

![image](https://github.com/ali0999109/configure-ad/assets/145396907/1efe40c0-dacc-47be-a59d-352265b542ae)
![image](https://github.com/ali0999109/configure-ad/assets/145396907/d7ed723f-5720-456e-9f81-00f0f476e632)
![image](https://github.com/ali0999109/configure-ad/assets/145396907/1e5f3080-bcad-43b5-9e80-23046ea5ed13)
![image](https://github.com/ali0999109/configure-ad/assets/145396907/e2250fe5-5336-4c50-9563-62545ef9b3c2)

![image](https://github.com/ali0999109/configure-ad/assets/145396907/61619ab2-e15b-4155-81a5-d212f9eefad7)
![image](https://github.com/ali0999109/configure-ad/assets/145396907/fa7d99dd-bc7b-49f8-8a3e-e5b267c210a6)

# Observing DNS and DHCP traffic in Wireshark
- type in ipconfig/renew to observe DHCP traffic (type in dhcp to filter out traffic in Wireshark)
- type in Nslookup and any website to observe DNS traffic for example google.com ( type in dns to filter out traffic in wireshark)
  
  ![image](https://github.com/ali0999109/configure-ad/assets/145396907/092e43e5-29ea-4005-96e3-f6f2dfb5bb0d)
  
  ![image](https://github.com/ali0999109/configure-ad/assets/145396907/8c6c7cea-f64c-41a0-a100-754b06f19a29)
