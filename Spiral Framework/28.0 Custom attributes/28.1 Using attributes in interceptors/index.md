# Using attributes in interceptors

Interceptors in Spiral Framework are a powerful tool for adding functionality to your application without modifying the core code. They can be used to handle cross-cutting concerns like logging, caching, and more. Attributes can be used in conjunction with interceptors to further enhance their functionality.

For example, you can create an interceptor that logs slow database queries. You can use an attribute to specify which methods should be logged, and the interceptor can read this attribute and act accordingly. This allows you to control the behavior of the interceptor on a per-method basis, giving you fine-grained control over its behavior.

Here is an example of how to use attributes in an interceptor:

```php
namespace App\Integration\Database\Interceptor;

use Psr\Log\LoggerInterface;
use Spiral\Core\CoreInterceptorInterface;
use Spiral\Core\CoreInterface;

class SlowQueryDetectorInterceptor implements CoreInterceptorInterface
{
    public function __construct(
        private readonly LoggerInterface $logger
    ) {
    }

    public function process(string $database, string $sql, array $parameters, CoreInterface $core): mixed
    {
        $startTime = \microtime(true);

        $result = $core->callAction($database, $sql, $parameters);
        
        $elapsed = \microtime(true) - $startTime;

        if ($elapsed > 0.1) {
            $this->logger->warning(
                'Slow query detected',
                [
                    'database' => $database,
                    'sql' => $sql,
                    'parameters' => $parameters,
                    'elapsed' => $elapsed
                ]
            );
        }

        return $result;
    }
}
```

### Links and materials to read more:
1. [Interceptors in Spiral Framework](https://spiral.dev/docs/framework-interceptors/current/en)
