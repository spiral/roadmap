# Setting Up Base Test

Before you start testing your Spiral application, you need to set up a base test. This is an abstract class that configures the environment for each test case. It initializes the application and sets up necessary services. After each test case, the application is destroyed to ensure that each test runs in a clean environment.

```php
abstract class BaseTest extends TestCase
{
    /**
     * @var \\App
     */
    protected $app;

    public function setUp()
    {
        $root = dirname(__DIR__) . '/';

        $app = $this->app = \\App::init([
            'root'        => $root,
            'libraries'   => $root . 'vendor/',
            'application' => $root . 'app/',
        ], null, null, false);

        //Monolog love to write to CLI when no handler is set
        $this->app->logs->debugHandler(new NullHandler());
    }

    /**
     * This method performs full destroy of spiral environment.
     */
    public function tearDown()
    {
        if (class_exists('Mockery')) {
            //Mockery defines it's own static container to be destructed
            \\Mockery::close();
        }

        //Forcing destruction
        $this->app = null;

        gc_collect_cycles();
        clearstatcache();
    }
}
```

### Links and materials to read more:
1. [Testing Application](https://spiral.dev/docs/application-testing/current/en)
