## Validating user input

The validation component of Spiral allows you to validate data that is submitted by a user or received from an external source. The component does not contain any validator implementation out of the box. Instead, it provides a set of interfaces and abstract classes that define the expected behavior of a validator.

There are three validator bridges available for use with Spiral validation component:

- Spiral Validator - This is the default validator bridge. It is a simple, lightweight validator that can handle basic validation tasks.
- Symfony Validator - This validator bridge provides integration with the Symfony Validator component, which is a more powerful and feature-rich validation library.
- Laravel Validator - This validator bridge provides integration with the Laravel Validator, which is a validation component used in the Laravel framework.

Here is an example of how to validate data using the default validator:

```php
use Spiral\Http\Request\InputManager;
use Spiral\Validation\ValidatorInterface;

class UserController
{
    public function create(InputManager $input, ValidatorInterface $validator)
    {
        $validator = $validator->validate([
            'username' => $input->post('username'),
            'email' => $input->post('email'),
        ], [
            'username' => 'required',
            'email' => 'required|email',
        ]);
        
        if (!$validator->isValid()) {
            $errors = $validator->getErrors();
            // ...
        }

        // Store the user in the database...
    }
}
```

Links and materials to read more:
1. [Spiral Validation](https://spiral.dev/docs/validation-spiral/current/en)