## Roles

In Spiral, roles are used to manage user permissions. Each user is associated with one or more roles, and each role is associated with one or more permissions. To use the RBAC component, you must register available roles and create an association between the role and the permission. You can use the `Spiral\Security\PermissionsInterface` for this purpose. Once the roles are created, you can associate them with permissions using the `associate` method.

Here is an example of how to create a role and associate it with a permission:

```php
namespace App\Bootloader;

use Spiral\Boot\Bootloader\Bootloader;
use Spiral\Security\PermissionsInterface;

class SecurityBootloader extends Bootloader
{
    public function boot(PermissionsInterface $rbac): void
    {
        $rbac->addRole('user');
        $rbac->associate('user', 'home.read');
    }
}
```

### Links and materials to read more:
1. [Spiral Security - Role Based Access Control](https://spiral.dev/docs/security-rbac/current/en)
