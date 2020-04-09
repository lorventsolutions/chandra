# Laravel 5.2, 5.3

**This documentation is for older version of laravel**[ **click here**](https://lorvent.gitbooks.io/chandra/content/laravel-54.html) **for latest laravel 5.4 documentation**

> If you are starting a new project, you can use our git repo to have everything pre-installed to save your time.

Please follow installation steps mentioned in "Laravel 5.1" but with following change in composer.

## composer changes

We Assume, your composer already includes `"laravel/framework": "5.2.*",`

### laravelcollective/html

Now, instead of `"laravelcollective/html": "5.1.*",`

Use `"laravelcollective/html": "5.2.*",`

### eloquent-taggable

Instead of `"cviebrock/eloquent-taggable": "dev-master",`

Use `"cviebrock/eloquent-taggable": "dev-laravel-5-refactor",`

Finally your composer.json, `require` array should have these

```text
"laravelcollective/html": "5.2.",
"cartalyst/sentinel": "2.0.",
"cviebrock/eloquent-sluggable": "dev-master",
"cviebrock/eloquent-taggable": "dev-laravel-5-refactor",
"yajra/laravel-datatables-oracle": "~5.0"
```

## Routes changes

We need to wrap all routes in routes.php with `web` middleware, like below

```php
Route::group(['middleware' => 'web'], function () {

    /*
|--------------------------------------------------------------------------
| Application Routes
|------------------------------------------------------------------


...
//all other routes
...

Route::get('{name?}', 'JoshController@showFrontEndView');
# End of frontend views

});
```

