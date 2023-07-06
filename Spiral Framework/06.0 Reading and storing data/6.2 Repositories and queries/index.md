# 06.2 Repositories and queries

Repositories in Spiral Framework provide a way to encapsulate database queries related to a specific entity. You can use the `select` method of the `Repository` class to create queries. This method returns a `Select` object, which you can use to add conditions to your query and fetch the results.

```php
$users = $orm->getRepository(User::class)->select()->where('username', 'test')->fetchAll();
```

In the following example, we use the `select` method to create a query that fetches all `User` entities where the `username` is 'test'.

### Links and materials to read more:
1. [Cycle ORM Docs](https://cycle-orm.dev/docs)
2. [Database and ORM](https://spiral.dev/docs/basics-orm/current/en)
