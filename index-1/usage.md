# usage

you can generate CRUD using below command

for example: to generate books model with title, author, description fields

please run

```text
php artisan crud:gen book --fields="title:string,author:string,description:text"
```

If you want just model and controller then run below command

```text
php artisan crud:gen book
```

when you don't pass fields, it will just create model and controller

## available field types

* string - this will create a varchar in database, input field for views
* text - this will create a text in daabase and textarea for views
* password - this will create varchar in database, password field for views
* email - this will create varchar in database, email field for views

all others will be treated as varchar in database and respected field type will be created for views

ex: if you pass 'radio' then in views, input type="radio" will be created

## other field types

we will be updating CRUD continously and you can expect other field types in coming days

## planned field types

* radio
* checkbox
* file
* select2
* icheck
* textarea \(summernote\)

