# Add NAS SMB/CFIS Share to Proxmox

<img width="256" height="256" alt="image" src="https://github.com/user-attachments/assets/288a7ef0-609c-4652-bb4d-6394a33fa23f" />

---

In this doc, we'll quickly go over adding my NAS (Terramaster F2-210) into Proxmox,
so we have additional storage to use.

---

## Terramaster NAS Setup

In our NAS, we'll enable SMB/CIFS File Service by going to:
**TOS (Terramaster Operating System) > Control Panel > File Service > SMB/CIFS File Service > Enable > *add domain if needed***

<img width="1157" height="469" alt="image" src="https://github.com/user-attachments/assets/fda0d8d9-ec56-4bb1-8d9a-c3dea4c67c76" />

We'll then go to: **Control Panel > Shared Folder > *Select Folder* > Edit > SMB**

Specify the Proxmox server or put '*' for all hosts:

<img width="777" height="583" alt="image" src="https://github.com/user-attachments/assets/a78db8d3-b165-4634-9204-00d39b303720" />

We'll also want to make sure the correct accounts have the correct permissions:

<img width="772" height="545" alt="image" src="https://github.com/user-attachments/assets/7e10b2c5-b426-4bb5-9e65-2ed90b60222e" />

## Add Folder to Proxmox

In Proxmox, we'll go to **Datacenter > Storage > Add > SMB/CFIS**

We'll fill in the details. 

Proxmox actually scans and detects and shares as well. 
Select the share:

<img width="852" height="509" alt="image" src="https://github.com/user-attachments/assets/bc48c40e-219d-4a1c-bfef-36db0b46ae58" />

Click Add and now we can see our TNAS share has been added to our Storage:

<img width="2552" height="486" alt="image" src="https://github.com/user-attachments/assets/761a181c-c8fe-4d37-a6d0-17db732227fd" />


# Use the Attached Storage

Now, if we go to create a Virtual Machine,
we can select our new SMB/CFIS share to use for the VM's virtual storage disk:

<img width="896" height="671" alt="image" src="https://github.com/user-attachments/assets/b1dda524-29dd-40c4-82f1-64b9594d0d34" />


