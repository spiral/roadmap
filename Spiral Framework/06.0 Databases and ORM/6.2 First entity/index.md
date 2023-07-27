## First entity

Entity in Spiral Framework is an object that represents data and its relations to different entities. 
Through the power of CycleORM it allows to map object structure and configuration into database table.

```php
namespace App\Entity;

use Cycle\Annotated\Annotation\Column;
use Cycle\Annotated\Annotation\Entity;
use App\Repository\UserRepository;
use Cycle\Annotated\Annotation\Relation\ManyToMany;
use Doctrine\Common\Collections\Collection;

#[Entity(repository: UserRepository::class)]
class User
{
    #[Column(type: 'primary')]
    public int $id;

    #[Column(type: 'string', name: 'first_name')]
    public string $firstName;
    
    #[Column(type: 'string', name: 'last_name')]
    public string $lastName;

    #[Column(type: 'string')]
    public string $email;

    #[ManyToMany(target: Group::class, through: UserGroup::class)]
    public Collection $groups;
}
```

### Links and materials to read more:
1. [Cycle ORM Docs](https://cycle-orm.dev/docs)
2. [Database and ORM](https://spiral.dev/docs/basics-orm/current/en)