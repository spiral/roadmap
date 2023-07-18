## Using the Serializer

Three serializers are available by default:

1. `JsonSerializer` - uses PHP functions `json_encode` and `json_decode`. It does not support data hydration to an object.
2. `PhpSerializer` - uses PHP functions `serialize` and `unserialize`.
3. `CallbackSerializer`- uses callbacks for serializing and deserializing data.

You can inject the serializer from a container using the `SerializerInterface`. It will refer to the default serializer. You can also use the `SerializerManager` to get a specific serializer by a serializer string key from config.

```php
// Configuration for the serializer component
use Spiral\Core\Container\Autowire;
use Spiral\Serializer\Serializer\JsonSerializer;
use Spiral\Serializer\Serializer\PhpSerializer; 
use Spiral\Serializer\Serializer\CallbackSerializer;

return [
    'default' => 'json',
    'serializers' => [
        'json' => JsonSerializer::class,
        'serializer' => new Autowire(PhpSerializer::class),
        'callback' => new CallbackSerializer()
    ],
];
```

### Links and materials to read more:
1. [Data Serialization](https://spiral.dev/docs/component-serializer/current/en)
