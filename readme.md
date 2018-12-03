# MailboxValidator Laravel Email Validation Package

MailboxValidator Laravel Email Validation Package provides an easy way to call the MailboxValidator API which validates if an email address is valid.



## Installation

Open the terminal, locate to your project root and run the following command :

`composer require mailboxvalidator-laravel/validation`



For Laravel versions below 5.5, you might need the additional step to make Laravel 
discover the service provider. Open the `config/app.php` and add the 
service provider manually into the providers section: 

``MailboxValidatorLaravel\Validation\ValidationServiceProvider::class,``

In the terminal, type the following command to publish the modified config file:

``
php artisan vendor:publish --provider=MailboxValidatorLaravel\Validation\ValidationServiceProvider --force
``



## Dependencies

An API key is required for this module to function.

Go to https://www.mailboxvalidator.com/plans#api to sign up for FREE API plan and you'll be given an API key.

After that, please save your API key in your web application environement file like this:
``
MBV_API_KEY = 'PASTE_YOUR_API_KEY_HERE'
``



## Usage

To use this package to validate the email coming from form submission, you will just need to include `'|disposable'`in Validator function in app\Http\Controllers\Auth\RegisterController.php . A step by step tutorial is included [here](https://www.mailboxvalidator.com/resources/articles/how-to-use-mailboxvalidator-laravel-email-validation-package-to-validate-email-during-registration/). 

To print the validation result on single email, you will first need to include this line on top of your file: `use MailboxValidatorLaravel\Validation\ValidateEmail;` . Then, initialite the ValidateEmail class by using this line: `$validate = new ValidateEmail();`. Lastly, just call `$validate->GetValidateDisposable('email_tobe_validate','your_api_key');`  into a variable and print out the variable.

## Result Fields 

##### email_address

The input email address.

##### is_disposable

Whether the email address is a temporary one from a disposable email provider.

Return values: True, False.

##### credits_available

The number of credits left to call the API.

##### error_code

The error code if there is any error. See error table below.

##### error_message

The error message if there is any error. See error table below.



## Errors

| error_code | error_message         |
| ---------- | --------------------- |
| 100        | Missing parameter.    |
| 101        | API key not found.    |
| 102        | API key disabled.     |
| 103        | API key expired.      |
| 104        | Insufficient credits. |
| 105        | Unknown error.        |



## Copyright

Copyright (C) 2018 by MailboxValidator.com, support@mailboxvalidator.com