# CHANGELOG

## 4.0.0 - 2022-01-09

This is a release with breaking changes. Please review the following changes and adapt your application where needed.

### Changes

* Added support for `kreait/firebase-php` ^6.0
* Dropped support for `kreait/firebase-php` <6.0
* Dropped support for Laravel/Lumen <8.0
* Removed deprecated Facades - use the `Kreait\Laravel\Firebase\Facades\Firebase` facade instead 
  * `Kreait\Laravel\Firebase\Facades\FirebaseAuth`
  * `Kreait\Laravel\Firebase\Facades\FirebaseDatabase`
  * `Kreait\Laravel\Firebase\Facades\FirebaseDynamicLinks`
  * `Kreait\Laravel\Firebase\Facades\FirebaseFirestore`
  * `Kreait\Laravel\Firebase\Facades\FirebaseMessaging`
  * `Kreait\Laravel\Firebase\Facades\FirebaseRemoteConfig`
  * `Kreait\Laravel\Firebase\Facades\FirebaseStorage`
* Removed support deprecated config options and environment variables
  * `$config['debug']`/`FIREBASE_ENABLE_DEBUG`, use the `http_debug_log_channel` config option instead

## 3.4.0 - 2021-12-04
### Added
* Added support for caching the authentication tokens used for connecting to the Firebase servers.

## 3.3.0 - 2021-11-29
### Added
* Ensure support for all PHP 8.x versions 
  ([#110](https://github.com/kreait/laravel-firebase/pull/110))

## 3.2.0 - 2021-10-21
### Added
* Support for Database Auth Variable Overrides
  ([#93](https://github.com/kreait/laravel-firebase/pull/93))
### Changed
* Type-hints have been updated to point to the interfaces that the underlying SDK provides
  since more recent versions.
* Bumped `kreait/firebase-php` dependency to `^5.24` (Database Auth Variable Overrides are supported since `5.22`)

## 3.1.0 - 2021-02-03
### Added
* Support for tenant awareness via `FIREBASE_AUTH_TENANT_ID` environment variable
  or `firebase.projects.*.auth.tenant_id` config variable.
  ([#79](https://github.com/kreait/laravel-firebase/pull/79))
  (thanks to [@sl0wik](https://github.com/sl0wik))

## 3.0.0 - 2020-11-01 
### Added
* Support for multiple firebase projects
  (thanks to [@dododedodonl](https://github.com/dododedodonl)).
  See "upgrading to version 3" section in [UPGRADE.md](UPGRADE.md)
* `\Kreait\Laravel\Firebase\Facades\Firebase` facade
* HTTP Client Options are now configurable 
  (thanks to [@kakajansh](https://github.com/kakajansh))

### Changed
* [config/firebase.php](config/firebase.php) has a new format to support multiple projects

### Deprecated
* Use of `FirebaseAuth`, `FirebaseDatabase`, `FirebaseDynamicLinks`, `FirebaseFirestore`, `FirebaseMessaging`, `FirebaseRemoteConfig` and `FirebaseStorage` facades

### Removed
* Dropped support Laravel 5.8 and Lumen 5.8

## 2.4.0 - 2020-10-04

### Added
* PHP `^8.0` is now an allowed (but untested) PHP version

## 2.3.1 - 2020-09-08

(no changes, I just somehow mis-tagged 2.3.0 🙈)

## 2.3.0 - 2020-09-08

### Added
* Added support for Laravel 8.x

## 2.2.0 - 2020-06-20

### Added
* It is now possible to log HTTP requests and responses to the Firebase APIs to existing log channels. 
  See the "logging" section in [`config/firebase.php`](config/firebase.php) for the configuration 
  options and the [SDK Logging Documentation](https://firebase-php.readthedocs.io/en/5.5.0/setup.html#logging) 
  for more information.
### Changed
* The default branch of the GitHub repository has been renamed from `master` to `main` - 
  if you're using `dev-master` as a version constraint in your `composer.json`, please 
  update it to `dev-main`.

## 2.1.0 - 2020-05-27

* Add config option to debug HTTP requests made directly from the SDK. It is disabled by
  default and can be enabled with the `FIREBASE_ENABLE_DEBUG=true` environment variable
  or by adding `'debug' => true` to `config/firebase.php`.

## 2.0.0 - 2020-04-01

* Update `kreait/firebase` to `^5.0`

## 1.5.0 - 2020-02-29

* Updated `kreait/firebase-php` to `^4.40.1`
* Added support for Laravel/Lumen `^7.0`

## 1.4.0 - 2020-02-22

* Updated `kreait/firebase-php` to `^4.40.0`
* A relative path to a credentials file is now resolved with `base_path()` to address issues on Windows systems [#7](https://github.com/kreait/laravel-firebase/issues/7) 

## 1.3.0 - 2020-01-15

* Added a notice about not using the factory pattern described in the SDK documentation when using this package. 
  (Although not a code change, adding it in the changelog to enhance visibility)
* Added support for [Lumen](https://lumen.laravel.com/)
* Updated `kreait/firebase-php` to `^4.38.1`

## 1.2.0 - 2019-10-26

* Updated `kreait/firebase-php` to `^4.35.0`
* Added Firestore to the Service Provider and as `FirebaseFirestore` facade

## 1.1.0 - 2019-09-19

* Updated `kreait/firebase-php` to `^4.32.0`
* Added Dynamic Links to the Service Provider and as `FirebaseDynamicLinks` facade
* Added `FIREBASE_DYNAMIC_LINKS_DEFAULT_DOMAIN` as environment variable

To update the package, please re-publish its configuration

```bash
php artisan vendor:publish --provider="Kreait\Laravel\Firebase\ServiceProvider" --tag=config
```

or add the following section to `config/firebase.php`:

```php
<?php

return [
    // ...
    'dynamic_links' => [
        'default_domain' => env('FIREBASE_DYNAMIC_LINKS_DEFAULT_DOMAIN')
    ],
    // ...
];
```

## 1.0.1 - 2019-08-19

* Made clear that this package needs Laravel 5.8 or higher.
* Updated `kreait/firebase-php` to `^4.30.1`
* Required `illuminate/contracts` and `illuminate/support`

## 1.0.0 - 2019-08-17

* Initial release
