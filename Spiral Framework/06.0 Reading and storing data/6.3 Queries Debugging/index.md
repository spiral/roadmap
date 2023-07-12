# 06.3 Queries debugging

Debugging queries in Spiral Framework can be done using the `__toString` method of the `Select` class, which will return the SQL query as a string. This can be useful for understanding what SQL query is being executed when you run your query.

```php
$query = $orm->getRepository(User::class)->select()->where('username', 'test');
echo $query->__toString();
```

In the following example, we create a query and then print the SQL query to the console.

### Links and materials to read more:
1. [Cycle ORM Docs](https://cycle-orm.dev/docs)
2. [Database and ORM](https://spiral.dev/docs/basics-orm/current/en)
