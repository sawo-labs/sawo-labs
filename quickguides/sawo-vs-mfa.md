---
description: >-
  In this article, we look at the widely prevalent multi-factor authentication
  mechanism and pit it up against the newer passwordless authentication method
  to see which one works better.
---

# SAWO vs MFA

Authentication should always be about user convenience combined with impeccable safety. However, most companies fail to understand this fine balance and thus either end up greatly inconveniencing the user with complicated authentication methods or compromise on the user’s privacy and safety.

### **The Basics**

Multi-Factor Authentication \(hereafter referred to as MFA\) requires the user to provide multiple pieces of evidence \(with a minimum of two\) in order to securely authenticate themselves. The most common MFA method involves entering a password followed by an OTP. This OTP is either sent through email/SMS or is generated on a code generator app such as Google Authenticator.

While this does give an additional layer of security compared to simply entering a password, it is still prone to hacking attacks. Moreover, as it is dual device-dependent, it can be cumbersome for the user who might simply want to quickly log in to their favorite streaming platform to watch content.

On the other hand, passwordless authentication simply allows the user to log in to their desired app by entering either the email address, username or mobile number. Authentication is managed by highly secure cryptographic techniques as well as biometrics, which eliminates the need for a password altogether. Safety and convenience, combined!

### **What’s wrong with passwords?**

Purists might place valid sounding arguments in favor of passwords, such as using a long, alphanumeric password with special characters and casing which is much harder to brute force or hack.

However, when looked at from the larger standpoint, passwords are more of a headache than a boon, both for the users as well as the implementers. For users, remembering such lengthy and secure passwords can be a pain, especially when dealing with a large number of websites that require authentication.

As a result, they might either use the same password across multiple websites, thus opening the scope for a total wipe-out in case a hacker gets hold of their password, or they might end up forgetting the password totally, thereby either locking them out completely or forcing them to complete lengthy verifications to reset the password.

To avoid this, they might resort to noting down the “strong” password either in plaintext digitally or lying around somewhere physically, again giving scope for the password to be easily compromised, thereby defeating the whole purpose of having a password.

From a business standpoint, passwords are a major security issue for organizations as the databases in which these passwords and other such sensitive data are stored are often prime targets for hackers. Thus, in order to mitigate database attacks, these companies will have to spend a lot of money on resource up-gradation, security mechanisms and monitoring. This unnecessarily adds to the operating costs of the organization, ultimately eating into their profit margins.

### **Challenges in Multi-Factor Authentication**

Common MFA mechanisms include two or more of these methods used in conjunction – SMS-based OTP, Email-based OTP, Biometrics, Authenticator apps, Code generators, hardware-based authentication.

Although these methods mentioned above seem highly secure, there have been instances of all these methods being breached. SMS or Email based OTP is the most [insecure method](https://www.kaspersky.co.in/blog/2fa-practical-guide/14467/) as the OTP sent through these channels are susceptible to what is termed as a man-in-the-middle \(MITM\) attack, which basically fraudulently intercepts the data while it is being transferred from the source to the destination. This can lead to the attacker getting hold of your OTP and conducting transactions without your knowledge, as the OTP or notification message is never received at your end.

Hackers have stepped up their game in the past few years, using advanced methods such as SIM Swapping and Network Tower Interception to [break into databases that contain a user’s personal data](https://www.vice.com/en/article/5dmbjx/how-hackers-are-breaking-into-att-tmobile-sprint-to-sim-swap-yeh?utm_source=vicetwitterus).

For users too, MFA is extremely cumbersome as they have to rely on two or more devices to complete the authentication process. It is not often that they have these devices in handy. This can be especially off-putting when it comes to logging in to low-risk platforms such as news websites or apps, or streaming platforms where the user simply wishes to access content and not perform any high-risk transaction such as a financial exchange.

Having such complicated authentication mechanisms might force the user to look for alternative apps or websites that do not require such levels of user authentication. This would translate to a loss of user base, ultimately leading to revenue losses.

### **Passwordless Authentication: A solution to these issues?**

Passwordless authentication is the latest evolution in authentication, a method through which passwords can be completely eliminated from the equation, allowing for a user-friendly experience. But the question of security would definitely arise, right? How does not entering a password make the whole thing secure, you may wonder.

The answer to all these questions is cryptography. Using highly advanced ciphers, a passwordless trust-based authentication system is possible. Solely by entering either a user id, phone number or email, combined with an initial trust-based authentication using biometrics, it is possible to eliminate redundancies in the login and authentication process.

Passwordless authentication is backed by a number of leading global players including Facebook, Google, Dropbox, Salesforce, eBay, ING etc., who are all part of the FIDO alliance. FIDO which stands for Fast IDentity Online is an organization dedicated to solving the password problem by adopting free and open standards of passwordless authentication based on cryptographic technology, where all authentication happens on the user’s local device itself, totally negating the chances of hacking at any other point.

This enables organizations to move away from issues such as data breaches and server attacks, reduce costs drastically and provide a cleaner, faster user experience to everyone involved.

### **Migrate to Passwordless with SAWO**

If you’re an organization still using the outdated MFA method, we strongly urge you to give passwordless authentication a shot. It’s pretty easy, straightforward and quick to set up and scale.

SAWO Labs offers a low-cost high-impact passwordless authentication mechanism that you can use on your apps and websites. Contact us right away for a free demo, and our technical experts will be at your assistance for all your queries.

