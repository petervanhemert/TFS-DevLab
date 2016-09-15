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
* [Create Domain Controller](#)</br>
* [Join VM to Domain Controllerr](#)</br>
* [Install TFS](#)</br>
* [Create TFS Build VM](#)</br>
* [Create TFS Release Management VM](#)



* [Top](#tfs-devlab)

---

Install Hyper-V on windows 10  ###[Top](#tfs-devlab)
-------------
1. Right click on the Windows button and select ‘Programs and Features’.

2. Select Turn Windows Features on or off.

3. Select Hyper-V and click OK.
 
![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/enable_role_Hyper-V.png)

---

Create a Virtual Switch.  ###[Top](#tfs-devlab)
------------------------
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

Create a Virtual Machine with Hyper-V Manager.  [Top](#tfs-devlab)
----------------------------------------------

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
**Install** an operating system from a bootable image file – this is similar to inserting a CD into the physical CD-ROM drive of a physical computer. To configure this option, select a .iso image. This image will be mounted to the virtual CD-ROM drive of the virtual machine. The boot order of the virtual machine is changed to boot first from the CD-ROM drive.</br></br>
**Install** an operating system from a network-based installation server – This option is not available unless you have connected the virtual machine to a network switch. In this configuration, the virtual machine attempts to boot from the network.

10. Review the virtual machine details and click Finish to complete the virtual machine creation.

Create Domain Controller.   [Top](#tfs-devlab)
------------------------





