---
description: >-
  Django is a high-level Python Web framework that aids in quick development and
  clean, realistic design. It reduces the hassle so we can focus on coding the
  app rather than reinventing the whole wheel.
---

# Django

### Let's Get your Django App running with SAWO 🙌 

{% embed url="https://drive.google.com/file/d/1MQYZemI7OuGxXqsIVjP3GyGjDmn8c25f/view" %}



#### **Requirements**

Python, pip 

**Steps**

1. The first step to getting started with SAWO API integration into your Django website/application is to **install the sawo** package as given below:

```text
pip install sawo
```

2. Next, you have to **import createTemplate, getContext, and verifyToken** methods from Sawo. The **getContext** method is used to create sawo dictionary object from data gain from Django Database. The ways to create the template and verify the token are given in subsequent steps.  


```text
from sawo import createTemplate, getContext, verifyToken
```

3. To use SAWO Login you would need an API key which can be obtained by creating a project in the [sawo dashboard](https://dev.sawolabs.com/). 

4.  Once you create your project, you would need to set your **project name and hostname.**  
    4.1. For **development** in a local machine, the **hostname** should be set to **'localhost'.**

{% hint style="info" %}
If using ''localhost" as hostname is not working for you, try "127.0.0.1"
{% endhint %}

 4.2. For the **production**, the **hostname** should be **set to your domain.** 

{% hint style="info" %}
If you are adding your domain do not add 'https://', "http://', 'www' or even trailing backslash.

**Example:**  
`https://dev.sawolabs.com/` should be kept as `dev.sawolabs.com`
{% endhint %}

5. Copy the **API key** from the project and keep it safe and secure

6. ****Getting Started with the Setup in Django

* First, create a template for SAWO password-less and OTP-less Authentication on your Django website. Use the code given below for the same:

```text
createTemplate("<filepath>")
#example
createTemplate("templates/partials")

```

* Next, you have to send this data required by \_sawo.html. The variable names used in \_sawo.html template are sawo.auth\_key, sawo.identifier and sawo.to Therefore, to send this data you have to create a JSON.

{% hint style="info" %}
**Note:**

* The "to" route should be a post route that can receive posted data.
* If you are not aware of how data is passed to templates in Django, it is suggested to look into it first.
{% endhint %}

There are two methods to do this:

**METHOD 1: SENDING STATIC DATA**

```text
context = {
        "sawo":{
                "auth_key": "<api_key>",
                "identifier": "email | phone_number_sms"
                "to": <route> #the route where you will receive
                the payload sent by sdk                 
        }
}

#example
context = {
        "sawo":{
                "auth_key": "785ha-hdjsdsd-799-ss345",
                "identifier": "email | phone_number_sms"
                "to": login               
        }
}

```

**METHOD 2: USING ADMIN AND DATABASE TO SAVE CONFIG FOR SAWO**  


Step 1: To begin, the **sawo api\_key** and an **identifier** have to be created from the admin dashboard. The following code can be used in the models of your app.

```text
class Config(models.Models):
    api_key = models.CharField(max_length=200)
    identifier = models.CharField(max_length=200)
    choices = [("email","Email"),("phone_number_sms","Phone")]

```

Step 2: Next, the **view.py** of the app has to be set up. Use the code given below for the same.

{% hint style="info" %}
Route should be the **receiving end** where you can handle **post** request
{% endhint %}

```text
from models import Config
from sawo import getContext

def <your_function>(request):
    config = Config.objects.order_by('-api_key')[:1]
    context = {
        "sawo" = getContext(config,<route>) #the route where you will receive
                the payload sent by sdk    
    }
        
#example

def index(request):
    config = Config.objects.order_by('-api_key')[:1]
    context = {
        "sawo" = getContext(config,"login") 
               
    }

```

**Verifying Token**

Once you are done with the login on the web page, **it sends the data to the backend as a payload.** To get the user verified, you can use the **verifyToken** function, which **returns** a **boolean**.  
**Note:** BACKEND CODE IS SAME FOR DJANGO AND FLASK

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

**Congratulations !! The SAWO API is now ready to be used in your Django application** 🤘**.**  

#### You can also check out SAWO's[ Django Sample Code](https://github.com/sawolabs/sawo-python-examples/tree/master/django) and [Deployed App.](https://github.com/sawolabs/sawo-python-examples/tree/master/django)

#### It's okay, we get it! You got Stuck! 😞 Feel free to contact us on \#ask-for-help on our [Discord](https://discord.com/invite/TpnCfMUE5P)

{% page-ref page="../faqs.md" %}

