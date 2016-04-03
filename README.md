WordPlate
=========

![wordplate](https://cloud.githubusercontent.com/assets/499192/13548328/22cb8d6c-e2ee-11e5-8adf-33c8184181b1.jpg)

WordPlate is a modern WordPress stack which tries to simplify the fuzziness around WordPress development. Using the latest standards from PHP. WordPlate utilizes WordPress as its dependency through Composer.

```bash
composer create-project wordplate/wordplate
```

[![Build Status](https://img.shields.io/travis/wordplate/framework/master.svg?style=flat)](https://travis-ci.org/wordplate/framework)
[![Latest Version](https://img.shields.io/github/release/wordplate/wordplate.svg?style=flat)](https://github.com/wordplate/wordplate/releases)
[![License](https://img.shields.io/packagist/l/wordplate/wordplate.svg?style=flat)](https://packagist.org/packages/wordplate/wordplate)

## Table of Contents

- [Installation](#installation)
- [Configuration](#configuration)
- [Theming](#theming)
- [Plugins](#plugins)
- [Gulp](#gulp)
- [Helpers](#helpers)
- [Contributing](#contributing)

## Why WordPlate?

- [Easy to setup](#installation)
- [Built with Composer](https://getcomposer.org/)
- [WordPress as a dependency](composer.json)
- [Environment files](https://github.com/vlucas/phpdotenv)
- [Versioning and cache busting](https://laravel.com/docs/5.2/elixir#versioning-and-cache-busting)
- [WordPress Packagist](https://wpackagist.org/)
- [Laravel Elixir](https://laravel.com/docs/5.2/elixir)
- [Real GUIDs](https://github.com/wordplate/uuid)
- [Soil plugin](https://roots.io/plugins/soil/)

## Installation

To use WordPlate, you need to have PHP 5.5.9+ installed on your machine. You'll also optionally need [Node.js](https://nodejs.org/en/) and [NPM](https://www.npmjs.com/) installed if you want to use [Elixir](https://laravel.com/docs/5.2/elixir) to compile your CSS and Javascript.

Install WordPlate by issuing the Composer `create-project` command in your terminal:

```bash
composer create-project wordplate/wordplate
```

## Configuration

The first thing you should do after installing WordPlate is to add [WordPress salts](https://wordplate.github.io/salt/) to your `.env` environment file.

Typically, these strings should be [64 characters long](https://wordplate.github.io/salt/). The strings can be set in the `.env` environment file. If you have not renamed the `.env.example` file to `.env`, you may do that now. If the [WordPress salts](https://wordplate.github.io/salt/) is not set, your user sessions and other encrypted data will not be secure!

Please visit [WordPlate's salt page](https://wordplate.github.io/salt/) and copy the WordPress salts to your environment file.

## Theming

Building your theme with WordPlate works like any other WordPress environment. Please use the [WordPress documentation](https://codex.wordpress.org/Theme_Development) for reference.

#### Plate

[Plate](https://github.com/wordplate/plate) is a plugin with a bunch of defaults to help you make the most out of WordPress. It comes with handy features such as customizing the administrator dashboard. It is required by default. Please see [the documentation](https://github.com/wordplate/plate#readme) for more information.

#### Soil

[Soil](https://github.com/roots/soil) is a plugin which contains a collection of modules to apply theme-agnostic front-end modifications. Since it is such a good plugin WordPlate requires it by default. If you like it, we [encourage you to buy a license](https://roots.io/plugins/soil).

## Plugins

[WordPress Packagist](https://wpackagist.org/) comes straight out of the box with WordPlate. It mirrors the WordPress [plugin](https://plugins.svn.wordpress.org/) and [theme](https://themes.svn.wordpress.org/) directories as a Composer repository.

#### How do I use it?

1. Add the repository to your `composer.json` file.
1. Add the desired plugins and themes to your requirements using `wpackagist-plugin` or `wpackagist-theme` as the vendor name.
1. Run `composer update`.
1. Packages are installed to `public/plugins` or `public/themes`.

#### Example
This is an example of how your `composer.json` file might look like.

```json
"require": {
    "wordplate/framework": "^4.0",
    "wpackagist-plugin/polylang": "^1.0",
},
```

Please visit [WordPress Packagist](https://wpackagist.org/) website for more information and examples.

## Gulp

WordPlate has integrated [Elixir](https://laravel.com/docs/5.2/elixir). It provides a clean, fluent API for defining basic Gulp tasks for your WordPlate application.

#### Installation

Before triggering Elixir, you must first ensure that [Node.js](https://nodejs.org/en/) is installed on your machine.

```sh
node -v
```

If you don't have Node on your machine you can install it by visiting their [download page](https://nodejs.org/download/).

After you have installed Node, you need to install the required NPM packages for Elixir. You can find them in the `package.json` file. To install, run the following command:

```sh
npm install
```

#### Usage

To use Elixir and Gulp, please run on of the following commands:

##### Development

This script is for development. This script will first run all the Gulp tasks and then keep listening for changes you make in your asset files.

```sh
npm run dev
```

This script will automagically start a [BrowserSync](https://www.browsersync.io/) proxy. For more information about getting started with BrowserSync, please visit the [Elixir documentation](https://laravel.com/docs/5.2/elixir#browser-sync).

##### Production

Then there is a script you should run before publishing your application. This script will compile all your asset files and revision them for [cache busting](https://laravel.com/docs/5.2/elixir#versioning-and-cache-busting).

```sh
npm run pro
```

For more information about Elixir please visit the [official document page](https://laravel.com/docs/5.2/elixir).

## Helpers

WordPlate includes a variety of "helper" PHP functions. You are free to use them in your own applications if you find them convenient.

##### `dd()`

The `dd` function dumps the given variable and ends execution of the script:

```php
dd($value);
```

If you do not want to halt the execution of your script, use the `dump` function instead:

```php
dump($value);
```

##### `elixir()`

The elixir function gets the path to the versioned [Elixir](https://laravel.com/docs/5.2/elixir#versioning-and-cache-busting) file:

```php
elixir($file);
```

##### `env()`

The env function gets the value of an environment variable or returns a default value:

```php
$env = env('WP_ENV');

// Return a default value if the variable doesn't exist...
$env = env('WP_ENV', 'production');
```

##### `value()`

The `value` function's behavior will simply return the value it is given. However, if you pass a `Closure` to the function, the `Closure` will be executed then its result will be returned:

```php
$value = value(function() { return 'bar'; });
```

## Contributing

Please review our [contribution guidelines](https://github.com/wordplate/framework/blob/master/CONTRIBUTING.md) before submitting a pull request.

## License

WordPlate is licensed under [The MIT License (MIT)](LICENSE).
