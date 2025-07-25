<p align="center">
<img width="auto" height="auto" alt="AD" src="https://github.com/user-attachments/assets/8997adb8-3e38-4019-9da5-6fadf4bab369" />
</p>

# Lab Architecture: Preparing Active Directory Infrastructure in Azure
*Step-by-step instructions for configuring a Domain Controller and a client machine in Microsoft Azure*

<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://github.com/user-attachments/assets/9bbedfde-1f6d-4f70-9242-05e314480b32" /> Pre-Configuration
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://github.com/user-attachments/assets/8212e71d-8b42-4c0f-9be1-5ccc93c0793f" /> Post-Configuration
    </td>
  </tr>
</table>

## Environments and Technologies Used:

- Microsoft Azure (Virtual Machines/Cloud Compute)
- Remote Desktop Protocol
- Windows Server
- Windows 10 

## Lab Prerequisites:
- PC or Laptop
- Connection to the Internet
- Microsoft Azure Subscription

# Installation Steps:

<img width="700" height="700" alt="RG Create 1" src="https://github.com/user-attachments/assets/896fb4ef-e804-4128-8d5b-cabf7a46d48a" />

- To begin, log on to your Azure account and Navigate to resource groups.
- Hit Create.

<img width="700" height="700" alt="RG Create 2" src="https://github.com/user-attachments/assets/919e86f4-1721-4553-97fb-2394c58d5ef5" />

- Making sure you're using the proper subscription, we are going to name our Resource Group for this lab & select the region.
  - Name your Resource Group Active-Directory-Lab
  - Put your Resource Group in a region local to you, I am going to use East US 2.
- Click Review + Create.


<img width="700" height="700" alt="RG Create 3" src="https://github.com/user-attachments/assets/562c288a-69df-41c2-a1f5-f86232522055" />

- Review the properties of the Resource Group, making sure it is in the region you want it to be in. We need to make sure to use the same region as we create this lab's infrastructure.
- When prompted, click create one last time.
- Next, we are going to create our Virtual Network.

<img width="700" height="700" alt="Virtual Network Create" src="https://github.com/user-attachments/assets/7c69335e-780b-42d4-9641-67ee3712f7d2" />

- Next, navigate to Virtual Networks, we are going to create our own for this lab.
- Click Create once you've landed on the Virtual Network home page.


<img width="700" height="700" alt="VNet Create" src="https://github.com/user-attachments/assets/980ea549-223f-4863-9563-9655cc186f2b" />


- Make sure the new Virtual Network is in the Resource Group we just created, and name the Virtual Network, "Active-Directory-VNet"
  - make sure that it is in the same region as your resource group.
- Once you've done so, we dont have to worry about anything else for the VNet so we can just click Review + Create!

<img width="700" height="700" alt="VNet create final" src="https://github.com/user-attachments/assets/a2b7db49-972c-4dc8-92ea-c301d23d63b1" />

- Again, double check to make sure you've put the Vnet in our newly created Resource Group, and verify it is in the same region as the Resource group.
- Once you've done so, click create one last time.
- Next, we are going to create our Domain Controller Virtual Machine.

<img width="700" height="700" alt="DC1 Create" src="https://github.com/user-attachments/assets/7db8ff67-17a6-4fc1-bcea-1ef9f8a59b02" />

- Navigate to the Compute infratructure | Virtual machines section of Azure & click Create, then select Virtual Machine.

<img width="700" height="700" alt="DC-1 create 2" src="https://github.com/user-attachments/assets/47d5227d-f91a-4f51-9676-f67e3f7c282b" />


- Make sure to select the Resource Group we just created.
- For our machine's name, make it DC-1
- Keep using the same region you've been using thus far.
- Keep everyhting as-is until you get down to image.
- THIS IS VERY IMPORTANT: Select, "Windows Server 2022 Datacenter: Azure Edition - x64 Gen2" for the image.

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/05f6221b-17e1-4424-b90c-5fc9d32c9d73" />


- Leave everything alone until you get to the size of the VM, and select "Standard_D2s_v3 - 2 vcpus, 8 GiB memory"
- For the username of the Administrator account: labuser
- Password: Cyberlab123!
- Leave everything else on the page alone until you get to the Licensing and check those boxes.
- Then we can click Next: Disks >
- Then, click Next: Networking >

<img width="700" height="700" alt="DC-1 good to go" src="https://github.com/user-attachments/assets/0540d627-027d-4097-9e8d-a51156927ca0" />

- As long as our Active-Directory-VNet is selected, we can go ahead and click Review + Create!

<img width="700" height="700" alt="Review + Create" src="https://github.com/user-attachments/assets/9ed21739-d7b1-44ea-81d9-2a8e4ab1742e" />\

- Make sure your DC-1 Basic details match the image above, specifically focusing on the Resource Group, Region, Image, Size, and Virtual Network.
- If they appear to match what is seen in the above image (minus the region if you've been using one different from mine) then you are safe to click Create!
- Once the DC-1 creates, head back to the Compute infrastructure | Virtual machines for the next step.

<img width="700" height="700" alt="Create" src="https://github.com/user-attachments/assets/40119dd5-958f-42e9-a048-ef093db0d981" />

- After taking a moment to notice and apprecite our DC-1 hanging there waiting to be configured, click on create; then select Virtual Machine as we are going to set-up our client machine.

<img width="700" height="700" alt="A.Client-1" src="https://github.com/user-attachments/assets/5124c37b-3507-4d02-a95d-247f984ba0fd" />

- Select our Active Directory Resource Group, and name our new machine, "Client-1".
- Again, make sure to be consistently using the same region.
- Leave everything else alone until you get to Image.

<img width="700" height="700" alt="Image & Size" src="https://github.com/user-attachments/assets/eda99a72-bef2-4f59-a35b-e83d9426bc99" />

- For image, we are going to use Windows 10 Pro, version 22H2 - x64 Gen2
- Scroll down to Size, and select Standard_D2s_v3 - 2 vcpus, 8 GiB memory

<img width="700" height="700" alt="Cyberlabs123!" src="https://github.com/user-attachments/assets/85ee76df-b6cc-4241-9c27-0a5df93edc14" />

- For the username of the Administrator account: labuser
- Password: Cyberlab123!
- Leave everything else on the page alone until you get to the Licensing and check the box.
- Then we can click Next: Disks >
- Then, click Next: Networking >

<img width="700" height="700" alt="VNET" src="https://github.com/user-attachments/assets/04804b0a-8cd5-4cf7-bf97-0fcc538786d2" />

- As long as our Active-Directory-VNet is selected, we can go ahead and click Review + Create!

<img width="700" height="700" alt="REVIEW" src="https://github.com/user-attachments/assets/8385b0de-f65d-4a3d-9f27-e348fd478118" />



- Review your Client-1 Basic details and make sure they match the image above. Specifically focusing on the Resource Group, Region, Image, Size, and Virtual Network.
- If they appear to match what is seen in the above image (minus the region if you've been using one different from mine) as well as your Virtual Network being set to "Active -Directory-VNet" then you are safe to click Create!
---
Now that our VMs are set-up we need to do some internal configuration for the intents and purposes of this lab:

*We need to set the domain controller’s (DC) private IP to static so it never changes. This is important because the client computer uses the DC’s IP address as its DNS server in order to join the domain. If the DC’s IP address changed (because it was set to dynamic), the client would no longer be able to find the domain controller or resolve domain names, and domain services would break. Setting it to static ensures the DC is always reachable at the same IP address.*

<img width="700" height="700" alt="DC-1 Homepage" src="https://github.com/user-attachments/assets/12056a4d-10c1-420f-a88d-be81b44b2acf" />

- In order to do so, naviage to DC-1's home page in Compute infrastructure | Virtual machines.
- Click on the Networking drop-down and select network settings.

<img width="700" height="700" alt="NIC" src="https://github.com/user-attachments/assets/aaf2f228-d40e-4152-a478-094532d271e7" />

- Once inside DC-1's Network settings, click on the Network Interface Card's hyperlink. We are going to configure the Network interface card (NIC) to prevent the private IP address from changing.

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/04e9dae7-9315-48fe-b7ab-6d793a8fe3bf" />

- First, click on ipconfig1 (the sidebar on the right will appear)
- Then, change the Private IP address settings to Static.
- Click Save.

---
Log into the DC-1 VM for the next Step:

*Please note that disabling the Windows Firewall is not recommended in a real-world environment, as it exposes the system to potential security risks. However, for the purpose of this lab, we are temporarily turning it off to simplify network connectivity and avoid troubleshooting firewall issues, so we can focus on learning Active Directory concepts. Thanks for your understandiong!* 

<img width="700" height="700" alt="About" src="https://github.com/user-attachments/assets/0485c5ac-ba50-4caf-9d1f-36ea8806c53f" />

- Once you're logged into your DC-1 VM, if you want to verify you are in the correct machine, you can type in about on the search bar or navigate to settings and search, "About" and if the Windows specifications show the edition to be the Windows Server 2022 Datacenter Azure Edition then you are good to go!
  
<img width="700" height="700" alt="RUN" src="https://github.com/user-attachments/assets/7bbb17de-fd51-4246-a323-a1b0515ffec9" />

- First, open up the Run command line and type in logged into the DC-1 VM, open up the run command and type in, "wf.msc"
  - You can open up the Run app by searching, "Run" in the search bar or by right clicking the windows start icon and finding the "Run" option.

<img width="700" height="700" alt="Firewall Properties" src="https://github.com/user-attachments/assets/f975819e-d778-4100-ad9b-e2378d2b54cd" />

- Click on, "Windows Defender Firewall Properties" to be brought to the next step.

<img width="auto" height="auto" alt="TURNEMOFF" src="https://github.com/user-attachments/assets/ad4c0182-079b-4758-83ad-ade5e845e56f" />

- Turn the Firewall off for the Domain Profile, the Private Profile, and the Public Profile.
- To do so, change the firewall state from on to off in each of the profile tabs, as seen above.
- Once you have done so, click on Apply, then on OK.

<img width="700" height="700" alt="No Firewallz" src="https://github.com/user-attachments/assets/27a3fda8-54d9-4a10-8383-cec32d7e4495" />

- Your overview should now look like this subsequent to the prior step.

<img width="700" height="700" alt="Get dc1 private IP" src="https://github.com/user-attachments/assets/1461c03f-d8c6-4421-9162-6c04a78ae53f" />

- Prior to the next step we need to head back over into Azure, and obtain DC-1's private IP address. So we can set Client 1's DNS settings to DC-1's private IP address.

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/0223a044-d157-4d98-98c9-f8c950f067ad" />

- Naviage to Client 1's Network Settings.
- Click on Client 1's Virtual Network Interface Card.

<img width="700" height="700" alt="C1 NIC" src="https://github.com/user-attachments/assets/8cf7334b-41a8-499e-9627-c98e8fd93398" />

- Navigate to DNS Server settings.
- Change, "Inherit from Virtual Network" to "Custom" and enter whatever your DC-1's private IP address is.
- Click save.

<img width="1000" height="800" alt="Restart Client 1" src="https://github.com/user-attachments/assets/30ae92fe-f1f8-4232-a947-3641fd2a8a5d" />

- Once you've configured the NIC settings within Client-1's DNS server settings, navigate back to the Virtual machine home and restart Client-1 by checking the box to the left of Client-1, then finding where it says "restart" and clicking on that.
- Once you've restarted the CLient-1 VM proceed to log into Client-1 for the next step.

---
Once the VM has been sucessfully restarted, use Remote Desktop Connection to proceed to log into Client-1.
- Once logged in to the Client-1 VM, we are going to attempt to Ping DC-1 in powershell.

<img width="700" height="700" alt="Verify" src="https://github.com/user-attachments/assets/7109d904-278b-4531-ac11-06ddbc214d32" />

- If you want to verify you are on the correct Virtual Machine prior to testing the VM's connectivity, you may open up the settings, type "About" into the sarch bar, and verfiy that the VM is running on Windows 10 Pro. 

<img width="700" height="700" alt="Start PS" src="https://github.com/user-attachments/assets/a287c022-281c-48c1-9280-1f3949f401ab" />

- Now, navigate to and open up Powershell.


<table>
  <tr>
    <td>
      <img width="700" height="700" alt="Pre-Run cmd" src="https://github.com/user-attachments/assets/e7806780-d570-4138-a02b-3769086397e0" /> Ping DC-1 Private IP
    </td>
    <td>
      <img width="700" height="700" alt="Successful ping" src="https://github.com/user-attachments/assets/788217cb-084d-4e12-8993-e78fbe14dd10" /> Sucessful Ping
    </td>
  </tr>
</table>

- Type in, Ping, followed by the private IP address of DC-1 to test the connection between the two VMs

- If the ping is successful, it means the the network and firewall settings are correctly configured and basic network communication needed for domain services is working.
- If the ping command fails at this point, it means Client 1 cannot communicate with DC-1 over the network. Likely reasons include:
  - DC-1’s Windows Firewall is still enabled and blocking ping requests.
  - Client 1 and DC-1 are in different virtual networks or subnets.
  - The network interface or DNS settings are incorrect.
  - DC-1 is not running or not reachable.
- This must be fixed for domain joining and other domain controller functions to work.

<table>
  <tr>
    <td>
      <img width="700" height="700" alt="ipconfig /all" src="https://github.com/user-attachments/assets/5cfe383e-6062-404a-9380-3acd0190ee82" />
    </td>
    <td>
      <img width="700" height="700" alt="DNS" src="https://github.com/user-attachments/assets/b723323c-adad-4a00-83de-8cbbc1b9b317" />
    </td>
  </tr>
</table>


- Next, we are going to run "ipconfig /all"
  - The output for the DNS settings should show DC-1's private IP address.
 
- If the "ipconfig /all" command successfully displays DC-1's private IP address in Client-1's DNS settings, it indicates that Client-1 is correctly configured to use DC-1 as its DNS server. It confirms that the network settings are correctly applied and that the two VMs can interact as intended within the Azure environment.

---

This concludes our preparation of the Active Directory infrastructure thus concluding our lab! In this lab, we successfully established a foundational Active Directory infrastructure by deploying a Windows Server 2022 Domain Controller and a Windows 10 client within Microsoft Azure. We also configured the network settings, to ensure that the Domain Controller's static IP was set correctly, and verified connectivity through successful ping tests and DNS configuration checks.

In the upcoming lab, we will dive deeper into deploying Active Directory services, and continue to build on our skills and knowledge! Hope to see you there.

 















---



<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>

<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>
