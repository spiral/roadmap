### Making registration form

Creating a registration form in Spiral Framework involves creating a form in your application and handling the form 
submission in a controller. The form should include fields for the user's information, such as their name, email, and password. 
When the form is submitted, the controller should validate the input, create a new user in the database, and log the user in.

Below is an example of how a user session can be started after creating a user:

```php
/** 
 * @var \Spiral\Auth\AuthScope $authScope
 * @var \Spiral\Auth\TokenStorageInterface $tokenStorage
 */

$token = $tokenStorage->create(['userID' => $user->getId()]);
$authScope->start($token);
```

### Links and materials to read more:
1. [Quick Start Guide](https://spiral.dev/docs/basics-quick-start/2.9/en)
