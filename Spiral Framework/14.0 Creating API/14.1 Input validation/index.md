## Input validation

Input validation is a crucial part of any API. It ensures that the data your API receives is in the correct format and meets your application's requirements. Spiral Framework provides a powerful validation library that allows you to validate incoming HTTP requests in a simple and flexible way.

```
// Input validation
use Spiral\Validation\ValidationInterface;

public function create(ValidationInterface $validation)
{
    $validation->rule('name', 'notEmpty')->rule('email', 'email');

    if (!$validation->isValid()) {
        return $validation->getErrors();
    }

    // Continue processing...
}
```

You can define validation rules for your API endpoints and apply them to the incoming request data. If the validation fails, Spiral will automatically generate a response with the validation errors.

### Links and materials to read more:
1. [Request Validation](https://spiral.dev/docs/validation-spiral/current/en)