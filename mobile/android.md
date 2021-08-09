---
description: >-
  Android software development is the process by which applications are created
  for devices running the Android operating system.
---

# Android

### Let's Get your React App running with SAWO 🙌

### Requirements  

[![](https://jitpack.io/v/sawolabs/Android-SDK.svg)](https://jitpack.io/#sawolabs/Android-SDK)\*\*\*\*

### Steps

1. Add following line to root build.gradle repositories block.

```text
maven { url 'https://jitpack.io' }
```

2. Add this to your app level build.gradle android block.

```text
    compileOptions {
         sourceCompatibility JavaVersion.VERSION_1_8
         targetCompatibility JavaVersion.VERSION_1_8
     }

     kotlinOptions {
         jvmTarget = '1.8'
     }
```

3. Add this to your app level build.gradle dependencies block

```text
implementation 'com.github.sawolabs:Android-SDK:0.1.8'
```

4. Sync your project.

5. To use SAWO Login you would need an **API key** which can be obtained by creating a project in the [sawo dashboard](https://dev.sawolabs.com/). 

6.  Once you create your project, you would need to set your **project name and hostname.**  
    6.1. For **development** in a local machine, the hostname should be set to **'localhost'.**

{% hint style="info" %}
If using ''localhost" as hostname is not working for you, try "127.0.0.1" 🤓 
{% endhint %}

    ****6.2. For **production**, the hostname should be set to your **domain.** 

{% hint style="info" %}
If you are adding your domain do not add 'https://', ''http://', 'www' or even trailing backslash.  
**Example:**  
`https://dev.sawolabs.com/` should be kept as `dev.sawolabs.com`
{% endhint %}

7. Copy the **API key** from the project and keep it safe and secure.

{% hint style="info" %}
The best practice to store your API key is to store values in .env so that they are not exposed.
{% endhint %}

8. Create an Activity in Android Studio to get login success response for this example lets assume it is CallbackActivity.

9. In your MainActivity add a button to login and add following code to its onclick handle.

**Java**

```text
import com.sawolabs.androidsdk.Sawo;

public void onClickLogin(View view) {
    new Sawo(
                this, 
                "", // your api key
                ""  // your api key secret
                ).login(
                "email", // can be one of 'email' or 'phone_number_sms'
                CallbackActivity.class.getName()  // Callback class name
        );
}
```

**Kotlin**

```kotlin
   import com.sawolabs.androidsdk.Sawo

   fun onClickLogin(view: View) {
           Sawo(
               this,
               "", // your api key
               ""  // your api key secret
           ).login(
               "email", // can be one of 'email' or 'phone_number_sms'
               CallbackActivity::class.java.name // Callback class name
           )
       }
```

10. Get the response payload in the CallbackActivity

**Java**

```java
import com.sawolabs.androidsdk.ConstantsKt;

Intent intent = getIntent();
String message = intent.getStringExtra(ConstantsKt.LOGIN_SUCCESS_MESSAGE);

// continue with your implementation
```

**Kotlin**

```kotlin
import com.sawolabs.androidsdk.LOGIN_SUCCESS_MESSAGE

val message = intent.getStringExtra(LOGIN_SUCCESS_MESSAGE)
// continue with your implementation
```

{% hint style="info" %}
**Recommended**: Verify the payload sent by sdk from your backend
{% endhint %}

Python example:

```python
import requests

data = {
    'user_id': payload_sent_from_sdk['user_id']
}
res = requests.post('https://api.sawolabs.com/api/v1/userverify/', data=data)
# Match the verification token in response with sdk payload
if res.status_code == 200:
    response_data = res.json()
    if response_data['verification_token'] \
                == payload_sent_from_sdk['verification_token']:
            # continue with your implementation for example add the user to your db
```

**Congratulations !! The SAWO API is now ready to be used in your Andriod application** 🤘**.**  

#### You can also check out SAWO's[ Andriod Sample Code\(Kotlin\)](https://github.com/sawolabs/Android-SDK).

#### It's okay, we get it! You got Stuck! 😞 Feel free to contact us on \#ask-for-help on our [Discord](https://discord.com/invite/TpnCfMUE5P)

