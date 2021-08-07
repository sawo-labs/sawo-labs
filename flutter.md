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
  sawo: ^0.1.0
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

5.  Once you create your project, you would need to set your **project name and hostname.**  
    5.1. For **development** in a local machine, the hostname should be set to **'localhost'.**

{% hint style="info" %}
If using ''localhost" as hostname is not working for you, try "127.0.0.1" 🤓 
{% endhint %}

       ****5.2. For the **production**, the hostname should be set to your **domain**. 

{% hint style="info" %}
If you are adding your domain do not add 'https://', ''http://', 'www' or even trailing backslash.  
**Example:**  
`https://dev.sawolabs.com/` should be kept as `dev.sawolabs.com`
{% endhint %}

6. Copy the **API key** from the project and keep it safe and secure.

7. Next, **create** a **Sawo Instance**

```text
  Sawo sawo = new Sawo(
        apiKey: <YOUR-API-KEY>,
        secretKey: <YOUR-Secret-Key>,
     );
```

8. Use the following code to **redirect** the user to the **login** page.

```text
// Sawo configuration object
    var config = {};
    // user payload
    String user;
    void payloadCallback(context, payload) {
      if (payload == null || (payload is String && payload.length == 0)) {
        payload = "Login Failed :(";
      }
      setState(() {
        user = payload;
      });
    }

    void toogleState(typedata, text) => setState(() {
          config[typedata] = text;
        });

    @override
    Widget build(BuildContext context) {
      Sawo sawo;
      return Center(
        child: Column(mainAxisAlignment: MainAxisAlignment.center, children: [
          TextField(
            onChanged: (text) {
              toogleState("apiKey", text);
            },
            decoration:
                InputDecoration(hintText: 'API Key', labelText: 'API Key'),
          ),
          TextField(
            onChanged: (text) {
              toogleState("secretKey", text);
            },
            decoration:
                InputDecoration(hintText: 'SecretKey', labelText: 'SecretKey'),
          ),
          Text("UserData :- $user"),
          ElevatedButton(
            onPressed: () {
              Sawo sawo = new Sawo(
                apiKey: config["apiKey"],
                secretKey: config["secretKey"],
              );
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
              Sawo sawo = new Sawo(
                apiKey: config["apiKey"],
                secretKey: config["secretKey"],
              );
              sawo.signIn(
                context: context,
                identifierType: 'phone_number_sms',
                callback: payloadCallback,
              );
            },
            child: Text('Phone Login'),
          ),
        ]),
      );
    }

```

{% hint style="info" %}
When a user is successfully verified, the callback method will get invoked with the payload which contains userID and when something is wrong the payload will be null.
{% endhint %}

**Congratulations !! The SAWO API is now ready to be used in your Flutter application** 🤘**.**  

#### You can also check out SAWO's [Flutter Sample Code](https://github.com/sawolabs/flutter-sdk).

#### It's okay, we get it! You got Stuck! 😞 Feel free to contact us on \#ask-for-help on our [Discord](https://discord.com/invite/TpnCfMUE5P)

