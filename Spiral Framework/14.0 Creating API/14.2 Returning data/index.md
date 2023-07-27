## Returning data

When creating an API, it's important to structure your responses in a way that's easy for clients to understand and use.
Spiral Framework provides several ways to return data from your API endpoints.

You can return data directly from your controller methods, and Spiral will automatically convert it to a JSON response. 
If you need more control over the response, you can use the `ResponseWrapper` service to create a response with custom headers, 
status code, and body.

#### ResponseWrapper

```php
use Psr\Http\Message\ResponseInterface;
use Spiral\Http\ResponseWrapper;

public function index(ResponseWrapper $response): ResponseInterface
{
    $data = ['message' => 'Hello, world!'];

    return $response->json($data);
}
```

#### JsonSerializable

```php
final class Response implements \JsonSerializable
{
    public function __construct(
        private readonly array $data
    ) {
    }

    public function jsonSerialize(): array
    {
        return $this->data;
    }
}

public function index(): \JsonSerializable
{
    return new Response(['message' => 'Hello, world!']);
}
```

#### Returning array directly

```php
public function index(): array
{
    return [
        'message' => 'Hello, world!'
    ];
}
```

### Links and materials to read more:
1. [Responses](https://spiral.dev/docs/http-request-response/current/en)
