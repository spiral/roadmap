## Permissions

The Spiral Framework includes the component `spiral/security`, which provides the ability to authorize user/actor access to specific resources or actions based on the list of associated privileges. The components implement "Flat RBAC" patterns described in NIST RBAC research. The implementation includes multiple additions such as an additional layer of rules to control the privilege/permission context, the ability to assign a role to multiple privileges using the wildcard pattern, and the ability to overwrite a role-to-permission assignment using the higher priority rule.

To use the RBAC component, we must register available roles and create an association between the role and the permission. Use the same Bootloader and `Spiral\Security\PermissionsInterface` for this purpose. Once the Bootloader is activated, you can use `Spiral\Core\GuardInterface` to check the access to the specific permissions, the guard will resolve active Actor automatically via dynamic scope using `Spiral\Security\GuardScope`.

Here is an example of how to set up permissions and check if the Actor has access to the specific permission:

```php
namespace App\Bootloader;

use Spiral\Boot\Bootloader\Bootloader;
use Spiral\Core\Container;
use Spiral\Security\Actor\Actor;
use Spiral\Security\ActorInterface;
use Spiral\Security\PermissionsInterface;

class ActorBootloader extends Bootloader
{
    public function boot(Container $container, PermissionsInterface $rbac): void
    {
        $container->bindSingleton(ActorInterface::class, new Actor(['user']));

        $rbac->addRole('user');
        $rbac->associate('user', 'home.read');
    }
}
```

Accessing:
```php
namespace App\Controller;

use Spiral\Security\GuardInterface;

class HomeController
{
    public function index(GuardInterface $guard): string
    {
        if (!$guard->allows('home.read')) {
            return 'can not read';
        }

        return 'can read';
    }
}
```

### Links and materials to read more:
1. [Spiral Security - Role Based Access Control](https://spiral.dev/docs/security-rbac/current/en)
