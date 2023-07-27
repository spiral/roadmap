## Reading user data

The Spiral Framework follows the **PSR-7** and **PSR-15** standards. Reading user data in Spiral Framework involves 
retrieving data sent by the user to the server via HTTP requests. This data can be sent through the URL (GET), 
form submissions (POST), or even through cookies and headers. Controller methods can receive `Psr\Http\Message\ServerRequestInterface` 
directly. Alternatively, you can use context-manager `Spiral\Http\Request\InputManager`, which can be stored inside 
singleton services/controllers, and always point to the current user request.

Here's a basic example of how you can read GET and POST data in Spiral Framework:

```php
// Reading GET data
$queryParams = $request->query->all();
$specificQueryParam = $request->query('specificKey');

// Reading POST data
$parsedBody = $request->->data->all();
$specificPostParam = $request->post('specificKey');
```

In these examples, `$request` is an instance of `Spiral\Http\Request\InputManager` which is automatically injected 
into your controller methods.

It is recommended to avoid direct access to `Psr\Http\Message\ServerRequestInterface` and `Spiral\Http\Request\InputManager` 
unless necessary, use **Request Filters** instead. The Filter class represents a set of request input fields 
that can be filtered and validated.

### Links and materials to read more:
1. [HTTP — Getting started](https://spiral.dev/docs/http-configuration/current/en)
2. [Request and Response in Spiral Framework](https://spiral.dev/docs/http-requests/current/en)
3. [Request Filters](https://spiral.dev/docs/filters-filter/current/en)
4. [Routing in Spiral Framework](https://spiral.dev/docs/http-routing/current/en)
