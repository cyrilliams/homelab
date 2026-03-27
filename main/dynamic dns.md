# Dynamic DNS

Today, I'll quickly set up Dynamic DNS (DDNS) through NameCheap.

*Most people go through Cloudflare DDNS but I already have my domains with NameCheap*

---
## Setup DDNS Host A Records


We'll go to the Host Records portion of NameCheap,
and then find the DDNS section **or** add an 'A + Dynamic DNS Record'

My bare domain as well as a record with a '*' under the Host to specify all variations of my domain.

<img width="1442" height="548" alt="image" src="https://github.com/user-attachments/assets/bf1901da-9645-4367-aec2-0cb174641f9c" />


## Set Up Client Software

First, we'll want to enable DDNS in NameCheap.

It'll give us a password and then a client software download link.

<img width="1500" height="581" alt="image" src="https://github.com/user-attachments/assets/d8611593-2153-4d3a-85af-da0c72edca98" />

I'll put the Client on my Windows Server, which will always be running.

We'll get to this initial configuration page. We'll add a new profile:

<img width="1600" height="1052" alt="image" src="https://github.com/user-attachments/assets/dd7cf789-284a-4aab-9be0-7923f82a2009" />

We'll put in our domain, DDNS password which we got from the NameCheap admin portal,
click 'Auto detect my public IP address', and how often to update:

<img width="541" height="454" alt="image" src="https://github.com/user-attachments/assets/8d232196-48ad-4417-9fee-6336fc568c21" />

## Verify Change

This is the part that is time consuming because we have to wait for our ISP to hand us a new lease on a public IP.

Luckily, my public IP changes in about 2 hours, so I'll know if the NameCheap client updated by public IP or not:

<img width="914" height="1031" alt="image" src="https://github.com/user-attachments/assets/e1f598ce-4ce7-469c-a3ad-19e38a82e12c" />

These is my public IP before the renewal *(mostly covered for privacy and security)*


