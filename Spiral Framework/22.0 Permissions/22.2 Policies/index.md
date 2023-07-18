## Policies

In addition to roles, Spiral also provides a way to manage permissions using policies. Policies are rules that determine what actions a user can perform on a specific resource. They provide an additional layer of rules to control the privilege/permission context.

You can create complex role-permission associations using policies. For example, you can grant access to all of the namespace permissions, excluding specific ones. To forbid role access, you can use `Spiral\Security\Rule\ForbidRule`.

Here is an example of how to create a policy:

```php
namespace App\Bootloader;

use Spiral\Boot\Bootloader\Bootloader;
use Spiral\Security\PermissionsInterface;
use Spiral\Security\Rule\ForbidRule;

class SecurityBootloader extends Bootloader
{
    public function boot(PermissionsInterface $rbac): void
    {
        $rbac->addRole('guest');
        $rbac->associate('guest', 'home.*');
        $rbac->associate('guest', 'home.read', ForbidRule::class);
    }
}
```

### Links and materials to read more:
1. [Spiral Security - Role Based Access Control](https://spiral.dev/docs/security-rbac/current/en)
