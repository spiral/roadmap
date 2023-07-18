### PSR-16

PSR-16, also known as the Common Interface for Caching Libraries, is a standard that describes a simple yet extensible interface for a cache item and a cache driver. It is designed to improve the interoperability of caching libraries, making it easier for libraries to drop their own caching implementations and easily rely on the one given to them by the framework, or another dedicated cache library.

The Spiral Framework's `spiral/cache` component is compliant with the PSR-16 standard. This means that it supports all serializable PHP data types, including strings, integers, floats, booleans, null, arrays, and objects that support lossless serialization and deserialization.

Here is an example of how to use the `set` method, which persists data in the cache, uniquely referenced by a key with an optional expiration TTL time:

```php
$data = $this->cache->get('key');
```

And here is how to store an item in the cache:

```php
$this->cache->set(
    key: 'key', 
    value: ['some' => 'data']
);
```

### Links and materials to read more:
1. [PSR-16: Common Interface for Caching Libraries](https://www.php-fig.org/psr/psr-16/)
2. [Caching Documentation](https://spiral.dev/docs/basics-cache/current/en)
