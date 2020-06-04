---
layout: default
title: Aws S3 (v3) Adapter
permalink: /v2/docs/adapter/aws-s3-v3/
---

Interacting with Aws S3 through Flysystem can be done
by using the `League\Flysystem\AwsS3V3\AwsS3V3Filesystem`.

## Simple usage:

```php
/** @var Aws\S3\S3ClientInterface $client */
$client = new Aws\S3\S3Client($options);

// The internal adapter
$adapter = new League\Flysystem\AwsS3V3\AwsS3V3Filesystem(
    // S3Client
    $client,
    // Bucket name
    'bucket-name'
);

// The FilesystemOperator
$filesystem = new League\Flysystem\Filesystem($adapter);
```

## Advanced usage:

```php
/** @var Aws\S3\S3ClientInterface $client */
$client = new Aws\S3\S3Client($options);

// The internal adapter
$adapter = new League\Flysystem\AwsS3V3\AwsS3V3Filesystem(
    // S3Client
    $client,
    // Bucket name
    'bucket-name',
    // Optional path prefix
    'path/prefix',
    // Visibility converter (League\Flysystem\AwsS3V3\VisibilityConverter)
    new League\Flysystem\AwsS3V3\PortableVisibilityConverter(
        // Optional default for directories
        League\Flysystem\Visibility::PUBLIC // or ::PRIVATE
    )
);

// The FilesystemOperator
$filesystem = new League\Flysystem\Filesystem($adapter);
```

