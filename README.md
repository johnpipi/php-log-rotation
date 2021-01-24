
# PHP class to logs rotation
PHP Class to rotate log files

This class permit log rotating with diferetne processor.

[![tests](https://github.com/cesargb/php-log-rotation/workflows/tests/badge.svg)](https://github.com/cesargb/php-log-rotation/actions)
[![Latest Version on Packagist](https://img.shields.io/packagist/v/cesargb/php-log-rotation.svg?style=flat-square&color=brightgreen)](https://packagist.org/packages/cesargb/php-log-rotation)

## Installation

You can install this package via composer using:

```bash
composer require cesargb/php-log-rotation
```

## Usage

This is an example:

```php
use Cesargb\Log\Rotation;
use Cesargb\Log\Processors\GzProcessor;
use Cesargb\Log\Processors\RotativeProcessor;

$fileLog='file.log';
$fileMaxSize=50; // only rotate log if over 50MB

$rotation = new Rotation();

$rotation->addProcessor(new GzProcessor());
    ->addProcessor(new RotativeProcessor())
    ->rotate($fileLog, $fileMaxSize);
```

## Processor

After of move the content of current log file, you can process changes in
the file was rotated.

### GzProcessor

This processor permit compress in gz format the file rotated.

### RotativeProcessor

This processor permit rotative each file in format file.log.1, file.log.2, ...

You can call method `setMaxFiles` to set the number max of the files rotated.
By default is 366 (One year if rotate each day).

## Todo

[ ] Processor Prefix; To add prefix to file rotated, sample: date (yyyy-mm-dd)
[ ] Processor Archive; To move the file rotated to other dir.
[ ] Processors to move to the cloud

## Test
Run test with:

```bash
composer test
```

## Contributing

Any contributions are welcome.
