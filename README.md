title: TFS-lab</br>
description: Ontwikkelstraat met release management</br>
author: Peter van Hemert</br>
created:  2016 Sept 15</br>
modified: 2016 Sept 15

---
# TFS-DevLab
------------
Ontwikkelstraat met release management.

* [Install Hyper-V on windows 10](#install-hyper-v-on-windows-10)</br>
* [Create a Virtual Switch.](#create-a-virtual-switch)</br>
* [Create a Virtual Machine with Hyper-V Manager.](#create-a-virtual-machine-with-hyper-v-manager)</br>
* [Creating A Windows 2012R2 Domain Controller](#create-domain-controller)</br>
* [13](#13)</br>
* [14 En](#14-en)

---

Install Hyper-V on windows 10   
-----------------------------

<sup>[GoTo Top](#tfs-devlab)</sup></br>
1. Right click on the Windows button and select ‘Programs and Features’.

2. Select Turn Windows Features on or off.

3. Select Hyper-V and click OK.
 
![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/enable_role_Hyper-V.png)

---

Create a Virtual Switch
-----------------------

<sup>[GoTo Top](#tfs-devlab)</sup></br>
Before you create a virtual machine in Hyper-V, you may want to provide a way for this virtual machine to connect to a physical network. Hyper-V includes software-based networking technology that allows a virtual machine's network card to connect to a virtual switch, providing network connectivity. Each virtual switch created in Hyper-V can be configured with one of three connection types:

* External Network – the virtual switch is connected to a physical network adapter which provides connectivity between the physical network, the Hyper-V host, and the virtual machine. In this configuration, you can also enable or disable the host's ability to communicate over the physically connected network card. This can be useful to isolate only VM traffic to a particular physical network card.

* Internal Network – the virtual switch is not connected to a physical network adapter. However, network connectivity exists between the Hyper-V host and any virtual machines connected to this switch.

* Private Network – the virtual switch is not connected to a physical network adapter and connectivity does not exist between the Hyper-V host and any virtual machines connected to this switch.

This exercise walks through how to create an external virtual switch using the Hyper-V Manager. When completed, your Hyper-V host contains a virtual switch that can be used to connect virtual machines to a physical network.

1. Open up Hyper-V Manager.

2. Right-click on the name of the Hyper-V host and select Virtual Switch Manager...

3. Under ‘Virtual Switches’, select New virtual network switch.

4. Under ‘What type of virtual switch do you want to create?’, select External.

5. Select the Create Virtual Switch button.

6. Under ‘Virtual Switch Properties’, give the new switch a name such as External VM Switch.

7. Under ‘Connection Type’, ensure that External Network has been selected.

8. Select the physical network card to be paired with the new virtual switch. This is the network card that is physically connected to the network.</br></br>
![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/newswitch_upd.png)

9. Select Apply to create the virtual switch. At this point you will most likely see the following message. Click Yes to continue.</br></br>
![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/pen_changes_upd.png)

10. Select OK to close the Virtual Switch Manager Window.

---

Create a Virtual Machine with Hyper-V Manager
----------------------------------------------

<sup>[GoTo Top](#tfs-devlab)</sup></br>
These steps walk through how to manually create a virtual machine and deploy an operating system to this virtual machine.

1. In Hyper-V Manager, click Action > New > Virtual Machine to bring up the New Virtual Machine Wizard.

2. Review the ‘Before You Begin’ content and click Next.

3. Give the virtual machine a name.</br>
``Note: This is the name Hyper-V uses for the virtual machine, not the computer name given to the guest operating system that will be deployed inside the virtual machine.``

4. Choose a location where the virtual machine files will be stored such as c:\virtualmachine. You can also accept the default location. Click Next when done.</br></br>
![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/new_vm_upd.png)

5. Select a generation for the machine and click Next.</br>
Generation 2 virtual machines were introduced with Windows Server 2012 R2 and provide a simplified virtual hardware model and some additional functionality. You can only install a 64-bit operating system on a Generation 2 virtual machine. For more information on Generation 2 virtual machines, see the Generation 2 Virtual Machine Overview.</br>
``If the new virtual machine is configured as Generation 2 and will be running a Linux distribution, secure boot will need to be disabled. For more information on secure boot, see Secure Boot.``

6. Select 2048 MB for the Startup Memory value and leave Use Dynamic Memory selected. Click the Next button.</br>
Memory is shared between a Hyper-V host and the virtual machine running on the host. The number of virtual machines that can run on a single host is in part dependent on available memory. A virtual machine can also be configured to use Dynamic Memory. When enabled, dynamic memory reclaims unused memory from the running virtual machine. This allows more virtual machines to run on the host. For more information on Dynamic Memory, see the Hyper-V Dynamic Memory Overview.

7. On the Configure Networking wizard, select a virtual switch for the virtual machine and click Next. For more information, see Create a Virtual Switch.

8. Give the virtual hard drive a name, select a location or keep the default, and finally specify a size. Click Next when ready.</br>
A virtual hard drive provides storage for a virtual machine similar to a physical hard drive. A virtual hard drive is required so that you can install an operating system on the virtual machine.</br></br>
![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/new_vhd_upd.png)

9. On the Installation Options wizard, select Install an operating system from a bootable image file and then select an operating system .iso file. Click Next once completed.</br>
When creating a virtual machine, you can configure some operating system installation options. The three options available are:</br>
**Install** an operating system later – this option makes no additional modification to the virtual machine.</br></br>
**Install** an operating system from a bootable image file – this is similar to inserting a CD into the physical CD-ROM drive of a physical computer. To configure this option, select a .iso image. This image will be mounted to the virtual CD-ROM drive of the virtual machine. The boot order of the virtual machine is changed to boot first from the CD-ROM drive.</br>
![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/Select%20iso%20with%20guid%20ui.PNG)
</br>
**Install** an operating system from a network-based installation server – This option is not available unless you have connected the virtual machine to a network switch. In this configuration, the virtual machine attempts to boot from the network.

10. Review the virtual machine details and click Finish to complete the virtual machine creation.

### Name change.

Next, after you powered up the Server we will set the Password.</br>
![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/PasswordSettings.png)

``NOTE: there are a few things we need to change here – first being Computer name (Nobody will remember that name if they needed to)
Click on Computer Name (The Blue text) this screen will show up – Click Change``

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/changeName01.png)

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/changeName02.png)

Type in the name that you want for this domain controller in the screen that comes up like below.

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/changeName03.png)

Click OK when done, and then close the screen behind – Reboot when it asks you to
Login to windows when ready and when Server Manager comes back up, click on Local Server again and validate the Name change 

Now let's validate that the internet is working so we can get some network settings written down. I went to www.bing.com and after the Internet Enhanced configuration prompts I was able to get to the internet.

Let's assign a static IP to the network card as you do not want the servers IP changing on you.

Open a command prompt and type "IPconfig". The resulting output will be  like below.

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/ipconfig.PNG)

The ipv4 address, subnet mask and the default gateway are the most important:
* Refer back to your router information and check the scope of address that it hands out: For instance Linksys routers hands out normally 192.168.1.100 to 192.168.1.150 (50 addresses). This is important to be able to assign an IP to your new server that is still on the network defined by the subnet mask but outside of the client scope, I am choosing 192.168.1.11 for my new domain controller for example.

* Right click this icon ![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/networksettingicone.png) on the taskbar and select "Open Network and Sharing Center"
* Select the "Change adapter settings" on the left
* Right click on your network adapter and select properties
* On the screen that comes up click "Internet Protocol Version 4 (TCP/IPv4) and then click the Properties button.

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/ipconfig02.png)

* Make your ip settings match mine with the exception of the IP address (If you selected another one) , Gateway depending on your routers config, and DNS most likely this will be your router if not refer back to the ipconfig /all output and have your dns settings match that. 

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/ipconfig03.png)
Once that's done lets validate that the internet still works

* Download and install all windows updates for the server – to do that right click the little flag icon by the clock and open the action center.
 On the left there will be a Windows Update link, click that and turn on Automatic Updating.
 Check for updates – this will take a bit to gather all of the updates that may be waiting for you.
 Go ahead and install any updates found and let the server reboot if it needs to. With the operating system being 2012 R2 there may not be a lot of updates.


---

Create Domain Controller
------------------------

<sup>[GoTo Top](#tfs-devlab)</sup></br>
Adding the Windows 2012R2 Server Domain Services Role.

Once the Server Manager has been opened, click on Manage and select Add Roles and Features.

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/DC.png)

Once the Add Roles and Features Wizard has started up, select Next.

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/DC02.png)

On the next page, the default settings can be used.

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/DC03.png)

Under server selection, the default settings should be selecting the domain control.

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/DC04.png)

On the Server Roles page, select Active Directory Domain Services.

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/DC05.png)

Windows will prompt for any additional features that will be needed.

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/DC06.png)

The next window will prompt with a few additional notes regarding best practices. Note that the Active Directory Domain Services Role will install the following in a new environment:
* DNS Services
* DFS Namespaces Services
* DFS Replication Services- Replication Services
* Group Policy Management

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/DC07.png)

The confirmation page will display all components that will be reinstalled. Note that on a new server, a reboot is not required to install the Active Directory Domain Services role.

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/DC08.png)

Once the installation has completed, this machine can be promoted to a domain controller.
In the top right corner, a warning label will now appear next to the task details icon. Click on this icon and select Promote this server to a domain controller.

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/DC09.png)

The Active Directory Domain Services Configuration Wizard will begin. In the example shown below, I am adding a new forest.

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/DC10.png)

Since the new server being deployed is going to replace one of the primary domain controllers, both DNS and Global Catalog were selected. Additionally, I used a Directory Services Restore Mode (DSRM) password that did not match the domain administrator. Although this password can match the domain administrator, I chose not to use the same password for security purposes. Make sure this password is documented as this password can help gain access to an environment in the event that all domain administrator accounts lose access.

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/DC11.png)

Since I was not using a parent zone, I got the following warning. In my case, I can ignore the warning as this will not affect whether the DNS feature gets installed.

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/DC12.png)

Additional options. The NetBIOS domain name is set. Click next.

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/DC13.png)

All the AD DS database, log files and SYSVOL data was left at their default locations.

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/DC14.png)

The next window will be a summary of all selected options. If anything needs to be adjusted, now would be the best time to do it. 

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/DC15.png)

Windows will perform a prerequisites check. If the user account used to promote the server does not have sufficient privileges (Schema Admin or Enterprise admin), then the installation will not be able to be completed. Either log onto another account that has the correct permissions or grant those permissions to the desired user and start over from the beginning of the promotion wizard. 

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/DC16.png)

Once the installation has been completed and the wizard has been closed out, the AD DS will reboot.

![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/DC17.png)



---

Join VM to Domain Controller
----------------------------

<sup>[GoTo Top](#tfs-devlab)</sup></br>
hoi

---

Install TFS
-----------

<sup>[GoTo Top](#tfs-devlab)</sup></br>
hoi

---

Create TFS Build VM
-------------------

<sup>[GoTo Top](#tfs-devlab)</sup></br>
hoi

---

Create TFS Release Management VM
--------------------------------

<sup>[GoTo Top](#tfs-devlab)</sup></br>
hoi

---

Create TFS Test Management VM
-----------------------------

<sup>[GoTo Top](#tfs-devlab)</sup></br>
hoi 

---

13
--

<sup>[GoTo Top](#tfs-devlab)</sup></br>
hoi

---

14 En
-----

<sup>[GoTo Top](#tfs-devlab)</sup></br>
hoi 2

---
