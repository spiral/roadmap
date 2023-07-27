## Defining dependencies

The Spiral container allows you to configure it by creating bindings between interfaces or aliases to specific implementations. 
You can use **Bootloaders** to define these bindings. 

#### Binding via bootloaders

```php
use Spiral\Boot\Bootloader\Bootloader;
use Spiral\Core\Container;

final class ServiceBootloader extends Bootloader
{
    protected const BINDINGS = [
        MyInterface::class => MyClass::class
    ];
    
    protected const SINGLETONS = [
        ClientInterface::class => [self::class, 'createClient'],
    ];
        
    private function createClient(GithubConfig $config): ClientInterface 
    {
        return new Client(
            $config->getAccessToken(),
            $config->getSecret(),
        );
    }
}
```

#### Binding via container

To bind an interface to a concrete implementation, you can use the `Container` or `BinderInterface`. 

```php
use Spiral\Core\Container;

public function boot(Container $container): void
{
    $container->bind(MyInterface::class, MyClass::class);
    $container->bindSingleton(MyInterface::class, MyClass::class);
}
```

### Links and materials to read more:
1. [Container and DI](https://spiral.dev/docs/framework-container/current)
2. [Bootloaders](https://spiral.dev/docs/framework-bootloaders/current)
