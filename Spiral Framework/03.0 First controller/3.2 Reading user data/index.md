## Reading user data

Reading user data in Spiral Framework involves retrieving data sent by the user to the server via HTTP requests. This data can be sent through the URL (GET), form submissions (POST), or even through cookies and headers.

Here's a basic example of how you can read GET and POST data in Spiral Framework:

```php
// Reading GET data
$queryParams = $request->getQueryParams();
$specificQueryParam = $request->getQueryParam('specificKey');

// Reading POST data
$parsedBody = $request->getParsedBody();
$specificPostParam = $request->getParsedBodyParam('specificKey');
```

In these examples, `$request` is an instance of `Spiral\Http\Request\InputManager` which is automatically injected into your controller methods.

### Links and materials to read more:
1. [HTTP — Getting started](https://spiral.dev/docs/http-configuration/current/en)
2. [Request and Response in Spiral Framework](https://spiral.dev/docs/http-requests/current/en)
3. [Routing in Spiral Framework](https://spiral.dev/docs/http-routing/current/en)

