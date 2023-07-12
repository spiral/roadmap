# 06.1 Saving entities

Saving entities in Spiral Framework involves creating an instance of your entity, setting its properties, and then using the `persist` and `run` methods of the `Transaction` class to save it to the database. This process is also known as persisting an entity.

```php
$user = new User();
$user->username = 'test';
$user->password = 'test';

$transaction = new Transaction($orm);
$transaction->persist($user);
$transaction->run();
```

In the following example, we create a new `User` entity, set its `username` and `password` properties, and then persist it to the database using a `Transaction`.

### Links and materials to read more:
1. [Cycle ORM Docs](https://cycle-orm.dev/docs)
2. [Database and ORM](https://spiral.dev/docs/basics-orm/current/en)
