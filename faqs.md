# FAQs

### **I am getting a 'Something went wrong, Please Contact Admin' error, What should I do?**

This means your API key or hostname is incorrect. Verify the API key for your project, and follow the previous thread if it's a local setup.

### **What should the 'hostname' be during setup?** 

If you are doing a local setup, use 'localhost', and if that doesn't work, '127.0.0.1' should do the trick.

### **How do I change the background colour and border settings on the authentication page?**

You can change the button background colour from the developer dashboard under the design tab which also includes more customization. There is currently no option to customise the border, and we are working on more customization options.

### **Can I get help with integrating using Django?**

Here is an example of a sample Django application built using the pip package: Please go through the documentation for integration here: [Django-Sawo-Sample](https://github.com/sawolabs/Django_Sample_App)



### **\[React\] I get the message: TypeError: Cannot read property ‘appendChild’ of null. What should I do to fix this?**

You will have to use the useEffect hook.

### **I did not receive the OTP. Is there an option to resend it in the form?**

The OTP resend option automatically becomes available after 2 minutes**.**

### **When does the login session timeout?**

There is a default session cooldown set for all projects, which can be changed under Dashboard &gt; Advanced Configuration

### **Where can I find more customization options?**

Please check the Advanced Customization page under Dashboard

### **Is there a way to set colours through hex code?**

For now, only RGB input is allowed. You can however use the colour palette provided to do the same

### **After login, the container persists while disturbing the alignment of other page components? How do I remove it after completing authentication?**

We remove the form programmatically after successful login, however, the container created to host the form is not removed, you can just remove it by using the following snippet**:**

```text
var sawoContainer = document.getElementById("sawo-container");
sawoContainer..remove()
```

### **Is there a logout option? Are the sessions persistent?**

The sessions are not persistent. Logging out can be implemented by adjusting the session cooldown under Dashboard &gt; Advanced Configuration

### **What does SAWO return on successful login and how can I access the same?**

SAWO returns a payload after successful login from the user based on the identifier type you are using in your project. For example:

```text
{
    "user_id": "9d66202e-1cbe-45af-8880-6c38bca78ada",
    "created_on": "2020-09-03T11:00:49.702000Z",
    "identifier": "abc@gmail.com",
    "identifier_type": "email",
    "verification_token": "4MOKplNeRJjjOXdMDETcRFTgwWCHkP8iwU8R"
}

```

You can get this from console.log from the payload.

You can build a sample application, for instance, on React using the SAWO npm package.[ Here](https://sawo-react-sample-app.netlify.app/) is an example

Have a look at [_What can i do with my payload?_](additonal-content/what-to-do-with-your-payload.md)\_\_

### **\[Flask\] Could I please get some help with making an authentication system with Flask, Python?**

Please go through our Flask documentation reference [here](https://docs.sawolabs.com/sawo/frameworks/flask)

[Here](https://github.com/sawolabs/sawo-python-examples/tree/master/flask) is a sample application built using the SAWO pip package

### **How can I integrate SAWO in HTML apps?**

Please go through our web integration documentation reference [here](https://docs.sawolabs.com/sawo/web-sdk-integration)

[Here](https://github.com/sawolabs/html-example) is a sample HTML app integrated with SAWO

### **How can I delete a project I created from the Dashboard?**

It is currently not possible to delete a project, although you need not worry as there is no limitation on the number of projects that can be created.

### **\[React\] How can I redirect to another page within the app after authentication?**

If authentication is successful, you will receive a non-empty payload, after which you can redirect to any page you want. An example of a non-empty payload is

```text
{
    "user_id": "9d66202e-1cbe-45af-8880-6c38bca78ada",
    "created_on": "2020-09-03T11:00:49.702000Z",
    "identifier": "abc@gmail.com",
    "identifier_type": "email",
    "verification_token": "4MOKplNeRJjjOXdMDETcRFTgwWCHkP8iwU8R"
}

```

If the payload returned is empty, please check for errors in the authentication.  
  
  
****  


  
  
  


###  

###  



