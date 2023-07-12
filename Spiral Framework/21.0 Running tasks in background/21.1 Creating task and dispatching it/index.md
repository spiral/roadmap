## Creating task and dispatching it

To create a task in Spiral, you need to create a job handler. Job handlers are classes responsible for performing specific tasks or actions within the system. To create a job handler, you need to implement the `Spiral\Jobs\HandlerInterface` interface. Spiral also provides a convenient abstract class called `Spiral\Queue\JobHandler` that you can extend to simplify the implementation of your job handlers.

Once you have a job handler, you can dispatch your job via `Spiral\Queue\QueueInterface` or via the prototype property queue. When you request the `Spiral\Queue\QueueInterface` from the container, you will receive an instance of the default queue connection. The method `push` of `QueueInterface` accepts a job name, the payload, and additional options.

Here is an example of how to create a job handler and dispatch a job:

```php
namespace App\Endpoint\Job;

use Spiral\Queue\JobHandler;

final class SampleJob extends JobHandler
{
    public function invoke(string $id, array $payload, array $headers): void
    {
        // Do something with service
    }
}

use App\Endpoint\Job\SampleJob;
use Spiral\Queue\QueueInterface;

public function createJob(QueueInterface $queue): void
{
    $queue->push(SampleJob::class, ['value' => 123]);
}
```

### Links and materials to read more:
1. [Spiral Queue and Jobs](https://spiral.dev/docs/queue-jobs/3.7/en)
2. [Spiral Queue Configuration](https://spiral.dev/docs/queue-configuration/3.7/en)
