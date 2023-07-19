## Autowiring

Autowiring is a feature of the Spiral container that allows automatic resolution of class dependencies. This means that the container can automatically create and inject dependencies for a class without the need for explicit configuration.

The container supports advanced features like union types, variadic arguments, referenced parameters and default object values for the auto-wiring.

```php
use Spiral\Core\Container\Autowire;
use Spiral\Session\Handler\FileHandler;

return [
    // ...
    'handler' => new Autowire(
        FileHandler::class,
        [
            'directory' => directory('runtime') . 'session',
            'lifetime' => (int)env('SESSION_LIFETIME', 86400),
        ]
    ),
];
```

### Links and materials to read more:
1. [Container and DI](https://spiral.dev/docs/framework-container/current)
