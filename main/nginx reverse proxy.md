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

<img width="1161" height="572" alt="image" src="https://github.com/user-attachments/assets/152e627b-5a19-4621-b2a8-b487a0c08c13" />


