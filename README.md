# Wegmeister.Recaptcha
*Tested with Flow 4.0.x*

Neos-Plugin to integrate Google's Recaptcha into Forms

(c) Benjamin Klix, die wegmeister gmbh


## Installation

Require the package using composer:
```
    composer require wegmeister/recaptcha
```

After this go to [http://www.google.com/recaptcha](http://www.google.com/recaptcha) and create some keys for your website (reCAPTCHA, Version 2).

Then you can simply add the new form element to your form definition renderables:
```yaml
type: 'Neos.Form:Form'
identifier: someIdentifier
label: Label
renderables:
  -
    type: 'Neos.Form:Page'
    identifier: page-one
    renderables:
      -
        type: 'Wegmeister.Recaptcha:Captcha'
        identifier: captcha
        label: Captcha
        properties:
          siteKey: your-public-key
          wrapperClassAttribute: 'form-group'
          # Optional values to adjust recaptcha. For further information visit
          # https://developers.google.com/recaptcha/docs/display#config
          theme: 'light'
          type: 'image'
          size: 'normal'
          tabindex: 0
        # optionally change the translationPackage
        # if you want to adjust the error message
        #renderingOptions:
        #  validationErrorTranslationPackage: 'Wegmeister.Recaptcha'
        validators:
          -
            identifier: 'Wegmeister.Recaptcha:IsValid'
            options:
              secretKey: your-private-key
finishers:
  -
   <Your finishers here>
```
## Using with [Neos.Form.Builder](https://github.com/neos/form-builder)

Install Neos.Form.Builder
```
composer require neos/form-builder
```

Add Captcha form element to your form
![Captch Element](Documentation/Images/CaptchaFormElement.png)

Configure reCaptcha key and other settings from the Inspector

Also add the Captcha Validator element inside validators child node of Captcha
![Captcha Validator](Documentation/Images/CaptchaValidator.png)

Configure reCaptcha secretKey from the Inspector

### I18N

English, German and Dutch are the only supported languages at the moment. Feel free to send us another language to add it to the plugin.



