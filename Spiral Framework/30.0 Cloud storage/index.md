# Cloud Storage

Spiral offers a comprehensive solution for file storage and distribution through its `spiral/storage` and `spiral/distribution` components. The `spiral/storage` component provides powerful storage abstraction utilizing the capabilities of the Flysystem PHP package, offering convenient drivers for working with both local file systems and Amazon S3. The `spiral/distribution` component, which is integrated with the `spiral/storage` component, is responsible for generating public HTTP links for resources stored through the storage component.

To use the storage capabilities, you need to install the component and configure it. The installation process involves adding the `Spiral\Storage\Bootloader\StorageBootloader` to the list of bootloaders in your application.

```php
// Installation
protected const LOAD = [
    // ...
    \Spiral\Storage\Bootloader\StorageBootloader::class,
    // ...
];
```

After installation, you need to configure the storage settings. The storage configuration file is located at `app/config/storage.php` by default. In this file, you can define the storage buckets and their drivers.


```php
// Configuration
return [
    'buckets' => [
        'local' => [
            'driver' => LocalStorageDriver::class,
            'directory' => directory('root') . 'uploads',
            'visibility' => AdapterInterface::VISIBILITY_PUBLIC,
        ],
        's3' => [
            'driver' => S3StorageDriver::class,
            'region' => env('AWS_REGION'),
            'version' => 'latest',
            'credentials' => [
                'key' => env('AWS_KEY'),
                'secret' => env('AWS_SECRET'),
            ],
            'bucket' => env('AWS_BUCKET'),
            'prefix' => env('AWS_PREFIX'),
            'endpoint' => env('AWS_ENDPOINT'),
            'visibility' => AdapterInterface::VISIBILITY_PUBLIC,
        ],
    ],
];
```

### Links and materials to read more:
1. [Spiral Storage Documentation](https://spiral.dev/docs/advanced-storage/current)
