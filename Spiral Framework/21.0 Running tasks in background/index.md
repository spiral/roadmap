# Running tasks in background

Spiral provides support for background PHP processing and a queue system. This feature is available out of the box and allows you to work with a variety of message brokers. To use this feature, you need to add `Spiral\Queue\Bootloader\QueueBootloader` to your application kernel.

The default queue configuration can be found in the `app/config/queue.php` file. This configuration file includes a set of options for each queue driver as well as aliases, which allow you to specify a default queue driver for your application to use.

Here is an example of how to set up the queue configuration:

```
protected const LOAD = [
    // ...
    \Spiral\Queue\Bootloader\QueueBootloader::class,
    // ...
];

return [
    /** Default queue connection name */
    'default' => env('QUEUE_CONNECTION', 'sync'),

    /** Aliases for queue connections, if you want to use domain specific queues */
    'aliases' => [
        // 'mailQueue' => 'null',
        // 'ratingQueue' => 'sync',
    ],
    
    'connections' => [
        'sync' => [
            // Job will be handled immediately without queueing
            'driver' => 'sync',
        ],
        'null' => [
            // Do nothing
            'driver' => 'null',
        ],
    ],
    
    'registry' => [
        'handlers' => [
            'sample::job' => App\Jobs\SampleJob::class
        ],
        'serializers' => [
            ObjectJob::class => 'json',
        ]
    ],
    
    'driverAliases' => [
        'sync' => \Spiral\Queue\Driver\SyncDriver::class,
        'null' => \Spiral\Queue\Driver\NullDriver::class,
    ],
];
```

### Links and materials to read more:
1. [Spiral Queue and Jobs](https://spiral.dev/docs/queue-jobs/3.7/en)
2. [Spiral Queue Configuration](https://spiral.dev/docs/queue-configuration/3.7/en)
