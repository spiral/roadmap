# Reading and Storing Data

Working with data is a fundamental part of any application. In Spiral Framework, this involves interacting with the database and ORM (Object-Relational Mapping) to read and store data.

The Spiral Framework uses Cycle ORM, a PHP DataMapper, and ORM that simplifies the interaction between your PHP application and the database. It provides a simple, flexible, and powerful API to perform various database operations.

The process of reading and storing data in Spiral Framework typically involves:

- **Entities**: These are the PHP objects that represent the data you're working with. Each entity corresponds to a table in the database, and each instance of an entity represents a row in that table.

- **Repositories**: These are classes that encapsulate the database queries related to a specific entity. They provide methods to fetch and save entities, making it easier to perform common database operations.

- **Transactions**: These are used to ensure that multiple database operations are performed atomically. This means that if one operation fails, all the operations in the transaction are rolled back, maintaining the integrity of your data.

- **Queries**: These are used to fetch data from the database. Cycle ORM provides a powerful query builder that allows you to create complex queries in an easy-to-understand way.

In the following sections, we'll dive deeper into each of these topics, providing examples and links to further resources for you to explore.

### Links and materials to read more:
1. [Cycle ORM Docs](https://cycle-orm.dev/docs)
2. [Database and ORM](https://spiral.dev/docs/basics-orm/current/en)
