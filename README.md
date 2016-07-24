Mainpixel Laravel Api
====================
Laravel API was created by, and is maintained by [Mr. J. del Luna](https://github.com/paperclamp), and is a [MainpixelV4](https://www.mainpixel.io) bridge for [Laravel 5](http://laravel.com). Feel free to check out the [change log](CHANGELOG.md).

## Installation

[PHP](https://php.net) 7+ are required.

[Laravel](https://laravel.com) 5.2+ are required.

To get the latest version of Laravel Mainpixel, simply require the project using [Composer](https://getcomposer.org):

```bash
$ composer require mainpixelbv/laravel-mainpixel
```

Instead, you may of course manually update your require block and run `composer update` if you so choose:

```json
{
    "require": {
        "mainpixelbv/laravel-mainpixel": "^1.0"
    }
}
```

Once Laravel Mainpixel is installed, you need to register the service provider. Open up `config/app.php` and add the following to the `providers` key.

* `'mainpixelbv\laravel-mainpixel\MainpixelApiServiceProvider'`

You can register the DigitalOcean facade in the `aliases` key of your `config/app.php` file if you like.

* `'DigitalOcean' => 'mainpixelbv\laravel-mainpixel\MainpixelApi'`

## Configuration

Laravel Mainpixel requires connection configuration.

To get started, you'll need to publish all vendor assets:

```bash
$ php artisan vendor:publish
```

This will create a `config/MainpixelApi.php` file in your app that you can modify to set your configuration. Also, make sure you check for changes to the original config file in this package between releases.

## Usage
`use` the right type class. Like `Containers`, `Databases`, `Contacts`

```php
use Mainpixel\Api\Types\Hosting\{type};
```

## Hosting

### Webcontainers
#### List all webcontainers

```php
public function index() {
    $list = $containers->list();
}
```
##### Output
```json
{
    "protected" : {
        "identifier" : "UNIQUE-CONTAINER-ID",
        "created_at" : "UNIX-TIMESTAMP",
        "updated_at" : "UNIX-TIMESTAMP",
        "dns_general_state" : "DOMAINS-DNS-STATE (true/false)"
    },
    "data" : {
    
    },
    "domains" : {
        0 : {
            "DOMAIN-ID" : "DOMAIN-INCL-TLD"
        }, 
    },
    "amount" : {
        "domains" : "NUMBER-OF-DOMAINS",
        "email" : "NUMBER-OF-EMAIL-ACCOUNTS/FORWARDERS/CATCHALLS",
        "databases" : "NUMBER-OF-DATABASES"
    },
}


