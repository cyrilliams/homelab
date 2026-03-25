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

