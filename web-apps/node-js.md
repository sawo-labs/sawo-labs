---
description: >-
  Node.js is an open-source, cross-platform, back-end JavaScript runtime
  environment that runs on the V8 engine and executes JavaScript code outside a
  web browser.
---

# Node Js

### Let's Get your React App running with SAWO 🙌 

### **Requirements**

Node \[Version 12.x+ \] , Node Package Manager \(NPM\) \[Version 6.x+\]

### **Steps**

1. Install express by running

```text
npm install express
```

2. Make endpoints in `index.js` file and serve your HTML files

```javascript
const express = require("express");
const app = express();

const path = require("path");
app.use(express.static(path.join(__dirname, "public")));

app.get("/", (req, res) => {
  res.sendFile(__dirname + "/index.html");
});

app.get("/login", (req, res) => {
  res.sendFile(__dirname + "/public/login.html");
});

app.get("/success", (req, res) => {
  res.sendFile(__dirname + "/public/success.html");
});

app.listen("3000", console.log("Listening on port 3000."));
```

3. To use SAWO Login you would need an **API key** which can be obtained by creating a project in the [sawo dashboard](https://dev.sawolabs.com/). 

4.  Once you create your project, you would need to set your **project name and hostname.**  
    4.1. For **development** in a local machine, the hostname should be set to **'localhost'.**

{% hint style="info" %}
If using ''localhost" as hostname is not working for you, try "127.0.0.1" 🤓 
{% endhint %}

    ****4.2. For **production**, the hostname should be set to your **domain.** 

{% hint style="info" %}
If you are adding your domain do not add 'https://', ''http://', 'www' or even trailing backslash.  
**Example:**  
`https://dev.sawolabs.com/` should be kept as `dev.sawolabs.com`
{% endhint %}

5. Copy the **API key** from the project and keep it safe and secure.

{% hint style="info" %}
The best practice to store your API key is to store values in .env so that they are not exposed.
{% endhint %}

6. The body of the HTML login page should look like this for showing the SAWO login form:

```markup
<body>
  <div id="sawo-container" style="height: 300px; width: 300px"></div>

  <script src="https://websdk.sawolabs.com/sawo.min.js"></script>
  <script>
    // Fetching payload from sessionStorage
    const payload = sessionStorage.getItem("payload");
    if (payload) {
      // If the payload is available, that means the user has logged in already.
      // So redirecting back to "/login"
      window.location.href = "/success";
    }
    var config = {
      // should be same as the id of the container created on 3rd step
      containerID: "sawo-container",
      // can be one of 'email' or 'phone_number_sms'
      identifierType: "email",
      // Add the API key copied from 2nd step
      apiKey: "Your API Key",
      // Add a callback here to handle the payload sent by sdk
      onSuccess: (payload) => {
        // Storing the payload in sessionStorage
        sessionStorage.setItem("payload", JSON.stringify(payload));
        // Redirecting to "/success"
        window.location.href = "/success";
      },
    };
    var sawo = new Sawo(config);
    sawo.showForm();
  </script>
</body>
```

{% hint style="info" %}
You can store the payload to the sessionStorage, database, or integrate CRM and can take actions according to that.
{% endhint %}

7. Once the SAWO SDK is successfully set up, a login form will be rendered in the provided container as displayed in the picture below:

![Final Render of SAWO Login.](../.gitbook/assets/sawo-final-render%20%281%29.png)

{% hint style="success" %}
You can use the below code to verify if a user has successfully logged in or not.

```markup
<body>
  <h2 id="login" style="text-align: center">
    You Have Logged In Successfully !
  </h2>

  <script>
    // Fetching payload from sessionStorage
    const payload = sessionStorage.getItem("payload");
    // Checking if the payload is available or not
    if (payload) {
      // If the payload is available then console.log the payload
      console.log("Payload : " + payload);
    } else {
      // If the payload isn't available, that means the user hasn't logged in yet.
      // So redirecting back to "/login"
      window.location.href = "/login";
    }
  </script>
</body>
```
{% endhint %}

**Congratulations !! The SAWO API is now ready to be used in your Node application** 🤘**.**  

#### You can also check out SAWO's [Node Sample Code](https://github.com/sawolabs/nodejs-sample-app).

#### It's okay, we get it! You got Stuck! 😞 Feel free to contact us on \#ask-for-help on our [Discord](https://discord.com/invite/TpnCfMUE5P)

{% page-ref page="../faqs.md" %}

