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


STEP TWO: INSTALL WIRESHARK

With your Virtual Machines are done and ready. A quick search for "Remote Desktop Connection" and enter the the public Ip Address of VM1 (Windows 10 21H2) and enter the virtual machine. This VM is where we install Wireshark(packet analysis software).
Install Wireshark (Window Installer 64-bit) and continue with all default settings.


![Annotation 2023-08-07 212358](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/32190aee-3e34-46a2-898a-50ee9de589bc)

![Annotation 2023-08-07 212458](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/33cc9b0c-743b-4912-b913-8cb19735dd69)

![Annotation 2023-08-07 212544](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/8d6959c4-c6ce-4998-be0b-b2ef5f909564)

After it's done installing, open start and search for Wireshark and open it. When you're in the program on the top left under the "FILE" tap there is a blue fin. Click on it'll open a capture page and this where we'll see the traffic. Can you see the traffic that's already coming in?


![Screenshot 2023-08-07 172903](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/9f5ccc9f-2694-4d8b-a848-4c9bef3a2961)

![Annotation 2023-08-07 213009](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/e0ed93d1-7150-4a1a-bd6a-3a9ccbe88a1f)


STEP THREE: 

With your "VM1" running, next get and copy the IP address for your VM2 (Linux Ubutu Server 20.04) and log into it with Remote Desktop Connection. Go to Command Panel or Powershell(Run as Administrator for either one you use) 
We can ping the connection between the two machine. 

We can view the the traffic that is traveling between both Vitrual machines. On wireshark we are viewing the traffic on wireshark by filtering it by ICMP. We can try with other Domains like (www.google.com) or any IP addresses.  
Wireshark on the left and Command Prompt(Run as Administrator) on Right. Use "ping 10.0.0.5 -t" this is a contunious reply from the other VM. 

![Annotation 2023-08-07 213804](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/a4450174-62e2-47e1-9988-ff358307efbc)

We also can deny the ping request by adding this rule to our Network Security Group within our Virtual machine. After we make the changes to our VM2 we'll see that the ping that was sent will time-out. 
Back in the Azure portal head to VM2 and settings Inbound Security Rule click +add then in the change the Protocol to "ICMP" and "DENY" for action, change the Priority to 200(I made a mistake in the example photo). and name it "DenyAnyCustomAnyInbound" then click "Add" 

![Screenshot 2023-08-07 174006](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/c67cc9b5-3ae3-43d1-b1ba-bef8d6c9b793)

![Screenshot 2023-08-07 174246](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/90be9fc2-02a7-42f2-8239-621a804b1f96)

Go back in to Powershell (VM1) and you will notice that the request has timed out. In Wireshark it'll say "Request" only.

![Screenshot 2023-08-07 174819](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/61f7fa54-c5ab-4f97-8b33-26886824e105)

To allow this rule back, just return to the network security group to delete the rule or select the rule and allow the rule again.

Back into Wireshark, we will change the filter bar to SSH or tcp.port==22, then move over to Command promt, here we can login to the other VM (Linux Ubuntu Server) "ssh username@ip adress" your private IP address

![Screenshot 2023-08-09 190436](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/e1038974-d5fe-4d08-9fa5-d19a2166fdea)

After Obserbing the ssh back to Wireshark filtering bar and enter "DHCP" only traffic 

![Annotation 2023-08-09 230605](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/9807e216-ae94-414a-91d4-8f4d5ca3bfab)

Next in Wireshark type DNS and refresh then Observe "DNS" "Domain Name System" traffic. Then Powershell or Commd promt type in "nslookup" www.google.com or www.disney.com (this is just asking what their IP address are) 

![Annotation 2023-08-09 230756](https://github.com/Leibwatcher/Network-Security-Groups--NSGs-and-Inspecting-Network-Protocols/assets/137578446/f6f517aa-d4a7-4fe6-b448-75e3e1b1f10c)

After DNS back to the filter bar for the RDP traffic only (tcp.port ==3389) because the RDP (Protocol) this will show you a constantly live stream from one computer to another. It will continuous transmitt the traffic.

That is the end of the lab. Log out of the both VMs and back into the Azure portal and delete the Resource Group this will delete both VMs as well. Go and type in the search bar "Resource Group" and delete. cope and past the name of the Resource Group name and click "delete".



Speed doesnt matter, keep going!
