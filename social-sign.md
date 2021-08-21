# Migrating from Social Sign On to SAWO's Passwordless

Proper planning is critical for the conduction of successful migration, at  SAWO we have already crafted the process to scale for you, the quickguide has outlined all requirements and design considerations, we have made sure that the process mitigates all risks and doesn't hold any disruptions for the end-user.

{% page-ref page="quickguides/" %}

## Why Migrate to SAWO?

The one major flaw with social login, if we're pragmatic about how users really behave, is password reuse. 59% of people have reported using the same password across multiple sites. When a user registers to a website via social login, his **profile data** and **personal preferences** are **shared** between a social network and a third-party website

Shared data might include user behavior **tracking** and using this data for **personalized ads** and customized content \(as it was in [Cambridge Analytica issue](https://www.vox.com/policy-and-politics/2019/4/16/18410932/facebook-user-data-privacy-cambridge-analytica)\). Thus, social logins as well raise **serious questions** of the security of data and safe password storage.  
  
So, we welcome you to ditch passwords altogether, along with a great level of security and user convenience. Say hello to SAWO!

## How can I implement SAWO in my Own App/Website?

You have already implemented a social sign-on solution which we can generally assume is Facebook, Gmail or Linkedin, now you already have a logic that validates authentication every time requested by the client and side by side a unique identifier stored by them in the database, most of the work has been completed by you and we don't want you to worry about anything else now, so,  we don't store any data of our end clients.   
A simple payload is returned to you using which you can conveniently map your clients with the identifier you chose.

{% hint style="info" %}
### How does our SDK work? 

We authenticate your end customer with asymmetric encryption and post out a payload of your client with details.
{% endhint %}

![](.gitbook/assets/flowchart-3-.png)

### Replacing your Login form with Our iframe

This is the moment from where we start taking over your worries, initially, we request you to replace your current login form with SAWO.

### What happens after you replace your login form?

After your client is successfully authenticated, a payload is sent from our side to your server so you can further process it from your end. Check out [_What to do with your payload?_](additonal-content/what-to-do-with-your-payload.md)\_\_

### New users signing up

If a new user gets authenticated, you can cross check with your Database and insert 

### Existing Users 

As you have already have existing Clients in your Database, you can map your Clients with the identifier sent in the payload by us

{% page-ref page="additonal-content/what-to-do-with-your-payload.md" %}



