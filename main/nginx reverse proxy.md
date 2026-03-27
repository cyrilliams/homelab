# Set Up a Reverse Proxy with NGINX

<img width="444" height="512" alt="image" src="https://github.com/user-attachments/assets/ffef70a9-666b-4ad3-8027-2c53d9382eb8" />

---

## Redirect Host

We're met with the initial setup screen after we hit the IP of NGINX at Port 81

``https://x.x.x.x:81``

<img width="1732" height="929" alt="image" src="https://github.com/user-attachments/assets/3a077b7e-037a-489f-a9e7-1e786d77f593" />

After deploying NGINX Reverse Proxy Manager,
we'll go to **Proxy Hosts > Add Proxy Host**

<img width="451" height="541" alt="image" src="https://github.com/user-attachments/assets/602ff687-b4eb-4c47-adef-aa1fa8d2f736" />

Let's also enable Websocket Support and Block Common Exploits

## SSL Certificate

I also want this site to be secured with an SSL Certificate.

We'll go to **SSL > Request a new Certificate**

<img width="454" height="329" alt="image" src="https://github.com/user-attachments/assets/761e295d-12e1-4f5e-bca4-24f5840fea2f" />

We'll also enable:
- Force SSL
- HTTP/2 Support

<img width="431" height="101" alt="image" src="https://github.com/user-attachments/assets/3246cdb1-7617-470d-b032-f04c4aab3219" />






## Add DNS Record

We'll go to our Domain registrar and add an A record (name to IP)

*I am using a Dynamic DNS + A record to update my Public IP when it renews from my ISP*

<img width="1466" height="354" alt="image" src="https://github.com/user-attachments/assets/edf58290-8ffe-4ca8-9792-8dd92eab308a" />

## Port Forward

Next, we'll need to setup Port Forwading in our router.

XFINITY sucks and makes you do it in the app:

<img width="797" height="1024" alt="image" src="https://github.com/user-attachments/assets/ecb31ddb-a781-4ff9-b880-6059487a6a7c" />

*Because NGINX is a WEB Proxy Manager, we'll forward Ports 443 (HTTPS) and Port 80 (HTTP) over to our NGINX container.*


## Visit The Site

If everything is configured properly, we should be able to go to our site and have a secure connection:

<img width="2541" height="1303" alt="image" src="https://github.com/user-attachments/assets/a95f7186-09cf-45bf-ae89-a9251900ddb5" />

We can even see the certificate is verified by Let's Encrypt:

<img width="475" height="391" alt="image" src="https://github.com/user-attachments/assets/73ad368c-e6f5-414e-a562-e1316fff06e2" />


