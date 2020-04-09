# Laravel 5.6

## 5.6 Installation <a id="56-installation"></a>

The zip file contains all laravel files integrated with josh, however you need to perform following steps to get vendors etc.

### Get Composer packages <a id="get-composer-packages"></a>

`composer install`

permissions

```text
chmod -R 775 storage

chmod 775 bootstrap/cache
```

If you are on linux/ mac you can run below command to chown it.

```text
chown -R www-data /var/www
```

### database credentials <a id="database-credentials"></a>

```text
cp .env.example .env
```

open`.env`and modify database details with yours

### Generate Key <a id="generate-key"></a>

```text
php artisan key:generate
```

### add tables to databaes <a id="add-tables-to-databaes"></a>

`php artisan migrate`

### add admin to users table <a id="add-admin-to-users-table"></a>

`php artisan db:seed`

### compile assets <a id="compile-assets"></a>

> If you don't have good knowledge on nodejs and npm, you can copy public folder files from codecanyon's downloaded files

**Note :**The above step is completely optional , if you are not comfortable with this, you can skip it and perform the below steps, still it works fine.

Make sure you have [nodejs](https://nodejs.org/) installed in your system with minimum version`6.10.0`, and yarn`1.5.1`

you can check installed version by running`node -v`command in terminal.

If you are having older version, please install latest version from [nodejs.org](http://nodejs.org/)

For laravel 5.6 , the minimum version of php required is 7.1.3 and

the following php extensions are rquired

* PHP &gt;= 7.1.3
* OpenSSL PHP Extension
* PDO PHP Extension
* Mbstring PHP Extension
* Tokenizer PHP Extension
* XML PHP Extension
* Ctype PHP Extension
* JSON PHP Extension

install local packages

`yarn install`

move assets to public

`npm run dev`

## Congratulations <a id="congratulations"></a>

open your website and now it should be fully working :\)

[    
](https://lorvent.gitbooks.io/josh/content/starter-kit.html)

