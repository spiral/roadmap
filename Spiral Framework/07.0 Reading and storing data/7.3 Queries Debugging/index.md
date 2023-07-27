## 06.3 Queries debugging

The Spiral Framework has the ability to enable logging of all requests for a specific database driver.
This can be useful for understanding what SQL query is being executed when you run your query.

To enable logging, you need to use the **app/config/monolog.php** configuration file:

```php
'handlers' => [
    // ...
    \Cycle\Database\Driver\Postgres\PostgresDriver::class => [
        [
            'class' => 'log.rotate',
            'options' => [
                'filename' => directory('runtime') . 'logs/sql.log',
                'level' => Logger::DEBUG,
            ],
        ],
    ],
    // ...
```

Or you can use the `__toString` method of the `Select` class, which will return the SQL query as a string.

```php
$query = $orm->getRepository(User::class)->select()->where('username', 'test');
echo $query->__toString();
```

In the following example, we create a query and then print the SQL query to the console.

### Links and materials to read more:
1. [Cycle ORM Docs](https://cycle-orm.dev/docs)
2. [Database and ORM](https://spiral.dev/docs/basics-orm/current/en)
