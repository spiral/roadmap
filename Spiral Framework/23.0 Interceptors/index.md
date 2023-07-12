# Interceptors

One of the key features of Spiral is its support for interceptors, which can be used to add functionality to the application without modifying the core code of the application. This can help to keep your codebase more modular and maintainable. Interceptors work similarly to middleware in HTTP requests, in that they allow developers to add functionality to the application at various points in the processing flow. However, unlike middleware which is typically specific to HTTP requests, interceptors can be used to add functionality to a wide range of components.

Interceptors should implement the `Spiral\Core\CoreInterceptorInterface` interface, which requires them to define a `process` method. This method is called by the framework at specific points in the application's execution, such as before or after a controller action is invoked.

Here is an example of how to set up an interceptor:

```
namespace App\Integration\Database\Interceptor;

use Spiral\Core\CoreInterceptorInterface;
use Spiral\Core\CoreInterface;
use Cycle\Database\Exception\StatementException\ConnectionException;

final class DatabaseConnectionInterceptor implements CoreInterceptorInterface
{
    public function process(string $database, string $sql, array $parameters, CoreInterface $core): mixed
    {
        try {
            return $core->callAction($database, $sql, $parameters);
        } catch (ConnectionException $e) {
            // Try to reconnect...
            return $this->process('slave', $sql, $parameters, $core);
        }
    }
}
```

### Links and materials to read more:
1. [Spiral Interceptors](https://spiral.dev/docs/framework-interceptors/current/en)
