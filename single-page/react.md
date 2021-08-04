---
description: >-
  React is a free and open-source front-end JavaScript library for building user
  interfaces or UI components. Several useful mobile applications can be built
  through this library.
---

# React⚛️

### Let's Get your React App running with SAWO 🙌 

{% embed url="https://drive.google.com/file/d/1w2ZWJnSzGmZttq\_iOlh6HRn96iQhDak5/view" caption="Walk-through of SAWO\'s integration with React." %}

### You can also check [SAWO's React Sample Code](https://github.com/sawolabs/React-Sample-App) 

### **Requirements**

Node, Node Package Manager\(NPM\)

### **Steps**

1. The first step to getting started with SAWO API integration into your React web page is to **install the sawo** package as given below:

```text
npm i sawo
```

2. After installation is done, you have to **import the Sawo class** from the installed sawo package to the top of the file:

```text
import Sawo from "sawo"
```

3. To use SAWO Login you would need an API key which can be obtained by visiting [dashboard](https://dev.sawolabs.com/) of SAWO and creating a project.

4.  Once you create your project, you would need to set your **project name and host name** and ****this is one of the most important step.  
    a. For development in local machine, host name should be set to 'localhost'.

{% hint style="info" %}
If are ''localhost" as host name is not working for you, try "127.0.0.1" 🤓 
{% endhint %}

    ****b. For the production, host name should be set to your domain. 

{% hint style="info" %}
If you are adding your domain do not add 'https://' or ''http://'.   
**Example**
{% endhint %}

5. Copy the API key from the project and keep it safe and secure.

6. Initialise SAWO and render the form according to following steps:

```text
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

7. Once the SAWO SDK is successfully setup, a login form will be rendered in the provided container as displayed in the picture below:  
                                                          **add image.**

#### Yayy, you have successful implemented SAWO to your application 🤘 \(Experimental\)

#### We get it! You got Stuck! 😞 Feel free to contact us on \#ask-for-help on our [Discord](https://discord.com/invite/TpnCfMUE5P)

{% page-ref page="../faqs.md" %}

