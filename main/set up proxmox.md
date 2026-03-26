# Set Up Proxmox Virtual Environment

In this doc, I'll try my best to show how I set up Proxmox.

## What Is Proxmox?

Proxmox is a free and open source Type 1 Hypervisor that allows me to run multiple
Virtual Machines, Containers, and various virtualized devices all on one machine.

Rather than buying 5 different devices to run 5 different operating systems, 
I can just run all 5 off of Proxmox.

## Prerequisites

1. Server or PC/Laptop
2. USB stick/boot device
3. Proxmox ISO
4. Rufus or a utility to create bootable media

## Create Bootable Drive

In this scenario, I'll create a bootable drive using Rufus.

I'll open Rufus,
select my USB drive,
select my ISO,
and click START

Rufus will delete everything on the drive and create a bootable drive for me to use on my soon-to-be server.

<img width="570" height="792" alt="image" src="https://github.com/user-attachments/assets/a196f3f3-1525-4ec4-a987-97966bf326dd" />

After 3 minutes and 56 seconds, 
Rufus has created our bootable media with the Proxmox image on it.

<img width="568" height="196" alt="image" src="https://github.com/user-attachments/assets/ca34e698-6b64-4b8d-b31a-0a65723a7548" />

Let's plug it in to our Server and boot into it.

## Boot into Proxmox ISO

We'll boot into BIOS and select our storage device with Proxmox on it!

*For the purpose of documentation, I've already installed and set up Proxmox, 
and will be replicating it on a Virtual Machine*

<img width="1281" height="957" alt="image" src="https://github.com/user-attachments/assets/865abe3e-3b91-49de-acbd-6e6cf6de0f38" />

We'll continue with the Graphical install:

In the first sections (after the EULA), we'll select which disk Proxmox will install to and how to set it up.

I'll use ext4:

<img width="1196" height="749" alt="image" src="https://github.com/user-attachments/assets/0f777e0c-64ef-4a56-9775-7091f9e33966" />


We'll set our admin password and email here:

<img width="1593" height="998" alt="image" src="https://github.com/user-attachments/assets/30f52b20-6a84-46e7-9a1e-e62b7a3df6a0" />

Nex't you'll set up the NIC (network interface card), IP and subnet (in CIDR notation), Gateway and DNS server (we can use Google's for now)

<img width="1199" height="750" alt="image" src="https://github.com/user-attachments/assets/fe54256f-399f-48d7-a834-7fdd1737db9c" />


### Fully Qualified Domain Name (FQDN)

It is important to note that the Hostname is asking for FQDN (Fully Qualified Domain Name).

So our examples of ```pve-test.cyriltest.site```, 
the hostname will be ``pve-test``
and our domain is ``cyriltest.site``

In Proxmox, we'll see the device name as just ``pve-test``


---

### Install & Access

We'll confirm the changes and Install:

<img width="1201" height="750" alt="image" src="https://github.com/user-attachments/assets/783fa651-65bf-4a66-b590-98eb27b1fd73" />

If everything has installed correctly,
we'll see Welcome to GRUB (Grand Unified Bootloader)

<img width="674" height="376" alt="image" src="https://github.com/user-attachments/assets/cc735a64-a9e8-481c-b4f8-0da12236a1f3" />

Give it a couple seconds and we will see this screen
which means our Proxmox VE has been installed successfully!

Let's hit that IP address and port number.

<img width="619" height="308" alt="image" src="https://github.com/user-attachments/assets/2179174b-8e64-44b9-8e21-0430fa2c515f" />


*You'll need to specify the port number. Ex. ``10.0.0.100:8006``*

We'll get this screen at first but thats okay! 
Our server doesn't have certificates setup yet. 

Click **Advanced > Proceed**

<img width="1918" height="994" alt="image" src="https://github.com/user-attachments/assets/7c6eabdc-c6d5-4524-90f4-be3d277c3b85" />

We are now on our Proxmox portal.

Our default login will be 

```
root

*password you set during the install*
```

Let's login and check our new Virtual Environment!

<img width="1919" height="994" alt="image" src="https://github.com/user-attachments/assets/37072226-1455-4e02-b5ef-7353386725e9" />

---

Now we can spin up Virtual Machines and Containers when needed. Have fun!
