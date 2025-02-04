# Exif reader

[![Latest Stable Version](https://poser.pugx.org/Abdelrahmanelmaghraby\ExifReader/v)](//packagist.org/packages/Abdelrahmanelmaghraby\ExifReader)
![PHP7.2 build](https://github.com/Abdelrahmanelmaghraby\ExifReader/workflows/PHP7.2/badge.svg)
![PHP7.3 build](https://github.com/Abdelrahmanelmaghraby\ExifReader/workflows/PHP7.3/badge.svg)
![PHP7.4 build](https://github.com/Abdelrahmanelmaghraby\ExifReader/workflows/PHP7.4/badge.svg)

[![codecov](https://codecov.io/gh/Abdelrahmanelmaghraby\ExifReader/branch/master/graph/badge.svg)](https://codecov.io/gh/Abdelrahmanelmaghraby\ExifReader)
[![Mutation testing badge](https://img.shields.io/endpoint?style=flat&url=https%3A%2F%2Fbadge-api.stryker-mutator.io%2Fgithub.com%2Fantodippo%2Fexif-reader%2Fmaster)](https://dashboard.stryker-mutator.io/reports/github.com/Abdelrahmanelmaghraby\ExifReader/master)
[![Type coverage badge](https://shepherd.dev/github/Abdelrahmanelmaghraby\ExifReader/coverage.svg)](https://shepherd.dev/github/Abdelrahmanelmaghraby\ExifReader)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This is a simple, straightforward and fully typed Exif reader library. It's based on [`exif_read_data`](https://www.php.net/manual/en/function.exif-read-data.php) PHP function, but it avoids a lot of headaches. It requires the [Exif extension](https://www.php.net/manual/en/exif.installation.php) to be installed.

The simplest way to install it is through Composer:

```bash
$ composer require abdelrahmanelmaghraby/exif-reader
```

To use it, it's as simple as this:

```php
$exifReader = new Reader();

try {
    $exifData = $exifReader->read('/tests/images/with-coordinates.jpg');
} catch (CannotReadExifData $e) {
    echo 'Cannot read exif data: ' . $e->getMessage();
}

echo $exifData->getCameraData()->getMaker();        // Sony
echo $exifData->getCameraData()->getModel();        // F5121
echo $exifData->getFileData()->getTakenDate();      // 2017-06-09 18:43:32
echo $exifData->getGeoLocation()->getLatitude();    // 64.25784
echo $exifData->getGeoLocation()->getLongitude();   // -21.121168
```

### Running the project and contributing

The library comes with a Docker setup. To build the containers:
```bash
$ make setup
```
To run the pipeline (static analysis, tests, mutations) for a specific PHP version:
```bash
$ make php72-pipeline
$ make php73-pipeline
$ make php74-pipeline
```
