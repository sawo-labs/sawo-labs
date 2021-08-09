---
description: >-
  React Native is an open-source mobile application framework created by
  Facebook, Inc. It is used to develop applications for Android, Android TV,
  iOS, macOS, tvOS, Web, Windows and UWP.
---

# React Native

### Let's Get your React Native App running with SAWO 🙌 

### **Requirements**

[![Current version](https://img.shields.io/badge/npm%20package-1.0.0-blue)](https://www.npmjs.com/package/sawo) [![Supported React Native Version](https://img.shields.io/static/v1?logo=react&label=react-native&message=0.64.0&color=777bb4)](https://www.npmjs.com/package/react-native)react-navigation react-native-webview

### **Steps**

1. Check if react-naviation is properly installed, if not please follow [React navigation installation doc](https://reactnavigation.org/docs/getting-started/).

2. Check for 'react-native-webiew', it is required package for Sawo. As currently auto linking for package depencdy is not there in react-native.

```text
npm i react-native-webview
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

6. To get started with Sawo, use the npm to add the package to your project's dependencies:

```text
$ npm install react-native-sawo
```

**Configuration**

7. import Sawo package in your project

```javascript
import Sawo from 'react-native-sawo';
```

8. Configure your route.

```javascript
import {NavigationContainer} from '@react-navigation/native';
import {createStackNavigator} from '@react-navigation/stack';

<NavigationContainer>
    <Stack.Navigator>
        <Stack.Screen
          name="YOUR_LOGIN_ROUTE"
          component={Sawo}
          options={{
            title: 'OTP Login',
            headerShown: false, // by default its true, to hide the header
          }}
        />
    </Stack.Navigator>
</NavigationContainer>
```

9. then when calling route, we need to pass required credentials and a callback method to receive the user login data

```javascript
navigation.navigate('YOUR_LOGIN_ROUTE', {
    apiKey: 'YOUR_API_KEY',
    secretKey: 'YOUR_SECRET_KEY',
    identifierType: '', // email | phone_number_sms,
    callback: data => {}
});
```

**Congratulations !! The SAWO API is now ready to be used in your React Native application** 🤘**.**  

#### You can also check out SAWO's [React Native Sample Code](https://github.com/sawolabs/React-Native-Sample-App).

#### It's okay, we get it! You got Stuck! 😞 Feel free to contact us on \#ask-for-help on our [Discord](https://discord.com/invite/TpnCfMUE5P).

