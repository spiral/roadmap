## Events

Events in Spiral Framework are a way for different parts of your application to communicate with each other. This is done by dispatching events and listening to them. The framework provides tools to make this process easy and efficient. It also provides an easy way to integrate PSR-14 compatible EventDispatcher.

An event is a message produced by an Emitter. It may be any arbitrary PHP object. A Listener is any PHP callable that expects to be passed an Event. Zero or more Listeners may be passed the same Event. A Listener MAY enqueue some other asynchronous behavior if it so chooses.

Here is an example of how to create an event:

```php
// Event creation
namespace App\Event;

use App\Database\User;

final class UserWasCreated
{
    public function __construct(
        public readonly User $user
    ) {
    }
}
```

And here is how to dispatch an event:

```php
// Dispatching an event
namespace App\Service;

use Psr\EventDispatcher\EventDispatcherInterface;
use App\Event\UserWasCreated;

final class UserService 
{
    public function __construct(
        private readonly EventDispatcherInterface $dispatcher
    ) {
    }

    public function create(string $username): User
    {
        $user = new User(username: $username);
        // ...
        $this->dispatcher->dispatch(new UserWasCreated($user));
        
        return $user;
    }
}
```

Finally, this is how you can create a listener:

```php
// Listener creation
namespace App\Listener;

use App\Event\UserWasCreated;
use Spiral\Events\Attribute\Listener;

#[Listener]
class UserWasCreatedListener
{
    public function __invoke(UserWasCreated $event): void
    {
        // ...
    }
}
```

### Links and materials to read more:
1. [Spiral Framework Events Documentation](https://spiral.dev/docs/advanced-events/3.7/en)
