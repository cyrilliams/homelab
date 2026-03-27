#VPN Using WireGuard (with WG Dashboard)

<img width="250" height="250" alt="image" src="https://github.com/user-attachments/assets/07a9c493-3ce8-4c0a-9382-aa198cb46ce8" />

---

In this doc, we'll set up Wireguard, a self hosted VPN service.

---
## Setup

The default login is:

```
admin
admin
```

I've already spooled up WireGuard and installed WGDashboard:

<img width="2560" height="1380" alt="image" src="https://github.com/user-attachments/assets/f6f8ff25-9042-4752-b82a-c2375b4c3c76" />

We'll go to 'Peer Settings' and the only thing I'll change is the 'Peer Remote Endpoint'

<img width="1739" height="780" alt="image" src="https://github.com/user-attachments/assets/8c16ef0a-f495-4b9d-a363-f738d9e7d4fc" />


## wg0

We'll want to set up our WireGuard wg0 configuration.

The first thing we'll want to do is create a Peer.

We'll click 'Peer'

The only thing here we need to really do is name the Peer:

<img width="1202" height="828" alt="image" src="https://github.com/user-attachments/assets/ce74ee24-ea30-409a-a70e-e279b4349eb1" />

*You can change the IP if you'd like.*

For wg0, I'll update the subnet/address wg0 will use:

<img width="2126" height="1213" alt="image" src="https://github.com/user-attachments/assets/36f97b6d-dd4c-4002-b1ea-3cde07927f86" />

I'll update the Peer's address as well:

<img width="707" height="327" alt="image" src="https://github.com/user-attachments/assets/9be81f15-6091-4d68-82ee-4c1287f811e1" />


## Share Config File with Peer

WireGuard requires you to upload a config file to connect to WireGuard.

In the Peer panel, we'll click the ... and click the download button to download the config file.

We can upload or share the config file to your client computer.

***On the client/remote computer***

<img width="425" height="290" alt="1" src="https://github.com/user-attachments/assets/e69949bd-90f1-47e6-8df7-1090226e960d" />

We'll also need to install the [WireGuard client](https://www.wireguard.com/install/):

<img width="497" height="389" alt="2" src="https://github.com/user-attachments/assets/5c788e88-60f8-41eb-a600-455f898c12b0" />

Import the config file:

<img width="957" height="750" alt="image" src="https://github.com/user-attachments/assets/d8e9c22d-9ad7-42ec-8ddc-775682afabd8" />


---

## DNS Setup

Before we enable wg0 and test, we need to configure our DNS and Public IP settings.

We'll want to map the our endpoint to our Public IP and then enable Port Forwarding to hit wg0.

### Domain & DDNS

In my Domain registrar, I'll set DDNS A record:

<img width="1454" height="560" alt="image" src="https://github.com/user-attachments/assets/6e4626f5-58ef-4380-92df-ba2c4e9405b4" />

### Port Forwarding

In your router, you'll want to enable the port to be forwarded to the WireGuard container at the proper port [51820]

XFINITY sucks and I have to enable and configure Port Forwarding on my phone,
but this is the config:

<img width="828" height="623" alt="image" src="https://github.com/user-attachments/assets/2fdae65f-0f52-431e-9642-c6994fe6a0be" />

Now, traffic not on my network will be sent to my Public IP > My Router > WireGuard

---

## Test & Verify

Back on the client computer, we'll switch to a different network than our LAN.

I'm using my phone hotspot for now:

<img width="276" height="125" alt="4" src="https://github.com/user-attachments/assets/18cecd39-a8eb-4e21-b093-b9b0cafeec80" />

Before we activate the VPN, let's try to ping our WireGuard container:

<img width="677" height="380" alt="5" src="https://github.com/user-attachments/assets/2b3e2261-f82e-4ecf-b6cc-d77c75bf1385" />

Now that we know it doesn't work,
let's activate the VPN and test it:

<img width="960" height="746" alt="image" src="https://github.com/user-attachments/assets/49f8c468-e351-4235-97b3-73f4f46ed0c8" />

It's active and we can now ping our WireGuard container, which we could not do before:

<img width="677" height="380" alt="7" src="https://github.com/user-attachments/assets/3b42df34-a6be-4e46-86cb-28468ad5b9c8" />

We can even get onto our NAS file share, which is on a different subnet:

<img width="686" height="446" alt="8" src="https://github.com/user-attachments/assets/eccae680-3a91-4871-90e7-b4257b63c421" />

*I did not configure DNS so I was not able to use the host name of the NAS*

Here is the IP of the remote machine:

<img width="461" height="233" alt="9" src="https://github.com/user-attachments/assets/f3450dd5-86d2-4acc-8eea-21fb6ebae0ed" />

### Server/Container Side

We can see that traffic is being recieved:

<img width="2107" height="1215" alt="image" src="https://github.com/user-attachments/assets/01f8084b-372f-46a1-87da-de057a37823f" />

And peer1 is active:

<img width="709" height="314" alt="image" src="https://github.com/user-attachments/assets/1a758492-8f03-47a2-a8c5-ad70c21361e6" />


---

## Troubleshooting & Resources


### Troubleshooting

If you've added a peer or turned on wg0 without setting it up properly,
it will lock you out.

To undo this, in the console of Proxmox, verify and run these commands:

```
wg show
```
<img width="684" height="126" alt="image" src="https://github.com/user-attachments/assets/1d3f991d-7ba1-4d8f-a5f3-bd576ae97e5e" />

Then run this to stop wg0:
```
wg-quick down wg0
```

<img width="1509" height="200" alt="image" src="https://github.com/user-attachments/assets/c65c0b7c-18d8-445d-beb7-616ac606ee25" />


You can then verify if wg0 is running by using ```wg show``` again


### Resources I Used:

https://www.youtube.com/watch?v=SRa76aFFK3Y


