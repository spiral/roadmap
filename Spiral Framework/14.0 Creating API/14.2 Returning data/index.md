# Returning data

When creating an API, it's important to structure your responses in a way that's easy for clients to understand and use. Spiral Framework provides several ways to return data from your API endpoints.

You can return data directly from your controller methods, and Spiral will automatically convert it to a JSON response. If you need more control over the response, you can use the `ResponseFactory` service to create a response with custom headers, status code, and body.

```php
// Returning data
use Spiral\Http\Response\ResponseFactory;

public function index(ResponseFactory $response)
{
    $data = ['message' => 'Hello, world!'];

    return $response->json($data);
}
```

### Links and materials to read more:
1. [Responses](https://spiral.dev/docs/http-request-response/current/en)