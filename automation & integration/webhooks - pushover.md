# Set Up a Webhook with Pushover

In this doc, we'll set up a webhook using Pushover.

## Set Up Pushover

We'll set up our Pushover account.
For now, I'm starting with a trial.

<img width="1148" height="894" alt="image" src="https://github.com/user-attachments/assets/307ac125-b102-4777-9a75-bf61f674f3c0" />

## Create Application

We'll first need to create an Application.

<img width="1347" height="311" alt="image" src="https://github.com/user-attachments/assets/bbd4d399-fa6f-4a58-b1e6-2635e4ca62f6" />

This part is easy. 
We just need to name our app, give it a description, and icon.

<img width="1173" height="656" alt="image" src="https://github.com/user-attachments/assets/2f67a872-fa4d-4915-9fb7-4b308a096618" />

Now we have an app with an API key.

<img width="1181" height="328" alt="image" src="https://github.com/user-attachments/assets/96909cc3-9032-4789-821d-fde765e9180e" />

Let's create the Webhook:

<img width="1138" height="121" alt="image" src="https://github.com/user-attachments/assets/09854be7-2150-4a3d-91f4-e0ac9df7453d" />

Click 'Create' and give the webhook a name:

<img width="1245" height="835" alt="image" src="https://github.com/user-attachments/assets/6f03638d-8881-459e-b16e-9b4549a30730" />

Here you can select the notification settings:

<img width="1145" height="734" alt="image" src="https://github.com/user-attachments/assets/e16ba8fb-9c8e-4c74-beb0-fb3af69deeb8" />

We'll click 'Create' just to generate a link:

<img width="1321" height="214" alt="image" src="https://github.com/user-attachments/assets/1a236966-ec16-4753-8a55-e498cef17e19" />


## Github Webhook Integration

To add the Webhook into Github,
we'll go to our **Repo > Settings > Webhooks > Create**


<img width="1006" height="755" alt="image" src="https://github.com/user-attachments/assets/58a0e625-f034-490b-941a-40506c59c8bf" />


We'll select 'application/json' as well for 'Content type'


<img width="754" height="75" alt="image" src="https://github.com/user-attachments/assets/253b1890-41e5-4b2b-9d71-4101f1484506" />


Also select the Webhook events and Add:

<img width="749" height="290" alt="image" src="https://github.com/user-attachments/assets/8e11798d-20a3-47ab-9b13-fb3aa5fb6190" />

Github now will send a test payload, let's check it out:

<img width="1008" height="51" alt="image" src="https://github.com/user-attachments/assets/c319348e-499b-455c-8478-3fe6d09d6706" />


In Pushover, if we click 'Check for Update', 
we should now see an updated Payload JSON:

<img width="1135" height="333" alt="image" src="https://github.com/user-attachments/assets/bb11ef00-0085-4d61-85a9-d79222e64537" />

We will not get notifications because we have not configured the 'Body Selector'. Lets do that now.


## Configure Data Extraction

The only thing I'll configure is the 'Body Selector' which will esentially be the body of the notifcation.
This will stem from the Payload JSON.

I'll configure the following things:

Title Selector: ``` $.repository.full_name```

Body Selector: `` $.zen``

URL Selector: ``$.repository.html_url``

URL Title Selector: ``$.repository.name``

We can use the Test Selectors button to verify they match the Payload

<img width="993" height="799" alt="image" src="https://github.com/user-attachments/assets/28cfbd8a-908e-4903-a231-6ebec3171295" />

We can see that it not only matches but gives me what I will see in my notifications.

Let's test it out on my phone:


