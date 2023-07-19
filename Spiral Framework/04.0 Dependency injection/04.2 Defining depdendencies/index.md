## Defining dependencies

The Spiral container allows you to configure it by creating bindings between interfaces or aliases to specific implementations. You can use Bootloaders to define these bindings. There are two ways to configure the container, either by using the `Spiral\Core\BinderInterface` or the `Spiral\Core\Container`.

To bind an interface to a concrete implementation, you can use the `BinderInterface`. To bind a singleton, you can use the `BinderInterface` as well. You can also bind with specific parameters by using the `Autowire` class.

Lastly, you can use closures to configure your class automatically by passing a closure to the `bind` or `bindSingleton` method.

```php
$container->bind(SomeInterface::class, SomeClass::class); 
```

### Links and materials to read more:
1. [Container and DI](https://spiral.dev/docs/framework-container/current)
