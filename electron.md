---
description: >-
  Electron is a free and open-source software framework developed and maintained
  by GitHub. It allows for the development of desktop GUI applications using web
  technologies.
---

# Electron

### Let's Get your React App running with SAWO 🙌 

### **Steps**

1. To use SAWO Login you would need an **API key** which can be obtained by creating a project in the [sawo dashboard](https://dev.sawolabs.com/). 

2.  Once you create your project, you would need to set your **project name and hostname.**  
    2.1. For **development** in a local machine, the hostname should be set to **'localhost'.**

{% hint style="info" %}
If using ''localhost" as hostname is not working for you, try "127.0.0.1" 🤓 
{% endhint %}

    ****2.2. For **production**, the hostname should be set to your **domain.** 

{% hint style="info" %}
If you are adding your domain do not add 'https://', ''http://', 'www' or even trailing backslash.  
**Example:**  
`https://dev.sawolabs.com/` should be kept as `dev.sawolabs.com`
{% endhint %}

3. Copy the **API key** from the project and keep it safe and secure.

{% hint style="info" %}
The best practice to store your API key is to store values in .env so that they are not exposed.
{% endhint %}

4. On your source, create a container for sawo component inside `body` tag

```markup
<div id="sawo-container" style="height: 300px; width: 300px;"></div>
```

5. Include `sawo-electron.min.js` to your source, follow either of following method 1. If you have Content Security Policy enabled, download the `sawo-electron.min.js` using following command and include it in your root source directory

```bash
wget https://websdk.sawolabs.com/sawo-electron.min.js

```

{% hint style="info" %}
If you don't have Content Security Policy enabled, include `sawo-electron.min.js` in your source using

```markup
<script src="https://websdk.sawolabs.com/sawo-electron.min.js"></script>
```
{% endhint %}

6. Add the snippet at bottom of source inside `body` tag

```text
<script>
    var config = {
        // should be same as the id of the container created on 3rd step
        containerID: "sawo-container",
        // can be one of 'email' or 'phone_number_sms'
        identifierType: "phone_number_sms",
        // Add the API key copied from 2nd step
        apiKey: "",
        // Add a callback here to handle the payload sent by sdk
        onSuccess: (payload) => {
            console.log(payload)
        },
    };
    var sawo = new Sawo(config);
    sawo.showForm();
</script>
```

{% hint style="info" %}
**Recommended**: Verify the payload sent by sdk from your backend:

Python Example:

```text
import requests

data = {
   'user_id': payload_sent_from_sdk['user_id']
}
res = requests.post('http://api.sawolabs.com/api/v1/userverify/', data=data)
# Match the verification token in response with sdk payload
if res.status_code == 200:
   response_data = res.json()
   if response_data['verification_token'] \
               == payload_sent_from_sdk['verification_token']:
           # continue with your implementation for example add the user to your db
```
{% endhint %}

**Congratulations !! The SAWO API is now ready to be used in your React application** 🤘**.**  

#### You can also check out SAWO's [React Sample Code](https://github.com/sawolabs/React-Sample-App) and [Deployed App](https://sawo-react-sample-app.netlify.app/).

#### It's okay, we get it! You got Stuck! 😞 Feel free to contact us on \#ask-for-help on our [Discord](https://discord.com/invite/TpnCfMUE5P)

{% page-ref page="faqs.md" %}



