yubikey-salesforce-client
=========================

Apex classes for validating YubiKey OTP's (one-time passwords).

## Usage
``` java
OtpValidator validator = new OtpValidator();
String result = validator.validate(otp, clientId);

if(result == AuthenticationResult.OK) {
  /* The OTP is valid! Now we want to check that the YubiKey belongs
   * to this user. To do this, we need to compare the ID of the YubiKey
   * used to generate the OTP with the YubiKey associated with the user's
   * account.
   *    
   * For example:
   */
  
  String yubikeyId = OtpUtils.getYubikeyId(otp)
  if(yubiKeyId == user.yubikeyId__c) {
    // Successfully authenticated!
  } else {
    // The wrong YubiKey was used for this user.
  }
} else {
  // Invalid OTP
}
```
