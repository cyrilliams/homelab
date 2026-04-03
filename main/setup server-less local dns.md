# Set Up Server-less DNS with NGINX Reverse Proxy Manager & Cloudflare

In this doc, we will set up local DNS resolution with domain names for our network.

I want to be able to hit my container and docker images without always having to use the IP,
but I would also like access to these containers to be on my local network only, not public like some other containers.

Let's set that up now:

## Set DNS Records for NGINX

In Cloudflare, we'll want to set an A record to point to the IP of our NGINX Reverse Proxy Manager:

<img width="1253" height="671" alt="image" src="https://github.com/user-attachments/assets/1f382539-28a1-49ea-8ade-b3ebd2d3148e" />

We'll also add a CNAME record to cover all of our wildcard domains, so we can use nginx.cyriltest.site, if we wanted:

<img width="1252" height="622" alt="image" src="https://github.com/user-attachments/assets/7243ac1e-f24a-47ac-b288-24eebe8380f4" />

*Make sure to uncheck Proxy status*

## NGINX

Now we'll add the Proxy Host in NGINX:

<img width="557" height="663" alt="image" src="https://github.com/user-attachments/assets/e2a75313-6b70-4f05-8d16-16ddcd3736e6" />

Now we can use nginx.cyriltest.site to access our Nginx container! No IP and port number needed!

<img width="1920" height="1032" alt="image" src="https://github.com/user-attachments/assets/f99dd841-56ce-4a4c-b0b3-8a310450e2ba" />

## SSL/HTTPS

I like this setup, but I want our site to be secure.

### Cloudflare API Key

Back in Cloudflare, we'll go to **Account >  Account API tokens > Create Token > Edit zone DNS**

<img width="1910" height="866" alt="image" src="https://github.com/user-attachments/assets/0526d422-9d19-49dd-8543-c63ea18e8c53" />

We'll change Zone Resources to: Include, All Zones

<img width="1127" height="819" alt="image" src="https://github.com/user-attachments/assets/09f4afb8-3a51-43bb-b6f4-a3b86cea42e5" />

**Summary > Create Token**

<img width="1349" height="545" alt="image" src="https://github.com/user-attachments/assets/55de363e-6d85-45db-b745-fbb253a2f939" />


Now we have our Token:

<img width="1341" height="660" alt="image" src="https://github.com/user-attachments/assets/c6a34e8f-36ec-4b96-a40a-5e2cd2d7aa96" />

### NGINX SSL Setup

In NGINX, we'll setup an SSL Cert

**Certificates > Add Certificate > Let's Encrypt via DNS**

Add the records as well as choose the DNS provider and copy over the API key:

<img width="558" height="867" alt="image" src="https://github.com/user-attachments/assets/a0a3c69d-15e4-414e-ad08-ee7daf8ab445" />

The '*.' in front of our domain allows us to use all wildcards and subdomains

<img width="1270" height="69" alt="image" src="https://github.com/user-attachments/assets/86117916-9c1c-4086-b877-5393071219e7" />


### Add Cert to Host Proxy

We'll add that newly created SSL Cert:

<img width="530" height="384" alt="image" src="https://github.com/user-attachments/assets/a77a031b-9352-49a5-9e02-e5313411e15f" />


## Verify

### LAN and Internal Network

Let's click the link or enter our URL:

*After refreshing the page*

<img width="1920" height="1032" alt="image" src="https://github.com/user-attachments/assets/79f970b7-4a78-4ee8-aa8c-f3cedd6f326e" />

And now we can see it's verified by Let's Encrypt!


We can also Ping (while on the LAN):

<img width="1113" height="626" alt="image" src="https://github.com/user-attachments/assets/fe8c89e5-e738-4bc5-bb89-2f6061d7fc16" />

nslookup also returns the Local IP and alias:

<img width="1113" height="626" alt="image" src="https://github.com/user-attachments/assets/d0f08c5a-c5cf-443c-a2c8-19f5fc186a3d" />


### WAN and Public Network

Off the LAN, I cannot access my NGINX:

<img width="1349" height="547" alt="image" src="https://github.com/user-attachments/assets/b809b785-0244-482e-92f0-4f8b3907df2c" />


