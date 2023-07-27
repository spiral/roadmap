### Input validation

Input validation is a crucial part of any API. It ensures that the data your API receives is in the correct format 
and meets your application's requirements. Spiral Framework provides a powerful validation library and request filters 
that allow you to validate incoming HTTP requests in a simple and flexible way.

```php
use Spiral\Filters\Model\Filter;
use Spiral\Filters\Model\FilterDefinitionInterface;
use Spiral\Filters\Model\HasFilterDefinition;
use Spiral\Validator\FilterDefinition;
use Spiral\Filters\Attribute\Input\Post;

final class CreateUser extends Filter implements HasFilterDefinition
{
    #[Post(key: 'email')]
    public string $email;

    #[Post(key: 'password')]
    public string $password;

    public function filterDefinition(): FilterDefinitionInterface
    {
        return new FilterDefinition([
            'email' => [['required']],
            'password' => [['required']],
        ]);
    }
}
```

This filter can be requested in a API controller method and will be automatically validated before being passed to the method.

```php
final class UserController
{
    public function create(CreateUser $request)
    {
        // $request already validated at this point
        $email = $request->email;
        $password = $request->password;
        
        // ...
    }
}
```

You can define validation rules for your API endpoints and apply them to the incoming request data. If the validation fails, Spiral will automatically generate a response with the validation errors.

### Links and materials to read more:
1. [Request Validation](https://spiral.dev/docs/validation-spiral/current/en)