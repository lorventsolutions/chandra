# Install Chandra

We need to install following packages, run migrations and database seeding.

## Delete existing migration files

Since we are not relying on default migration tables, please remove following two files from `database/migrations` folder

```text
2014_10_12_000000_create_users_table.php
2014_10_12_100000_create_password_resets_table.php
```

Otherwise you will get error at later stage of installation.

## Setup HTML package

Laravel 5 doesn't come with HTML,FORM package by default,

if you want to use it... we need to add package manually

Since we use it in many places, we have to add it to our composer.json

 **Add Package to composer**

open your composer.json file and add the following to the require array:

`"illuminate/html": "~5.0",` then in terminal/cmd run `composer update`

 **Add service providers** 

Open `config/app.php` and add following lines

In the `$providers` array add the following service provider

`'Illuminate\Html\HtmlServiceProvider',`

In the `$aliases` array add following facades

`'Form' => 'Illuminate\Html\FormFacade',`

`'Html' => 'Illuminate\Html\HtmlFacade',`

## Setup sentry

**Add Sentry to composer**

Open your composer.json file and add the following to the require array:

`"cartalyst/sentry": "dev-feature/laravel-5",`

now in your command prompt run `composer update` and all required files will be added

**Add sentry service provider**

Now, we need to add sentry service provider to make use of it.

Open `config/app.php` and add following lines

In the `$providers` array add the following service provider

`'Cartalyst\Sentry\SentryServiceProvider',`

In the `$aliases` array add the following facade

`'Sentry' => 'Cartalyst\Sentry\Facades\Laravel\Sentry',`

Now we need to add user, groups etc tables to database, to do so in your command prompt, execute following code

```text
php artisan migrate
```

Note: please check all files in `database\migrations` to know what fields are being added.

Now we need to publish config, so that you can edit configuration, if needed

Excecute following command in command prompt/terminal

```text
php artisan vendor:publish
```

please headover to [sentry website](https://cartalyst.com/manual/sentry) to learn more about it

## Add admin user

As database tables have been setup, we need to add admin user to be able to login into adminCP.

Run following command in your command prompt

```text
php artisan db:seed
```

**A default admin user with user with username admin@admin.com and password admin will be created**

Optional: If you wish to use a different username or password, please open `database\seeds\AdminSeeder.php` and edit values around lines 14-18

## upload directory permissions

user's profile pics will be uploaded into `public/uploads/users`

so we need to provide write access for that folder

to do so, please run following command in your command prompt/terminal

```text
chmod 777 public/uploads/users
```

