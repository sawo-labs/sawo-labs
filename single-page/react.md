---
description: >-
  React is a free and open-source front-end JavaScript library for building user
  interfaces or UI components. It is maintained by Facebook. Several useful
  applications can be built through this library.
---

# React

### Let's Get your React App running with SAWO 🙌 

{% embed url="https://drive.google.com/file/d/1w2ZWJnSzGmZttq\_iOlh6HRn96iQhDak5/view" caption="Walk-through of SAWO\'s integration with React." %}

### **Requirements**

Node \[Version 12.x+ \] , Node Package Manager \(NPM\) \[Version 6.x+\]

### **Steps**

1. The first step to getting started with SAWO API integration into your React web page is to **install the sawo** package as given below:

```text
npm i sawo
```

2. After installation is done, you have to **import the Sawo class** from the installed sawo package to the top of the file:

```javascript
import Sawo from "sawo"
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
The best practice to store your API key is to store values in _.env_  so that they are not exposed.
{% endhint %}

6. Initialize SAWO and render the form according to the following steps:

* As part of this step, a **container** has to be created for the **SAWO component**. This has to be done on your project’s **source** file.

```markup
<div id="sawo-container" style="height: 300px; width: 400px;"></div>
```

* Some **configurations** have to be checked as given below. The code given below should help in the same.

```javascript
 var config = {
        // should be same as the id of the container created on 3rd step
        containerID: "<container-ID>",
        // can be one of 'email' or 'phone_number_sms'
        identifierType: "phone_number_sms",
        // Add the API key copied from 2nd step
        apiKey: "",
        // Add a callback here to handle the payload sent by sdk
        onSuccess: (payload) => {},
    };
```

* Then a **SAWO instance** has to be **created** using the code given below:

```javascript
let sawo = new Sawo(config)
```

* The **showForm** method should be called thereafter as the **showForm** method is responsible for rendering the form in the given container.

```javascript
sawo.showForm()
```

7.  Below code-block can be used as a reference **after** you have completed setting up your project:

```javascript
import React, { useEffect } from 'react'
import Sawo from 'sawo'

const LoginPage = () => {
    useEffect(() => {
        var config = {
            // should be same as the id of the container created on 3rd step
            containerID: '<container-ID>',
            // can be one of 'email' or 'phone_number_sms'
            identifierType: 'phone_number_sms',
            // Add the API key copied from 5th step
            apiKey: '',
            // Add a callback here to handle the payload sent by sdk
            onSuccess: payload => {
                // you can use this payload for your purpose
            },
        }
        let sawo = new Sawo(config)
        sawo.showForm()
    }, [])

    return (
        <div>
            <div id="sawo-container" style="height: 300px; width: 300px;"></div>
        </div>
    )
}

export default LoginPage
```

8. Once the SAWO SDK is successfully set up, a **login form** will be rendered in the provided container as displayed in the picture below:

![Final Render of SAWO Login.](../.gitbook/assets/sawo.png)

{% hint style="info" %}
We have another implementation that can be created as simple as an added [component](../additonal-content/react-component.md).
{% endhint %}

**Congratulations !! The SAWO API is now ready to be used in your React application** 🤘**.**  

#### You can also check out SAWO's [React Sample Code](https://github.com/sawolabs/React-Sample-App) and [Deployed App](https://sawo-react-sample-app.netlify.app/).

#### It's okay, we get it! You got Stuck! 😞 Feel free to contact us on \#ask-for-help on our [Discord](https://discord.com/invite/TpnCfMUE5P)

{% page-ref page="../additonal-content/what-to-do-with-your-payload.md" %}

{% page-ref page="../faqs.md" %}

