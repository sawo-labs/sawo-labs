---
description: >-
  In this article, we look at the widely prevalent multi-factor authentication
  mechanism and pit it up against the newer passwordless authentication method
  to see which one works better.
---

# SAWO vs Social Login

SSO was created for IT managers who found remembering IDs and passwords for hundreds of IT services, servers, and corporate applications to be difficult. They may use a single password and user ID to access various services on the corporate network thanks to SSO. In recent years, SSO has made its way to the web for consumers. If you log into Gmail, for example, you may open other Google services \(in other browser tabs\) without having to log in again. Gmail credentials may be used for Google Drive, Google Maps, Google Photos, and other Google services. As a result, SSO solutions are extremely useful since they eliminate the need for end-users to remember numerous passwords.

Third-party online services extend SSO by using plug-ins, widgets, and APIs to interact with social networking sites. For authorisation, SSO for consumer websites employs the OAuth industry standard. Customers can use their social network accounts to sign into third-party websites/online services. This is intended to make logins easier for end-users while also providing more trustworthy demographic data to site developers. Users have difficulty remembering numerous login IDs and passwords. So why not utilize something they're already familiar with? That sounds great until your social media account is hacked and taken over.

The University of Illinois at Chicago did a study on the top one million websites according to Alexa in 2018. According to the survey, 6.30 percent of websites support SSO. That was two years ago, and the figure is now substantially greater. This demonstrates the scope of the issue, since attackers may acquire access to a vast array of web services simply by obtaining one's social network credentials.

**How Social Logins work**

* The end-user goes to a third-party website \(relying party or RP\) and chooses the preferred social network provider \(Identity Provider\) for login.
* A login request is issued to the identity provider in question \(IdP\).
* This allows the user to log in to the RP's website or service once the IdP validates the user's identity with an access token or authorization code.
* When a user logs in for the first time, they are registered as a new user and then signed in to the program.

**SSO tech is not perfect**

Even though Logging in with a familiar whose credentials you easily remember saves you the trouble of going through yet another process of account creation and memorizing dozens of passwords. But what exactly are you signing up for?

Many potential difficulties exist with SSO systems, which are far from ideal and have a number of shortcomings. According to experts at the University of Illinois in Chicago, SSO technology can "offer a significant security concern". A proof-of-concept assault against Facebook was developed by the researchers, in which they were able to totally take over a user's account. "By using a Facebook account that has been hacked, an attacker may indirectly compromise 226 other online sites."

To quote from the research paper: “Due to the proliferation of SSO, user accounts in identity providers are now keys to the kingdom and pose a massive security risk. If such an account is compromised, attackers can gain control of the user’s accounts in numerous other web services.”

Logging in with Google or Facebook allows the website to request data that revolves around you

* -The exact data that the website is requesting for pops up in a window asking for permission. Saying yes to that request narrows downs the road of your data and third-party websites. -Allowing one account to have access to others means that if the least secure account is hacked, the rest could also be compromised.
* -If a trusted source of your identity is less secure — whether that's Facebook, Google, or another account — they risk becoming the weak link in the chain that gets targeted by attackers.
* -Slapdash sites may do something else with your data than what you agreed to —selling it to a third or fourth company that you do not want to hold any aspect of your online identity. -Google and Facebook provide a possession-based SDK.
* -Possession Based Authentication comprises anything that a user must have to log in. OTP token, key fobs, ID cards, smart cards, and physical tokens. Before signing into a site with your existing social account, make sure you trust the third-party site.

### **Passwordless Authentication: A solution to these issues?**

Passwordless authentication is the latest evolution in authentication, a method through which passwords can be completely eliminated from the equation, allowing for a user-friendly experience. But the question of security would definitely arise, right? How does not entering a password make the whole thing secure, you may wonder.

The answer to all these questions is cryptography. Using highly advanced ciphers, a passwordless trust-based authentication system is possible. Solely by entering either a user id, phone number or email, combined with an initial trust-based authentication using biometrics, it is possible to eliminate redundancies in the login and authentication process.

Passwordless authentication is backed by a number of leading global players including Facebook, Google, Dropbox, Salesforce, eBay, ING etc., who are all part of the FIDO alliance. FIDO which stands for Fast IDentity Online is an organization dedicated to solving the password problem by adopting free and open standards of passwordless authentication based on cryptographic technology, where all authentication happens on the user’s local device itself, totally negating the chances of hacking at any other point.

This enables organizations to move away from issues such as data breaches and server attacks, reduce costs drastically and provide a cleaner, faster user experience to everyone involved.

