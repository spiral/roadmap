# 05.5 Schema debugging

Schema debugging in Spiral Framework involves inspecting your database schema to ensure it matches your entities' configurations. This can be done using various tools and techniques.

```
$schema = $orm->getSchema();
$table = $schema->define('users');

var_dump($table->getColumns());
```

### Links and materials to read more:
1. [Cycle ORM Docs](https://cycle-orm.dev/docs)
2. [Database and ORM](https://spiral.dev/docs/basics-orm/current/en)