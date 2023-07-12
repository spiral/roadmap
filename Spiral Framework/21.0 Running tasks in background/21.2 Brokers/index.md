## Brokers

Queue aliasing is a feature that allows your application and modules to access the queue system in a variety of ways, using separate connections that are related to a single physical queue. To obtain a queue instance by its name or alias, you can use the `getConnection` method of the `Spiral\Queue\QueueConnectionProviderInterface`.

If the available queue driver does not meet your specific needs, you can create your own custom driver by implementing the `Spiral\Queue\QueueInterface` interface.

Here is an example of how to use queue aliasing and create a custom queue driver:

```php
return [
    'aliases' => [
        'mailQueue' => 'roadrunner',
        'ratingQueue' => 'sync',
    ],
];

use Spiral\Queue\QueueConnectionProviderInterface;

$container->bind(MyService::class, function(QueueConnectionProviderInterface $provider) {
    return new MyService($provider->getConnection('mailQueue'));
})

final class MyService
{
    public function __construct(
        private readonly QueueInterface $queue
    ) {
    }
}

'connections' => [
    'mail' => [
        'driver' => \App\Infrastructure\Queue\RedisQueue::class,
        'server' => 'redis://localhost:6379',
        'queueName' => 'mail',
    ],
],

'driverAliases' => [
    'redis' => \App\Infrastructure\Queue\RedisQueue::class,
    // ...
],
```

### Links and materials to read more:
1. [Spiral Queue and Jobs](https://spiral.dev/docs/queue-jobs/3.7/en)
2. [Spiral Queue Configuration](https://spiral.dev/docs/queue-configuration/3.7/en)
