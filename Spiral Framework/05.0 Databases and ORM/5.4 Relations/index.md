# 05.4 Relations

Relations in Spiral Framework are managed through Cycle ORM. It allows you to define the relationships between your entities, such as one-to-one, one-to-many, and many-to-many.

```
namespace App\Entity;

use Cycle\Annotated\Annotation\Entity;
use Cycle\Annotated\Annotation\Column;
use Cycle\Annotated\Annotation\Relation\BelongsTo;

/**
 * @Entity()
 */
class Post
{
    // ...

    /**
     * @BelongsTo(target="User", nullable=false)
     * @var User
     */
    public $user;
}
```

### Links and materials to read more:
1. [Cycle ORM Docs](https://cycle-orm.dev/docs)
2. [Database and ORM](https://spiral.dev/docs/basics-orm/current/en)