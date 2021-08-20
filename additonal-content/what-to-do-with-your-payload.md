---
description: >-
  SAWO's SDK returns a payload which can be used in various methods. Some of
  them are explained below.
---

# What to do with your Payload?

### Dummy Payload

The Payload of an API Module is the body of your request and response message. It contains the data that you send to the server when you make an API request. You can send and receive Payload in different formats, for instance JSON.

On successful authentication, SAWO's SDK returns a payload that is similar to the JSON that is shown below:

```javascript
Payload : {
    "user_id":"05e5d3f1-aea0-4441-89ae-7dee68469ccf",
    "created_on":"2021-08-04T15:11:41.396000Z",
    "identifier":"john@gmail.com",
    "identifier_type":"email",
    "verification_token":"0mkauQoeDeAf97rJcLpRmkmFuIH0bRpFsi6d",
    "customFieldInputValues":{
        "Name":"John",
        "Company Name":"SAWO Labs"
        }
    }

```

This is a dummy payload that is shown above where,

`user_id` is a unique string that is generated when a user has been successfully authenticated.  
`created_on` contains the date and time of the authentication.  
`identifier` holds the value of your `email-id` or `phone-number`.  
`identifier_type` is the type of identifier that the user has defined.  
`verification_token` is a unique string that is used to authenticate   
`customFieldInputValues` is an object where it contains details of a key of the name of the field and value contains the value of that field.

On successful authentication, the payload would come as a response and it was be utilised in various manners. Some of them are: 

### Storing Data to Database

The payload received by you will be containing essential knowledge about your customer, you can easily store that in a database for further usage of data.

### Managing Session Storage

The payload contains a verification token that can be used to maintain sessions as a challenge happens with the string combination of the verification token with the private key.   
This can be helpful to store sessions in a user's machine.

### CRM 

The data that comes along with the payload can be fed into the CRM system so that the companies are connected to customers, streamline processes, and improve the overall experience.

