---
description: >-
  iOS is a mobile operating system created and developed by Apple Inc.
  exclusively for its hardware.
---

# iOS

### Let's Get your iOS App running with SAWO 🙌 

### **Steps**

1. To use SAWO Login you would need an **API key** which can be obtained by creating a project in the [sawo dashboard](https://dev.sawolabs.com/). 

2.  Once you create your project, you would need to set your **project name and hostname.**  
    2.1. For **development** in a local machine, the hostname should be set to **'localhost'.**

{% hint style="info" %}
If using ''localhost" as hostname is not working for you, try "127.0.0.1" 🤓 
{% endhint %}

    **2**.2. For **production**, the hostname should be set to your **domain.** 

{% hint style="info" %}
If you are adding your domain do not add 'https://', ''http://', 'www' or even trailing backslash.  
**Example:**  
`https://dev.sawolabs.com/` should be kept as `dev.sawolabs.com`
{% endhint %}

3. Copy the **API key** from the project and keep it safe and secure.

{% hint style="info" %}
The best practice to store your API key is to store values in .env so that they are not exposed.
{% endhint %}

#### iOS CocoaPod Integration

1 iOS CocoaPod Integration

![](../.gitbook/assets/new-xcode-project.png)

2. Choose app in app templates.

![](../.gitbook/assets/select-app-template.png)

3. Add unique Bundle Identifier.

![](../.gitbook/assets/bundle-identifier.png)

4. Create an Apple Developer account ID and login.

5. Select Identifiers and click + icon.



6. Select App IDs in Certificates, Identifiers & Profiles Tab.

7. Select App as a type.

8. Add you bundle ID mentioned in the project created and description. Now select App groups in the capabilities.

9. 

**Congratulations !! The SAWO API is now ready to be used in your iOS application** 🤘**.**  

#### You can also check out SAWO's [iOS Sample Code](https://github.com/sawolabs/ios-sdk-demo).

#### It's okay, we get it! You got Stuck! 😞 Feel free to contact us on \#ask-for-help on our [Discord](https://discord.com/invite/TpnCfMUE5P)

