Symantec VeriSign Identity Protection (VIP) TOTP Generator
================

This repository a Docker wrapper around [@cyrozap](https://github.com/cyrozap)'s [python-vipaccess](https://github.com/cyrozap/python-vipaccess), which is a free and open source software (FOSS) implementation of Symantec's VIP Access client. In combination with this repository, it generates OTPAUTH URIs by running a Docker container so that any TOTP-generating application can be used as a Symantec VIP OTP token.

You can see [@cyrozap](https://github.com/cyrozap)'s blog post [here](https://www.cyrozap.com/2014/09/29/reversing-the-symantec-vip-access-provisioning-protocol/), which describes how he reverse-engineered the VIP Access application.

Usage
-----

Once you've installed [Docker](https://www.docker.com/), you can run the following command to generate a new `otpauth://` URI:
```docker run --rm claudiodekker/symantec-vip-otp-generator```


Example Applications
-----

### PayPal
PayPal supports 2FA using either a mobile phone number or a security key. Unfortunately, this security key is a physical device (credit-card format) from either PayPal or Verisign Identity Protection.

Of course, you could go and order one such physical key and take it with you wherever they go (including the risk of losing and/or breaking it), or you could simply use this and generate your own Symantec VIP-compliant TOTP `otpauth://` URI, which can then be stored in any TOTP-supporting password manager, such as [1Password](https://1password.com/)

You can connect your 2FA token to your account here: https://www.paypal.com/us/cgi-bin/webscr?cmd=_activate-security-key-any


Changelog
-----

### May 29th, 2017 -- Security-related side-note
Because of ongoing breakage with [cyrozap/python-vipaccess@master](https://github.com/cyrozap/python-vipaccess/commits/master), this repository is currently using [zecoj/python-vipaccess@34b6ce6](https://github.com/zecoj/python-vipaccess/commit/34b6ce697429892141ad511d5e8e4b95e40abb98) as it's HEAD instead.
This repository is a fork from the original, in which the endpoints regarding the Symantec VIP service have been updated.
