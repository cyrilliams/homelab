# Mount/Add an Additional Storage Disk in Proxmox

In this scenario, I've added my Lenovo Thinkcentre M700 to my Proxmox cluster. 

The Thinkcentre has two disks:
1. A 256 Gb SSD that Proxmox boots off of
2. A 500 Gb HDD that is not being used.

I want to now add the HDD into Proxmox to be used for whatever storage needs I have

## Verify Additional Disk

In the portal, we'll go to **Datacenter > Thinkcentre (or the node you are configuring) > Disks**

<img width="2104" height="926" alt="image" src="https://github.com/user-attachments/assets/fe846e5f-1917-4a90-a715-44a7d4f60107" />

We can see I have two disks, the bottom being our boot drive and the top being our extra HDD, which is not mounted.

## Wipe and Initialize Disk

Now we'll wipe the disk (this will erase EVERYTHING on that disk)

<img width="371" height="261" alt="image" src="https://github.com/user-attachments/assets/a284c004-d25a-4513-97cf-97fe554bb91f" />

Now that it has been wiped, we get the option to 'Initialize DISK with GPT':

<img width="1556" height="264" alt="image" src="https://github.com/user-attachments/assets/81fed4b5-6590-4fe1-a58e-29b39aa60654" />

## Create Directory

Now, we'll create the directory on the disk.

We'll go to **Datacenter > Thinkcentre (or the node you are configuring) > Disks > Directory > Create Directory**

Choose the newly formatted disk:

<img width="1001" height="311" alt="image" src="https://github.com/user-attachments/assets/3a8f00b7-b5d8-44dc-a149-d24e8903c832" />

We'll select our filesystem and give it a name.

*I did ext4 which is better for smaller, less performance oriented drives like the one I am using*

<img width="410" height="294" alt="image" src="https://github.com/user-attachments/assets/4077caab-6246-4ead-95b8-6577691ddf39" />

Now we can see the disk was mounted if we go back to Disks:

<img width="1553" height="198" alt="image" src="https://github.com/user-attachments/assets/8e3789f3-9cd5-410f-ab42-7f7dc31eca9c" />


---

## Resources:

https://www.youtube.com/watch?v=tKD-dgSKBxU&t=31s
