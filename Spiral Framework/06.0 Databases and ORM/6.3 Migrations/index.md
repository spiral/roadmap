## 05.3 Migrations

Migrations in Spiral Framework are a way of applying version control to your database. They allow you to manage your database schema and data changes over time.

To generate migrations, use the console command:

```bash
php app.php cycle:migrate
```

The generated migration is located in **app/migrations/**. Execute it using:

```bash
php app.php migrate
```

### Links and materials to read more:
1. [Cycle ORM Docs](https://cycle-orm.dev/docs)
2. [Database and ORM](https://spiral.dev/docs/basics-orm/current/en)