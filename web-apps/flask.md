---
description: >-
  Flask is a micro web framework written in Python. It is classified as a micro
  framework because it does not require particular tools or libraries.
---

# Flask

### Let's Get your Flask App running with SAWO 🙌 

{% embed url="https://drive.google.com/file/d/1F\_iUAHXDET5KQx-7Kd-RnlviUGzqgGjr/view?usp=sharing" %}



### Requirements

Python, pip \(package-management system written in Python used to install and manage software packages\)

### Steps

1. The first step to getting started with SAWO API integration into your Django website/application is to **install the sawo** package as given below:

```text
pip install sawo
```

2. Next, you have to import **createTemplate**, **getContext,** and **verifyToken** methods from Sawo. The **getContext** method is used to create sawo dictionary object from data gain from Django Database. The ways to create the template and verify the token are given in subsequent steps.

```text
from sawo import createTemplate, getContext, verifyToken
```

3. To use SAWO Login you would need an API key which can be obtained by creating a project in the [sawo dashboard](https://dev.sawolabs.com/). 

4.  Once you create your project, you would need to set your **project name and hostname.**  
    4.1. For **development** in a local machine, the hostname should be set to **'localhost'.**

{% hint style="info" %}
If using ''localhost" as hostname is not working for you, try "127.0.0.1"  
{% endhint %}

   4.2. For **production,** the hostname should be set to your **domain**. 

{% hint style="info" %}
If you are adding your domain do not add 'https://', ''http://', 'www' or even trailing backslash.  
**Example:**  
`https://dev.sawolabs.com/` should be kept as `dev.sawolabs.com`
{% endhint %}

5. Copy the **API key** from the project and keep it safe and secure.

6. Getting Started with the Setup in Flask:

* First, you have to **create a template** for SAWO password-less and OTP-less Authentication for your Flask website. Use the code given below for the same:

  ```text
  createTemplate("./<filepath>",flask=True)
  #example
  createTemplate("./templates/partials",flask=True)
  ```

* Next, you have to send this data required by **\_sawo.html.** The variable names used in **\_sawo.html** template are **sawo.auth\_key**, **sawo.identifier** and **sawo.to** Therefore,to send this data you have to create a **JSON**.

{% hint style="info" %}
**Note:**  
The "to" route should be a post route that can receive posted data.  
If you don’t know how data is passed to templates in Django or Flask. We will suggest looking into it first
{% endhint %}

**METHOD USING ADMIN AND DATABASE TO SAVE CONFIG FOR SAWO**

*  Creating fields for **sawo api\_key** and identifier to set it from **admin** dashboard. Copy this code in models of your app

```text
class Config(models.Models):
    api_key = models.CharField(max_length=200)
    identifier = models.CharField(max_length=200)
    choices = [("email","Email"),("phone_number_sms","Phone")]
    
```

* Setting up **view.py** of the app. Note: Route should be the receiving end where you can handle post request

```text
from models import Config
from sawo import getContext

def <your_function>(request):
    config = Config.objects.order_by('-api_key')[:1]
    context = {
        "sawo" = getContext(config,<route>) #the route where you will recieve
                the payload sent by sdk    
    }
    
    
#example

def index(request):
    config = Config.objects.order_by('-api_key')[:1]
    context = {
        "sawo" = getContext(config,"login") 
               
    }
```

**FLASK**

```text
"sawo":{
       "auth_key": "<api_key>",
       "identifier": "email | phone_number_sms"
       "to": <route> #the route where you will recieve the payload sent by sdk                 
 }
 
 #example
 
 "sawo":{
        "auth_key": "785ha-hdjsdsd-799-ss345",
        "identifier": "email | phone_number_sms"
        "to": login               
}
```

**Verifying Token** 

When the login is done on the webpage it sends the data to **backend as a payload** to verify user, you can use **verifyToken** function, which returns a boolean.

BACKEND CODE IS THE SAME FOR DJANGO AND FLASK

```text
from sawo import verifyToken

#use the method provided by flask and django to receive the 
#data from post request the use this function it will return 
#True or False depending on user status
verifyToken(payload)

//example 
payload = <data from POST request>
if(verifyToken(payload)):
    #do something
else:
    #do something else
```

**Congratulations !! The SAWO API is now ready to be used in your Flask application** 🤘**.**  

#### You can also check out SAWO's [Flask Sample Code](https://github.com/sawolabs/sawo-python-examples/tree/master/flask) and [Deployed App](https://github.com/sawolabs/sawo-python-examples/tree/master/flask).

#### It's okay, we get it! You got Stuck! 😞 Feel free to contact us on \#ask-for-help on our [Discord](https://discord.com/invite/TpnCfMUE5P)

{% page-ref page="../faqs.md" %}

