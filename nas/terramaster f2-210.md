# Terramaster F2-210 Setup

In this doc I'll briefly go over the set up and initizlization for my Terramaster F2-210 NAS that I found at Goodwill!

---

## Setup

Currently, the NAS is connected via ethernet to my network switch which is connected to the rest of my network.

I have two hard drives in there at both 6TB each.

```
HD00 - 6TB
HD01 - 6TB
```

I think I'll set up RAID 1 for redundancy.

Logically, it'll look like 1 drive of 6TBs but protect me if 1 drive goes down.

```
HDD00 - 6TB    ➡️: LOGICAL DRIVE 6TB
HDD01 - 6TB
  
```

---

## Initialize

We may be able to skip this step, but I'll first download TNAS PC from the Terramaster website:
https://support.terra-master.com/download/packages?product=F2-210

Once that installs, we can open and let is find our NAS,
*(assuming it is plugged in and powered on of course)*

<img width="1920" height="1008" alt="image" src="https://github.com/user-attachments/assets/0cd68c8f-eccf-45d7-a731-e1d0d7bd2bff" />

Next we can hit the IP address of the NAS. 

We'll get this nice welcome screen:

<img width="1920" height="1008" alt="image" src="https://github.com/user-attachments/assets/d6685473-6ae0-4fff-a74b-1ec8291741c3" />

It'll validate the drives in the NAS:

<img width="1920" height="1008" alt="image" src="https://github.com/user-attachments/assets/8e9bf941-89f1-4760-a550-d524a1f5fe15" />

After, it'll install TOS (Terramaster Operating System)

<img width="1920" height="1008" alt="image" src="https://github.com/user-attachments/assets/b4047af4-6244-436d-a3d3-7cb1721d8ad4" />


After it installs on the NAS and reboots, we'll get to the initial setup:

<img width="722" height="836" alt="image" src="https://github.com/user-attachments/assets/f99802c1-1a29-4437-922e-809efe546527" />

Next, it'll ask us how we want to create our Storage Pool and what RAID setup we would like to use.

I'll choose RAID 1:

<img width="921" height="412" alt="image" src="https://github.com/user-attachments/assets/2a1db45c-6745-491b-a848-0bbf68f77040" />


We'll create the Volume for the Storage Pool:

<img width="739" height="511" alt="image" src="https://github.com/user-attachments/assets/499b4a3c-6b83-40b5-a921-7c4ec6c28894" />

We'll also choose Ext4 for our file system:

<img width="729" height="193" alt="image" src="https://github.com/user-attachments/assets/1395923a-5bf3-434f-a3ac-a3a3a70db239" />

We'll confirm our settings and let is create our Storage Pool:

<img width="679" height="505" alt="image" src="https://github.com/user-attachments/assets/699b7006-f792-4d52-ac9d-40088a368e23" />


Once setup finishes, we can log in to our NAS:

<img width="1920" height="1008" alt="image" src="https://github.com/user-attachments/assets/1ab359f8-65b8-43b4-89c8-477e5d049df1" />


## Create a Network/Share Folder

In TOS, we'll go to **Control Panel > Shared Folder > Shared Folder > Create**

<img width="980" height="451" alt="image" src="https://github.com/user-attachments/assets/57900ade-c810-4645-9655-48887f360a97" />

We'll name it and give it a description; as well as choose the volume it'll be stored on.


<img width="932" height="526" alt="image" src="https://github.com/user-attachments/assets/671d9339-da2e-4c1e-93b9-b3ecafbe00ea" />


We can also encrypt the folder and set delete retention time here:

<img width="918" height="530" alt="image" src="https://github.com/user-attachments/assets/22c9b274-613f-469a-9931-42a255bba88d" />

Here we can set our user or group access:

<img width="927" height="519" alt="image" src="https://github.com/user-attachments/assets/398cf3fa-9fab-411f-a78c-55d6e4afb178" />

Now we see it's been created. 

<img width="984" height="458" alt="image" src="https://github.com/user-attachments/assets/edd18369-9200-4267-9a84-68532548eeb6" />


Let's try to get into it from a Windows machine.

In File Explorere, if we backslash into the IP address of the machine, 
we can see that it now asks for credentials:

<img width="570" height="778" alt="image" src="https://github.com/user-attachments/assets/27d8e332-e01b-4076-beaf-abad22572ffc" />


And we're in:

<img width="2134" height="321" alt="image" src="https://github.com/user-attachments/assets/d68759e0-71aa-495b-987c-1c2e7adf88d8" />

