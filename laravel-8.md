# Laravel 8

> tip This installation guide is for latest version, if you are installing an older version of laravel, please find it's instructions in the left menu. :::

## Laravel 8.x Installation

This Installation guide has been split into 3 parts

* Pre-requisites
* Installation
* after setup

### Pre-requisites

To use JOSH which is a developer-oriented product, you should have a basic idea of following tools and make sure they are installed in your system.

::: tip Windows Users If you don't want to install all of them manually, please download [laragon](https://laragon.org/) :::

#### Git

you can check if you have git by running `git --version` in terminal, if you don't have it...you can get it from git-scm.com

or on \*nix system, you can install by running `apt-get install git` command

#### nodejs

you can check if you have nodejs installed or not by running `nodejs -v` in terminal, if you don't have it... you can get it from nodejs.org

for \*nix system, find instructions here [https://nodejs.org/en/download/package-manager/](https://nodejs.org/en/download/package-manager/)

#### yarn

you can check for yarn existence by running `yarn -v` in terminal, if you don't have it, you can get from their website [https://yarnpkg.com](https://yarnpkg.com) and follow instructions mentioned there

#### composer

you can check for composer existence by running `composer -v` in terminal and if you don't have it, get it from getcomposer.org

### Installation

The zip file contains all laravel files integrated with josh, however, you need to perform the following steps to get vendors etc.

#### .env file and setting your values

Since everyone can have their own database name, mail settings etc, laravel doesn't ship with `.env` but `.env.example` which we copy as `.env` and modify with our DB details etc.

```bash
cp .env.example .env
```

**For Windows Users**

```text
copy .env.example .env
```

now open `.env` and modify database etc. details with yours

you need to modify the following values

```bash
DB_DATABASE=homestead
DB_USERNAME=homestead
DB_PASSWORD=secret
```

you may need to change other fields as well, if necessary

#### Get Composer packages

We don't add all vendors files into zip, hence you need to get them manually, running below command can get you all composer vendor packages

```bash
composer install
```

#### Permissions

::: tip Windows users don't need follow these steps :::

Laravel requires directories within the `storage` and the `bootstrap/cache` directories should be writable by your web server

You should use the minimum permissions available for writing, based on how you've got your web server configured.

```bash
chmod -R 775 storage

chmod 775 bootstrap/cache
```

If you still run into a permissions error, you may need to increase the permissions to 777, or twiddle your user/group permissions on your server.

```bash
chmod -R 777 storage

chmod 777 bootstrap/cache
```

You'll also want to make sure that your laravel directory and all files within are owned by something other than root. It's very common to create a user on your server \(like www-data\), add that user to the apache group, and then chown your files to be owned by www-data, chgrp to the apache group.

This ensures your files can be executed correctly and cache files can be written to without having to give files owned by root the permissions to write or execute.

#### Mails

If you want to send emails from your website, you need to configure `MAIL_DRIVER` etc details in your `.env` file, if you don't want to send emails \(ex: in dev environment\), you can set `MAIL_DRIVER` to `log` and it will write all your emails to log files.

::: tip Global 'from' address You can specify `from` address from each email from `mailables` however if you wish to have a single global `from` address then please modify `config/mail.php` below section with your values

```php
'from' => [
        'address' => env('MAIL_FROM_ADDRESS', 'hello@example.com'),
        'name' => env('MAIL_FROM_NAME', 'Example'),
    ],
```

:::

::: warning If you want to use other mail drivers like `sparkpost, mailgun` etc, then please refer to [https://laravel.com/docs/mail](https://laravel.com/docs/mail) :::

#### Generate Key

To secure user sessions and other encrypted data, we need to set application key.

```bash
php artisan key:generate
```

#### Add tables to the database

Now that, we have set up database details in `.env`, its time to migrate tables into database.

To have default admin user, we need to seed data into DB, to do that run below command, which inserts two users into the database along with two roles `admin` and `user`.

| User email | password | Role |
| :--- | :---: | ---: |
| admin@admin.com | admin | admin |
| user@user.com | user | user |

```bash
php artisan migrate --seed
```

along with users, it also inserts all countries data into `countries` table.

::: tip If you want to have some dummy data in datatables examples, please run

`php artisan db:seed --class=DatatablesSeeder` :::

#### Compiling assets

Now we need to get frontend assets and move them to the proper place, please run the following commands.

`yarn install`

`npm run dev`

if everything compiles successfully, by now you should have a working website

you can access your website at [http://URL/public](http://URL/public) \(if not using virtualhosts\) or [http://URL](http://URL) \(if using virtualhosts\) and you can access admin section by going to [http://URL/public/admin](http://URL/public/admin) or [http://URL/admin](http://URL/admin) respectively.

### After setup

Still, we need to get some keys and set up things to make sure josh is working properly

#### Uploads folders permission

::: tip Windows users don't need to follow these steps :::

we need to provide write permission to the following folder

```text
public/uploads/blog

public/uploads/crudfiles

public/uploads/files

public/uploads/news

public/uploads/users
```

\*\*\*\*

