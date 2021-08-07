---
description: >-
  Laravel is a free, open-source PHP web framework. Intended for the development
  of web applications following the model–view–controller architectural pattern
  and based on Symfony.
---

# Laravel

### Let's Get your Laravel App running with SAWO 🙌 

### **Requirements**

### \*\*\*\*[![Current version](https://img.shields.io/packagist/v/sawolabs/sawo-laravel.svg?logo=composer)](https://packagist.org/packages/sawolabs/sawo-laravel) [![Supported PHP version](https://img.shields.io/static/v1?logo=php&label=PHP&message=%5E7.2|~8.0.0&color=777bb4)](https://packagist.org/packages/sawolabs/sawo-laravel)

### Steps**:**

**1. Installation**

To get started with Sawo, use the **Composer package manager** to add the package to your project's dependencies:

```text
$ composer require sawolabs/sawo-laravel
```

**2. Configuration**

Before using Sawo, you will need to **add credentials** for your application. These credentials should be placed in your application's `config/sawo.php` **configuration file.**

```text
<?php

return [
    /*
    |--------------------------------------------------------------------------
    | Configure Sawo defaults
    |--------------------------------------------------------------------------
    |
    | Supported Identifier Types: "phone_number_sms", "email"
    |
    */

    'api_key' => env('SAWO_API_KEY', ''),

    'api_secret_key' => env('SAWO_SECRET_KEY', ''),

    'identifier_type' => env('SAWO_IDENTIFIER_TYPE', 'email'),

    'redirect_url' => env('SAWO_REDIRECT', ''),
];
```

then add the following in the **.env file**

```text
SAWO_API_KEY=<YOUR_SAWO_API_KEY_HERE>
SAWO_SECRET_KEY=<YOUR_SAWO_SECRET_KEY_HERE>
SAWO_IDENTIFIER_TYPE=phone_number_sms
SAWO_REDIRECT=https://yourdomain.com/sawo/callback
```

**3. Add Sawo login form to blade template**

Include the following code in your **login blade template** to show Sawo Auth dialog**.**

```text
@include('sawo::auth')
```

**4. Verifying User Token**

```text
use SawoLabs\Laravel\Sawo;

Route::get('/sawo/callback', function () {
    $userData = $request->only('user_id', 'created_on', 'identifier', 'identifier_type', 'verification_token');

    $isVerified = Sawo::validateToken($userData['user_id'], $userData['verification_token']);

    // If user is identifying via phone
    if ('phone_number_sms' == $userData['identifier_type']) {
        $user = User::where('phone', $userData['identifier'])->first();
    } elseif ('email' == $userData['identifier_type']) {
        $user = User::where('email', $userData['identifier'])->first();
    }

    if (empty($user)) {
        $user = new \App\Models\User();
        $user->phone = $userData['identifier'];
        $user->email = $userData['identifier'];
        $user->password = bcrypt($userData['verification_token']);
    }

});
```

**Congratulations !! The SAWO API is now ready to be used in your Laravel application** 🤘**.**  

#### You can also check out SAWO's [Laravel Sample Code](https://github.com/sawolabs/laravel-example) and [Deployed App](https://github.com/sawolabs/laravel-example).

#### It's okay, we get it! You got Stuck! 😞 Feel free to contact us on \#ask-for-help on our [Discord](https://discord.com/invite/TpnCfMUE5P)

{% page-ref page="../faqs.md" %}

