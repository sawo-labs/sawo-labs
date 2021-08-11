---
description: >-
  React is a free and open-source front-end JavaScript library for building user
  interfaces or UI components. A Component is one of the core building blocks of
  React.
---

# SAWO React Component

### Let's get your React Component running with SAWO 🙌 

### **Requirements**

Node \[Version 12.x+ \] , Node Package Manager \(NPM\) \[Version 6.x+\]

### **Steps**

1. The first step to getting started with SAWO API integration into your React web page is to **install the sawo-react** package as given below:

```javascript
npm i sawo-react
```

2. After installation is done, you have to import the SawoLogin class from the installed sawo package to the top of the file:

```javascript
import SawoLogin from 'sawo-react'
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

6. Initialize SAWO and render the form according to the following steps:

* Define a callback function

```javascript
function sawoLoginCallback(payload) {
        console.log(payload)
    }
```

* Make a config object. The code given below should help in the same.

```javascript
const sawoConfig = {
        onSuccess: sawoLoginCallback //required,
        identifierType: 'email' //required, must be one of: 'email', 'phone_number_sms',
        apiKey: '' // required, get it from sawo dev.sawolabs.com,
        containerHeight: '230px', // the login container height, default is 230px
    }
```

* Add the react component to the main page where the Login Component has to render. 

```javascript
<SawoLogin config={sawoConfig}/>
```

7.  Below code-block can be used as a reference **after** you have completed setting up your project:

```javascript
import React, { useEffect } from 'react'
import SawoLogin from 'sawo-react'

const LoginPage = () => {

    function sawoLoginCallback(payload) {
        console.log(payload)
    }
    
    const sawoConfig = {
        onSuccess: sawoLoginCallback //required,
        identifierType: 'email' //required, must be one of: 'email', 'phone_number_sms',
        apiKey: '' // required, get it from sawo dev.sawolabs.com,
        containerHeight: '230px', // the login container height, default is 230px
    }

    return (
        <div>
            <SawoLogin config={sawoConfig}/>
        </div>
    )
}

export default LoginPage
```

8. Once the SAWO SDK is successfully set up, a login form will be rendered in the provided container as displayed in the picture below:

![Final Render of SAWO Login](../.gitbook/assets/sawo-final-render%20%281%29.png)

**Congratulations !! The SAWO API Component is now ready to be used in your React application** 🤘**.**  

#### You can also check out SAWO's [Deployed App](https://sawo-react-sample-app.netlify.app/).

#### It's okay, we get it! You got Stuck! 😞 Feel free to contact us on \#ask-for-help on our [Discord](https://discord.com/invite/TpnCfMUE5P).

{% page-ref page="../faqs.md" %}

