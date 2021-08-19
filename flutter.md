---
description: >-
  Flutter is an open-source UI software development kit created by Google. It is
  used to develop cross-platform applications.
---

# Flutter

### Let's Get your Flutter App running with SAWO 🙌 

### Steps:

1. To get started with the integration of SAWO API on your Flutter App, add the **plugin** in **dependencies**:

```text
dependencies:
  sawo: ^0.1.2
```

2. After this, **install the plugin**, by running the mentioned command:

```text
flutter pub get
```

3. As part of the next step, **import the plugin into class** by using the code given below:

```text
import 'package:sawo/sawo.dart';
```

4. To use **SAWO Login** you would need an **API key** which can be obtained by creating a project in the [sawo dashboard](https://dev.sawolabs.com/). 

5.  Once you create your project, you would need to set your **project name.**

6. Copy the **API key** from the project and keep it safe and secure.

{% hint style="info" %}
It is always recommended to store your apiKey and secretKey in a .env file. Otherwise, create a separate .dart file and add it to the .gitignore. Just make sure that you are not exposing the keys publicly and also add them to the .gitignore before pushing the project to a public repo.
{% endhint %}

7. Next, **create** a **Sawo Instance**

```kotlin
    Sawo sawo = new Sawo(
        apiKey: <YOUR-API-KEY>,
        secretKey: <YOUR-Secret-Key>,
     );
```

8. Use the following code to **redirect** the user to the **login** page.

{% hint style="info" %}
SAWO provides two ways to authenticate users, one by email and one by phone number.
{% endhint %}

```kotlin
  // sawo object
  Sawo sawo = Sawo(
    apiKey: "Your API Key",
    secretKey: "Your Secret key",
  );

  // user payload
  String user = "";

  void payloadCallback(context, payload) {
    if (payload == null || (payload is String && payload.length == 0)) {
      payload = "Login Failed :(";
    }
    setState(() {
      user = payload;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Center(
      child: Padding(
        padding: const EdgeInsets.symmetric(horizontal: 20),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text("UserData :- $user"),
            ElevatedButton(
              onPressed: () {
                sawo.signIn(
                  context: context,
                  identifierType: 'email',
                  callback: payloadCallback,
                );
              },
              child: Text('Email Login'),
            ),
            ElevatedButton(
              onPressed: () {
                sawo.signIn(
                  context: context,
                  identifierType: 'phone_number_sms',
                  callback: payloadCallback,
                );
              },
              child: Text('Phone Login'),
            ),
          ],
        ),
      ),
    );
  }

```

{% hint style="info" %}
When a user is successfully verified, the callback method will get invoked with the payload which contains userID and when something is wrong the payload will be null.
{% endhint %}

**Congratulations !! The SAWO API is now ready to be used in your Flutter application** 🤘**.**  

#### You can also check out SAWO's [Flutter Sample Code](https://github.com/sawolabs/flutter-sdk/tree/master/example).

#### It's okay, we get it! You got Stuck! 😞 Feel free to contact us on \#ask-for-help on our [Discord](https://discord.com/invite/TpnCfMUE5P)

