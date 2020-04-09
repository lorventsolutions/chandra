# Fresh Installation

## Fresh Installation

**When you download files from codecanyon, you will see a zip folder named 'ready\_to\_use.zip' which has everything pre-configured**

If you are starting a new project, you can use this version and you don't need to go through the process of setting up everything.

This version is a bit different than the original one because everything configured properly

In fact this will take less time compared to installing from CodeCanyon's files

#### add vendors

we don't push vendors to git as they can grow like anything \(a default feature of laravel or any composer related projects\)

`composer install`

### create .env file

Since .env file is not included, we need to create that \(again a security measure of not to expose your database details to anyone else\)

`cp .env.example .env`

### generate key

Every app needs a key which is being used for many purposes including salting your passwords

`php artisan key:generate`

### permissions

```text
chmod -R 755 storage

chmod 755 bootstrap/cache
```

### database credentials

open `.env` and change database details with yours

### add tables to databaes

`php artisan migrate`

### add admin to users table

`php artisan db:seed --class=AdminSeeder`

## Congratulations

open your website and now it should be fully working :\)

