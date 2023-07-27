## First controller

Controller is part of MVC architecture pattern responsible for handling incoming PSR-7 compatible requests,
processing data, and then returning a response to the client.

To create your first controller effortlessly, use the scaffolding command:

```bash
php app.php create:controller HomeController --action index
```

This will create a new **HomeController** class:

```php
use Psr\Http\Message\ResponseInterface;
use Spiral\Router\Annotation\Route;

class HomeController
{
    /**
     * Please, don't forget to configure the Route attribute or remove it and register the route manually.
     */
    #[Route(route: 'path', name: 'name')]
    public function index(): ResponseInterface
    {
    }
}
```

Following the code generation through the scaffolding command, the next step involves implementing the controller methods.

### Links and materials to read more:
1. [First controller](https://spiral.dev/docs/start-http-basics/current/en)
2. [Scaffolding](https://spiral.dev/docs/basics-scaffolding/current/en)
