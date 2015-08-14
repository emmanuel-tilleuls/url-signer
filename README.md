# Create URLs with a limited lifetime.

[![Latest Version on Packagist](https://img.shields.io/packagist/v/spatie/signedurl.svg?style=flat-square)](https://packagist.org/packages/spatie/signedurl)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)
[![Build Status](https://img.shields.io/travis/spatie/signedurl/master.svg?style=flat-square)](https://travis-ci.org/spatie/signedurl)
[![Quality Score](https://img.shields.io/scrutinizer/g/spatie/signedurl.svg?style=flat-square)](https://scrutinizer-ci.com/g/spatie/signedurl)
[![Total Downloads](https://img.shields.io/packagist/dt/spatie/signedurl.svg?style=flat-square)](https://packagist.org/packages/spatie/signedurl)

This package can create URLs with a limited lifetime.

```php
echo $signedUrl->sign('https://myapp.com', 30);
// => The generated url will be valid for 30 days
```
This will output an URL not unlike `https://myapp.com/?expires=1439223344&signature=2d42f65bd023362c6b61f7432705d811`.

Spatie is a webdesign agency in Antwerp, Belgium. You'll find an overview of all
our open source projects [on our website](https://spatie.be/opensource).


## Install

The package can installed via Composer:
```
$ composer require spatie/signedurl
```

## Usage

A`Spatie\SignedUrl\SignedUrl`-object can sign and validate signed URLs. The secret key is used to
generate signatures.

```php
use Spatie\SignedUrl\SignedUrl;

$signedUrl = new SignedUrl('mysecretkey');
```

### Generating URLs

Signed URLs can be generated by providing a regular URL and an expiration date to the `sign()` method.

```php
$expirationDate = (new DateTime)->modify('10 days');

$signedUrl->sign('https://myapp.com', $expirationDate);

// => The generated url will be valid for 10 days
```

If an integer is provided as expiration date, the url will be valid for that amount of days.

```php
$signedUrl->sign('https://myapp.com', 30);

// => The generated url will be valid for 30 days
```

### Validating URLs

To validate a signed URL, simply call the `validate()` method. This will return a boolean.

```php
$signedUrl->validate('https://myapp.com/?expires=1439223344&signature=2d42f65bd023362c6b61f7432705d811');

// => true

$signedUrl->validate('https://myapp.com/?expires=1439223344&signature=2d42f65bd0-INVALID-23362c6b61f7432705d811');

// => false
```

## Tests

The tests are written in phpspec.

```
$ vendor/bin/phpspec run
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

## Security

If you discover any security related issues, please email freek@spatie.be instead of using the issue tracker.

## Credits

- [Sebastian De Deyne](https://github.com/sebastiandedeyne)
- [All Contributors](../../contributors)

## About Spatie
Spatie is a webdesign agency in Antwerp, Belgium. You'll find an overview of all our open source projects [on our website](https://spatie.be/opensource).

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
