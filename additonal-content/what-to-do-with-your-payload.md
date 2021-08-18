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
    "customFieldInputValues":{}
    }

```

This is a dummy payload that is shown above where,

`user_id` is  
`created_on` is  
`identifier` is  
`identifier_type` is  
`verification_token` is  
`customFieldInputValues` is

explain key, added custom fields, suceeful auth can be 

### Database

The payload that a user receives can be stored in a database as the payload contains vital information regarding the user.

### Session Storage



### CRM 

examples sales

