## 06.1 Saving entities

Saving entities in Spiral Framework involves creating an instance of your entity, setting its properties, and then using the `persist` and `run` methods of the `EntityManagerInterface` implementation to save it to the database. This process is also known as persisting an entity.

```php
use Cycle\ORM\EntityManagerInterface;

final class UserService
{
    public function __construct(
        private readonly EntityManagerInterface $entityManager
    ) {
    }
    
    public function create(string $email, string $password): void
    {
        $user = new User();
        $user->email = $email;
        $user->password = $password;
        
        $this->entityManager->persist($user);
        $this->entityManager->run();
    }   
}

```

In the following example, we create a new `User` entity, set its `username` and `password` properties, and then persist it to the database using a `EntityManagerInterface`.

### Links and materials to read more:
1. [Cycle ORM Docs](https://cycle-orm.dev/docs)
2. [Database and ORM](https://spiral.dev/docs/basics-orm/current/en)
