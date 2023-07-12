# Mocking Databases

For more realistic testing, you can mock your database. This involves pointing your target database to another driver, usually a runtime SQLite. This allows you to test your application code in a more realistic environment, but be aware that your tests might take longer to execute.

```
public function setUp()
{
    $root = dirname(__DIR__) . '/';

    $app = $this->app = \\App::init([
        'root'        => $root,
        'libraries'   => $root . 'vendor/',
        'application' => $root . 'app/',
    ], null, null, false);

    //Replace default database
    $this->app->dbal->addDatabase(new Database(
        $this->app->dbal->driver('runtime'),
        'default',
        'tests_'
    ));

    //Monolog love to write to CLI when no handler is set
    $this->app->logs->debugHandler(new NullHandler());

    //Schemas and seeds
    $this->app->console->run('orm:schema', ['-alter'=>true]);
    $this->app->console->run('app:seed');
}
```

### Links and materials to read more:
1. [Testing Application](https://spiral.dev/docs/application-testing/current/en)
