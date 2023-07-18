## Cookies and sessions

Spiral Framework provides robust support for managing cookies and sessions, which are essential for maintaining state in web applications.

### Cookies

Cookies in Spiral are managed by the `CookieManager` middleware, which provides a `CookieQueue` class for managing cookies within a specific scope. This middleware is automatically mounted in the HTTP config and runs on every request, allowing you to access the cookie queue inside your controllers using either dependency injection or the shortcut `cookies`.

Note that `CookieQueue` is not the same as request cookies. To access request cookies, you can use `$this->input->cookies`.

```php
// Setting a cookie
public function indexAction(CookieQueue $cookies)
{
   $cookies->set('hello', 'world');
   
   $this->cookies->set('abc', 'value');
}
```

### Sessions

Spiral provides a `SessionInterface` for managing user sessions. You can access the user session using this interface. The session will be automatically started on first data access and committed when the request leaves `SessionMiddleware`.

```php
// Accessing the session
use Spiral\Session\SessionInterface;

public function index(SessionInterface $session): void
{
    $session->resume();
    dump($session->getID());
}
```

You can also create a named section of the session using the `getSection` method of the session object.

```php
// Creating a named section of the session
public function index(SessionInterface $session): void
{
    $cart = $session->getSection('cart');

    $cart->set('items', ['my-items']);

    dump($cart->getAll());
}
```

### Links and materials to read more:
1. [Sessions](https://spiral.dev/docs/basics-session/current/en)
2. [Cookies](https://spiral.dev/docs/http-cookies/current/en)
