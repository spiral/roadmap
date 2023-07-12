# Testing HTTP Methods

Spiral provides a `HttpTest` class that allows you to emulate user requests, cookies, and sessions. This is useful for testing how your application responds to different HTTP methods like GET, POST, DELETE, and PUT.

```
class IndexTest extends HttpTest
{
    public function testSeeWelcome()
    {
        $response = $this->get('/');

        $this->assertSame(200, $response->getStatusCode());
        $this->assertContains('Welcome to Spiral Framework', (string)$response->getBody());
        $this->assertContains('welcome.dark.php', (string)$response->getBody());
    }
}
```

### Links and materials to read more:
1. [Testing HTTP Methods](https://spiral.dev/docs/testing-http/current/en)
