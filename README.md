# Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols
<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>



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

- Create Resourses
- Install Wireshark
- Observe Differant Network Protocols


<h2>Actions and Observations</h2>
STEP ONE: INSTALL RESOUCE GROUP
<p>
You'll need to create a "Resourse Group" so the vitrual machines that are used, are housed in one place. This helps to keep things orginzed and help keeps track on traffic between the two machines. 
So to get started first we'll create a "Resourse Group" and to create one is head to the search bar and quick search "Resource Group" or seletect "Create a Resource" within the Azure Portal. Then select the "create a Resource".
  
  
 ![Screenshot 2023-08-27 121224](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/0e455b1d-680e-45e2-93b7-1918ff4a9c7f)

On the top left click on on "+ Create" or Create Resourse Group" in the middle of the page. This create a hub for your "vitrual Machines".

![Screenshot 2023-08-27 121047](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/a948cee7-d235-4d38-a230-7a32e704b50b)

In the "Project Details" select your subscripion name then "create" a name for your "Resouce Group" Here mine is "Lab2". Lastly, select the appropriate Region for you. Closer to your region the cheaper the cost of the service.


![Screenshot 2023-08-27 121200](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/2c6fc021-48a4-4951-9262-4c2c4be92c39)

To create the two "vitrual machine" repeat the steps that created the "Resource Group". These two "Vitrual Machines" will allow us to send traffic between the two machines. Naming the two Machines  will help you keep things orginzed. Since there are two vitual machines, the first one will be created "Windows Operating System" and name this one "VM1". To create VM go to search type " Vitrual Machine" and +create "Azure Virtual Machine". Just like in the creating the Resource group, select the Subsription, Resource Group, name your Vitrual Machnine(VM1), your Region, then select Windows 10 Pro version 22H2-x64 Gen2 for the VM "Image. Then select the "Size" of the VM. Must be "2 vcpus" or bigger. Make sure you check mark the "I confirm" box then procced to "review + Create" and again "Create".

![Screenshot 2023-08-24 171447](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/67d80e13-8c1f-4b23-9257-4e69377e5c95)

![Screenshot 2023-08-24 171516](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/cef2d31e-6bde-46f0-87f8-3167e2c9869e)


![Screenshot 2023-08-24 171807](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/54d47afa-6037-4b82-a3b2-23baa8a32ecc)



For the second VM choose the same info. But for the name abd the image will be different. So name the second "VM" (VM2) and select the "Ubuntu Server 20.04 LTS-x64 Gen2. Finish the rest and then create + review.   

![Screenshot 2023-08-24 171720](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/5f40ccd9-584a-4576-b21c-a95bbbc81d89)

After both are done being created, you can go to your "vitrual Machine" tab or your "Resource Group" tab in the Azure front page. You can view both Vitrual machine at once and you observe both have different operating system. 

![Screenshot 2023-08-24 172348](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/d485a0c4-386e-49c2-bb02-765f4aa1405c)


STEP2: INSTALL WIRESHARK

With your Virtual Machines are done and ready. A quick search for "Remote Desktop Connection" and enter the the public Ip Address of VM1 and enter the virtual machine. 









