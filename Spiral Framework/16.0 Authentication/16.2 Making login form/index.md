### Making login form

Creating a login form in Spiral Framework involves creating a form in your application and handling the form submission 
in a controller. The form should include fields for the user's credentials, such as their email and password. 
When the form is submitted, the controller should validate the input, find a user, check user credentials, and start a session.

Below is an example of how a login form can be handled:

```php
use Spiral\Auth\AuthScope;
use Spiral\Auth\TokenStorageInterface;

final class Authenticator
{
    public function __construct(
        private readonly UserRepository $userRepository,
        private readonly PasswordHasher $hasher,
        private readonly AuthScope $authScope,
        private readonly TokenStorageInterface $tokenStorage
    ) {
    }

    public function start(string $email, string $plainPassword): void
    {
        $user = $this->userRepository->findByEmail($email);
        if ($user === null) {
            throw new InvalidCredentialsException(
                'The Email is not associated with any account. Please check your Email and try again.'
            );
        }

        if (!$this->hasher->compare($plainPassword, $user->passwordHash)) {
            throw new InvalidCredentialsException(
                'Incorrect password. Please try again.'
            );
        }

        $token = $this->tokenStorage->create(['userID' => $user->getId()]);

        $this->authScope->start($token);
    }
}
```

### Links and materials to read more:
1. [Quick Start Guide](https://spiral.dev/docs/basics-quick-start/2.9/en)
