# Laravel Secondary mailer
Laravel 5.1 package to allow a secondary mailer.

## Install

Add the following line to your `composer.json` and run install/update:

    "cyberduck/laravel-secondary-mailer": "1.0.*"


Publish the package config files

    php artisan vendor:publish

Edit the configuration in `app/config/mail2.php` or in your .env file.

Add the service provider to your `app/config/app.php`:

```php
'providers' => array(
  'Cyberduck\LaravelWpApi\LaravelWpApiServiceProvider'
)
```

Optionally, add the facade to your `app/config/app.php`:

```php
'aliases' => array(
    'Mail2' => 'Cyberduck\Mail\Facades\Mail',
)
```
or include tha Facade in your class adding

```php
use \Cyberduck\Mail\Facades\Mail as Mail2;
```

### Usage
Send an email using the \Cyberduck\Mail\Facades\Mail facade with the same syntax of the default mailer.

```php
Mail2::send('emails.reminder', ['user' => $user], function ($m) use ($user) {
    $m->from('hello@app.com', 'Your Application');
    $m->to($user->email, $user->name)->subject('Your Reminder!');
});
```