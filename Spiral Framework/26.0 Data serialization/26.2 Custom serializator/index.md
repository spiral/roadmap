# Creating a Custom Serializer

You can create a custom serializer that implements the `SerializerInterface`. You need to implement 2 methods: the `serialize` method with the `$payload` parameter (and this method should return the serialized data) and the `unserialize` method, which in the parameters accepts serialized data `$payload` and optionally the name of the class or object `$type` into which the payload should be deserialized.

```
namespace App;

use Spiral\Serializer\SerializerInterface;

class CustomSerializer implements SerializerInterface
{
    public function serialize(mixed $payload): string|\Stringable
    {
        // your serialization logic goes here
    }

    public function unserialize(\Stringable|string $payload, object|string|null $type = null): mixed
    {
        // your deserialization logic goes here
    }
}
```

### Links and materials to read more:
1. [Data Serialization](https://spiral.dev/docs/component-serializer/current/en)
