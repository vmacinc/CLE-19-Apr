### CEG-4900 In class exercies April 19
Building your own Virtual cyber range.

### Background
Building your own testing environment is an invaluable skill for cyber security
professionals.  Whether its for mocking up a customer's environment to test 
exploits and scans, practicing/learning new skills, or investigating potentially 
malicious files or code, having an environment that is trivially easy to setup, 
lock down, and destroy is important.

In this in class exercise we will investigate using VirtualBox to set up a 
vulnerable web application for testing some of the skills learned in this course.

### Resources
* Your ParrotOS linux install
* [Ubuntu Server 18.04 `.iso`](http://releases.ubuntu.com/18.04/ubuntu-18.04.2-live-server-amd64.iso)
* [bWAPP (an extremely buggy web app)](http://www.itsecgames.com/)
* [Metasploitable 2 VM](https://sourceforge.net/projects/metasploitable/files/latest/download)

### Task 1 - Building a VM
To start with, make sure you have downloaded the [Ubuntu Server 18.04 `.iso`](http://releases.ubuntu.com/18.04/ubuntu-18.04.2-live-server-amd64.iso)
file.  We will be creating a virtual machine from scratch using this installation.
MD5SUM of this file should be `fcbcc756a1aa5314d52e882067c4ca6a *ubuntu-18.04.2-live-server-amd64.iso`

1. In VirtualBox click the `New` button to create a new VM.  If you name the VM 
   `Ubuntu-18.04` It should automatically switch the Type and Version fields to be
   Linux and Ubuntu respectively, if not select them and click `Next >`
2. Select an amount of Memory (RAM) to associate with this VM.  The default of
   1024MB should be sufficient.  Click `Next >`
3. Make sure the radio button by `Create a virtual hard disk now` is checked and click `Create`
4. Check the radio button by `VDI` and click `Next >`
5. Dynamically allocated is fine.  Click `Next >`
6. The defaults of File location and size should be fine (size should be 10GB).  Click `Create`
7. You should now see a Ubuntu-18.04 VM in virtual box in the Powered Off state.

### Task 2 - Configuring your VM
Your Ubuntu VM is still technically empty since we have not configured it fully 
or installed any Operating System yet.  Lets do that now.  With your Ubuntu-18.04
VM highlighted click on the Settings button:

1. Clicking on the storage tab on the left gives you access to two devices
   * IDE controller (optical drive)
   * Sata Controller (hard disk created early)
2. Select the empty icon under `Controller: IDE` and on the right next to 
   `Optical Drive` click on the Disk then click on `Choose Virtual Optical Disk File...`
3. Browse to your `ubuntu-18.04.2-live-server-amd64.iso` file and select it
4. Now select the `Network` tab on the far left.  This should bring up the 
   configuration for Adapter 1 which should be enabled by default.
5. Pay close attention to all of the options in the `Attached to:` menu.  Below
   is a summary [from the VirtualBox manual](https://www.virtualbox.org/manual/ch06.html).  
   * NAT:  If all you want is to browse the Web, download files, and view email
     inside the guest, then this default mode should be sufficient.  May have
     some limitations with windows file share services.
   * NAT Network: A NAT network is a type of internal network that allows 
     outbound connections
   * Bridged Adapter: This is for more advanced networking needs, such as 
     network simulations and running servers in a guest. When enabled, Oracle 
     VM VirtualBox connects to one of your installed network cards and 
     exchanges network packets directly, circumventing your host operating 
     system's network stack
   * Internal networking: This can be used to create a different kind of 
     software-based network which is visible to selected virtual machines, but 
     not to applications running on the host or to the outside world.
   * Host-only networking: This can be used to create a network containing the 
     host and a set of virtual machines, without the need for the host's 
     physical network interface. Instead, a virtual network interface, similar 
     to a loopback interface, is created on the host, providing connectivity 
     among virtual machines and the host.
   * Generic networking: Rarely used I'm not covering this here. 
   For this in class exercise we will be switching the network interface 
   settings around a bit, for now leave the network set to `NAT` since we need 
   internet access to install and configure our VM.  Later we will lock this down
   as necessary.

### Task 3 - 




