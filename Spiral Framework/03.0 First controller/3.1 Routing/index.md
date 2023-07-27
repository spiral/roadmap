## Routing

The Router component allows to set under what URL the resource will be available. In the Spiral Framework, 
you have multiple methods to accomplish this. However, the simplest and highly recommended approach is to utilize attributes.

```php
#[Route(route: '/', name: 'index', methods: 'GET')]
public function index(): string
{
    return $this->views->render('home');
}
```

> **Note**
> Make sure to add `Spiral\Router\Bootloader\AnnotatedRoutesBootloader` to your application kernel before using attributes.

You can set HTTP method that will lead to given controller method and you can set additional parameters like id of the resource you want to process.

### Links and materials to read more:
1. [HTTP Routing](https://spiral.dev/docs/http-routing/current/en)
