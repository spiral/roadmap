# Middlewares

Middlewares in Spiral Framework are based on the PSR-15 standard, which defines a common interface for processing HTTP server requests using middleware. Middleware is responsible for handling functionality that is related to the request and response, such as authentication, caching, or logging. It can modify the request and response before they are passed on to the router, but it cannot make decisions about which routes should be handled by the application.

```
// Creating a middleware
namespace App\Endpoint\Web\Middleware;

use Psr\Http\Server\MiddlewareInterface;
use Psr\Http\Message\ServerRequestInterface;
use Psr\Http\Server\RequestHandlerInterface;
use Psr\Http\Message\ResponseInterface;

class MyMiddleware implements MiddlewareInterface
{
    public function process(
        ServerRequestInterface $request, 
        RequestHandlerInterface $handler
    ): ResponseInterface {
        return $handler->handle($request)->withAddedHeader('My-Header', 'my-value');
    }
}
```

Spiral provides several ways to set middleware, allowing developers to choose the approach that best fits their needs. You can activate a global middleware that applies to all routes and requests, or you can configure middleware that's grouped and will only be applied to routes within the corresponding group. You can also apply middleware to a specific route.

```
// Adding a middleware to a route
namespace App\Application\Bootloader;

use Spiral\Bootloader\Http\RoutesBootloader as BaseRoutesBootloader;
use Spiral\Router\Loader\Configurator\RoutingConfigurator;
use App\Endpoint\Web\Middleware\MyMiddleware;

final class RoutesBootloader extends BaseRoutesBootloader
{
    protected function defineRoutes(RoutingConfigurator $routes): void
    {
        $routes->add(name: 'news.show', pattern: '/news/<id:int>')
            ->middleware(['middleware:web', MyMiddleware::class]);
    }
}
```

Spiral Framework allows developers to combine middleware with the IoC scope to create a request-specific application context. This allows developers to set up a context for the current request, which can be accessed by other parts of the application. This can be useful for tasks such as logging or data access, where the context of the request is important.

### Links and materials to read more:
1. [Middlewares](https://spiral.dev/docs/http-middleware)
