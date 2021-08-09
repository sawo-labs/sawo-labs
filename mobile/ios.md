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

4. SawoFramework is available through [CocoaPods](https://cocoapods.org). 

5. Create a new Xcode Project with a View Controller and create a login button and its action in the ViewController.swift file.

6. Open your project folder in terminal and type in 'pod init', then open the pod file of your project and add the following line to the pod file and save it.

```text
pod 'SawoFramework'
pod 'SwiftKeychainWrapper' 
```

7. Now go back to the terminal and type pod install to install the pod to your project. Once the pod has been installed xcworkspace file of your project and work on it.

8. Import the Framework and pod by adding the following code.

```text
import UIKit
import SawoFramework
import SwiftKeychainWrapper
```

9. Add the following snippet above viewDidLoad 

```text
let VC = SawoFramework.LoginViewController()
var PayloadApi = ""

var publicKeyApp = ""
var privateKeyApp = ""
var sessionIdApp = ""
    
var keychainPublicKEY = KeychainWrapper.standard.string(forKey: "publicKEY")
var keychainPrivateKEY = KeychainWrapper.standard.string(forKey: "privateKEY")
var keychainSessionID = KeychainWrapper.standard.string(forKey: "sessionID")
```

10. Add the following code snippet in your @IBAction func of the button

```text
present(VC, animated: true, completion: nil)
let apiKey = ["apikey": "ADD-YOUR-API-KEY"]
let identifierType = ["identifier": "ADD-YOUR-IDENTIFIER"]
let secretKey = ["secretkey": "ADD-YOUR-SECRET-KEY"]
let keychainPuK = ["keychainPuk": "\(String( keychainPublicKEY ?? "not found any"))"]
let keychainPrK = ["keychainPrk": "\(String( keychainPrivateKEY ?? "not found any"))"]
let keychainSess = ["keychainSess": "\(String( keychainSessionID ?? "not found any"))"]

print("on Login Pressed The values ....")
print(keychainPublicKEY)
print(keychainPrivateKEY)
print(keychainSessionID )

NotificationCenter.default.post(name: Notification.Name("ProductKey"), object: nil,userInfo: apiKey)
NotificationCenter.default.post(name: Notification.Name("IdentifierType"), object:nil, userInfo: identifierType)
NotificationCenter.default.post(name: Notification.Name("SecretType"), object:nil, userInfo: secretKey)
NotificationCenter.default.post(name: Notification.Name("keychainPuKFramework"), object: nil,userInfo: keychainPuK)
NotificationCenter.default.post(name: Notification.Name("ProductKeyFramework"), object: nil,userInfo: keychainPrK)
NotificationCenter.default.post(name: Notification.Name("keychainSessFramework"), object: nil,userInfo: keychainSess)

```

11. The following code in viewDidLoad func 

```text
NotificationCenter.default.addObserver(self, selector: #selector(LoginIsApproved(_:)), name: Notification.Name("LoginApproved"), object: nil)
NotificationCenter.default.addObserver(self, selector: #selector(loginCONTENTapi(_:)), name: Notification.Name("PayloadOfUser"), object: nil)

NotificationCenter.default.addObserver(self, selector: #selector(PublicKEYApp(_:)), name: Notification.Name("publickey"), object: nil)
NotificationCenter.default.addObserver(self, selector: #selector(PrivateKEYApp(_:)), name: Notification.Name("privatekey"), object: nil)
NotificationCenter.default.addObserver(self, selector: #selector(SessionIDApp(_:)), name: Notification.Name("sessionId"), object: nil)
```

12. Add a new View Controller to which you want to take your user after login. 

13. Create a Segue to this  View Controller and select its type as present modally. Inside Attributes inspector in presentation select full screen and give the segue a name an identifier.

14. Add the snippet below  `viewDidLoad func`

```text
@objc func LoginIsApproved(_ notification: Notification){
    print("Login was Successful")
    self.dismiss(animated: true, completion: nil)
    performSegue(withIdentifier: "Sawo", sender: nil)
    

}


@objc func loginCONTENTapi(_ notification: Notification){
    if let data = notification.userInfo as? [String: String]
        {
            for (UserPayload, Content) in data
            {
                PayloadApi = Content
                print("\(UserPayload) : \(Content) ")
            }
    }

}

@objc func PublicKEYApp(_ notification: Notification){
    if let data = notification.userInfo as? [String: String]
        {
            for (PublicKEYApps, valuePublic) in data
            {
                publicKeyApp = valuePublic
                print("\(PublicKEYApps) : \(valuePublic) ")
                KeychainWrapper.standard.set(valuePublic, forKey: "publicKEY")
            }
    }
}

@objc func PrivateKEYApp(_ notification: Notification){
    if let data = notification.userInfo as? [String: String]
        {
            for (PrivateKEYApps, valuePrivate) in data
            {
                privateKeyApp = valuePrivate
                print("\(PrivateKEYApps) : \(valuePrivate) ")
                KeychainWrapper.standard.set(valuePrivate, forKey: "privateKEY")
            }
    }
}

@objc func SessionIDApp(_ notification: Notification){
    if let data = notification.userInfo as? [String: String]
        {
            for (SessionIDApps, valueSessionID) in data
            {
                sessionIdApp = valueSessionID
                print("\(SessionIDApps) : \(valueSessionID) ")
                KeychainWrapper.standard.set(valueSessionID, forKey: "sessionID")
            }
        
    }
    

}
```

15. Add values to the places marked in the comments.

16. PayloadApi variable contains the user's payload.

**Congratulations !! The SAWO API is now ready to be used in your iOS application** 🤘**.**  

#### You can also check out SAWO's [iOS Sample Code](https://github.com/sawolabs/ios-sdk-demo).

#### It's okay, we get it! You got Stuck! 😞 Feel free to contact us on \#ask-for-help on our [Discord](https://discord.com/invite/TpnCfMUE5P)

