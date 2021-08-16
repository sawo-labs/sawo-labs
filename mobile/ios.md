---
description: >-
  iOS is a mobile operating system created and developed by Apple Inc.
  exclusively for its hardware.
---

# iOS

### Let's Get your iOS App running with SAWO 🙌 

### **Steps**

#### iOS CocoaPod Integration

1 iOS CocoaPod Integration

![](../.gitbook/assets/new-xcode-project.png)

2. Choose app in app templates.

![](../.gitbook/assets/select-app-template.png)

3. Add unique Bundle Identifier.

![](../.gitbook/assets/bundle-identifier.png)

4. Create an Apple Developer account ID and login.

5. Select Identifiers and click + icon.

![](../.gitbook/assets/add-identifier.png)

6. Select App IDs in Certificates, Identifiers & Profiles Tab.

![](../.gitbook/assets/app-ids.png)

7. Select App as a type.

![](../.gitbook/assets/select-app-template%20%281%29.png)

8. Add your bundle ID mentioned in the project created and description. Now select App groups in the capabilities.

![](../.gitbook/assets/select-app-groups-capabilty.png)

9. Go to signing and capabilities and select teams with apple developer account linked to it and. Click on capabilities button

![](../.gitbook/assets/select-apple-developer-account-in-team.png)

10. Select app groups in capabilities.

![](../.gitbook/assets/select-app-groups-in-capabilities.png)

11. Add App group - “ ”

![](../.gitbook/assets/add-app-group.png)

12. To use SAWO Login you would need an **API key** which can be obtained by creating a project in the [sawo dashboard](https://dev.sawolabs.com/). 

13. Copy the **API key** from the project and keep it safe and secure.

{% hint style="info" %}
The best practice to store your API key is to store values in .env so that they are not exposed.
{% endhint %}

14. SawoFramework is available through [CocoaPods](https://cocoapods.org).

15. Create a new Xcode Project with a View Controller and create a login button and its action in the ViewController.swift file.

16. Open your project folder in terminal and type in 'pod init', then open the pod file of your project and add the following line to the pod file and save it.

```text
pod 'SawoFramework
```

17. Now go back to the terminal and type pod install to install the pod to your project. Once the pod has been installed xcworkspace file of your project and work on it.

18. Import the Framework and pod by adding following code.

```text
import UIKit
import SawoFramework 
```

19. Add the following snippet above viewDidLoad func

```text
let VC = SawoFramework.LoginViewController()
var PayloadApi = ""

var publicKeyApp = ""
var privateKeyApp = ""
var sessionIdApp = ""

    
var keychainPublicKEY = ""
var keychainPrivateKEY = ""
var keychainSessionID = ""
```

20. Add the following code snippet in your @IBAction func of the button

```text
self.present(self.VC, animated: true, completion: nil)

let apiKey = ["apikey": "ADD-API-KEY-HERE"]
let identifierType = ["identifier": "ADD-IDENTIFIER-HERE"]
let secretKey = ["secretkey": "ADD-SECRET-KEY-HERE"]
        

var userDefaults = UserDefaults(suiteName: "group.Trusted.SawoLabs.onesignal")
if let testpublicKEY = userDefaults?.object(forKey: "publicKEY") as? String {
    //print("publicKEY : \(testpublicKEY)")
    keychainPublicKEY = testpublicKEY
}
if let testprivateKEY = userDefaults?.object(forKey: "privateKEY") as? String {
    //print("publicKEY : \(testprivateKEY)")
    keychainPrivateKEY = testprivateKEY
}
if let testsessionID = userDefaults?.object(forKey: "sessionID") as? String {
    //print("publicKEY : \(testsessionID)")
    keychainSessionID = testsessionID
}
        
let keychainPuK = ["keychainPuk": "\(String( keychainPublicKEY ))"]
let keychainPrK = ["keychainPrk": "\(String( keychainPrivateKEY ))"]
let keychainSess = ["keychainSess": "\(String( keychainSessionID ))"]


NotificationCenter.default.post(name: Notification.Name("ProductKey"), object: nil,userInfo: apiKey)
NotificationCenter.default.post(name: Notification.Name("IdentifierType"), object:nil, userInfo: identifierType)
NotificationCenter.default.post(name: Notification.Name("SecretType"), object:nil, userInfo: secretKey)
NotificationCenter.default.post(name: Notification.Name("keychainPuKFramework"), object: nil,userInfo: keychainPuK)
NotificationCenter.default.post(name: Notification.Name("ProductKeyFramework"), object: nil,userInfo: keychainPrK)
NotificationCenter.default.post(name: Notification.Name("keychainSessFramework"), object: nil,userInfo: keychainSess)

NotificationCenter.default.addObserver(self, selector: #selector(SessionIDApp(_:)), name: Notification.Name("sessionId"), object: nil)
```

21. The following code in viewDidLoad func 

```text
NotificationCenter.default.addObserver(self, selector: #selector(WebViewError(_:)), name: Notification.Name("WebViewError"), object: nil)
NotificationCenter.default.addObserver(self, selector: #selector(LoginIsApproved(_:)), name: Notification.Name("LoginApproved"), object: nil)
NotificationCenter.default.addObserver(self, selector: #selector(loginCONTENTapi(_:)), name: Notification.Name("PayloadOfUser"), object: nil)

NotificationCenter.default.addObserver(self, selector: #selector(PublicKEYApp(_:)), name: Notification.Name("publickey"), object: nil)
NotificationCenter.default.addObserver(self, selector: #selector(PrivateKEYApp(_:)), name: Notification.Name("privatekey"), object: nil)
NotificationCenter.default.addObserver(self, selector: #selector(SessionIDApp(_:)), name: Notification.Name("sessionId"), object: nil)

NotificationCenter.default.addObserver(self, selector: #selector(loginButtonWebView(_:)), name: Notification.Name("loginButtonPressed"), object: nil)

```

22. Add a new View Controller to which you want to take your user after login. Create a Segue to this View Controller and select its type as present modally. Inside Attributes inspector in presentation select full screen and give the segue a name in identifier.

23. Add the snippet below viewDidLoad func

```text
@objc func loginButtonWebView(_ notification: Notification){
//                DispatchQueue.main.asyncAfter(deadline: .now() + 6.0) {
//                self.dismiss(animated: true, completion: nil)
//                }
//        performSegue(withIdentifier: "InternetError", sender: nil)
}


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
                var userDefaults = UserDefaults(suiteName: "group.Trusted.SawoLabs.onesignal")!
                userDefaults.set("\(valuePublic)", forKey: "publicKEY")
                userDefaults.synchronize()

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
                var userDefaults = UserDefaults(suiteName: "group.Trusted.SawoLabs.onesignal")!
                userDefaults.set("\(valuePrivate)", forKey: "privateKEY")
                userDefaults.synchronize()

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
                var userDefaults = UserDefaults(suiteName: "group.Trusted.SawoLabs.onesignal")!
                userDefaults.set("\(valueSessionID)", forKey: "sessionID")
                userDefaults.synchronize()

            }
        
    }
    

}

@objc func WebViewError(_ notification: Notification){
    print("Web View Error Recorded")
    performSegue(withIdentifier: "InternetError", sender: nil)
}

}



```

24. Add values to the places marked in the comments.

25. PayloadApi variable contains the user's payload.

**Congratulations !! The SAWO API is now ready to be used in your iOS application** 🤘**.**  

#### You can also check out SAWO's [iOS Sample Code](https://github.com/sawolabs/ios-sdk-demo).

#### It's okay, we get it! You got Stuck! 😞 Feel free to contact us on \#ask-for-help on our [Discord](https://discord.com/invite/TpnCfMUE5P)

