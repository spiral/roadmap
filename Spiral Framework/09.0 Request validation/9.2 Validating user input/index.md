## Validating user input

The validation component of Spiral allows you to validate data that is submitted by a user or received from an external source. 
The component does not contain any validator implementation out of the box. Instead, it provides a set of interfaces 
and abstract classes that define the expected behavior of a validator.

There are three validator bridges available for use with Spiral validation component:

- Spiral Validator - This is the default validator bridge. It is a simple, lightweight validator that can handle basic validation tasks.
- Symfony Validator - This validator bridge provides integration with the Symfony Validator component, which is a more powerful and feature-rich validation library.
- Laravel Validator - This validator bridge provides integration with the Laravel Validator, which is a validation component used in the Laravel framework.

The preferred way to validate incoming data is to use **Request Filters** with the validation rules described:

```php
use Psr\Http\Message\UploadedFileInterface;
use Spiral\Filters\Model\Filter;
use Spiral\Filters\Model\FilterDefinitionInterface;
use Spiral\Filters\Model\HasFilterDefinition;
use Spiral\Validator\FilterDefinition;
use Spiral\Filters\Attribute\Input\Post;
use Spiral\Filters\Attribute\Input\File;

final class CreatePost extends Filter implements HasFilterDefinition
{
    #[Post(key: 'title')]
    public string $title;

    #[Post(key: 'text')]
    public string $text;

    #[File]
    public UploadedFileInterface $image;

    public function filterDefinition(): FilterDefinitionInterface
    {
        return new FilterDefinition([
            'title' => [
                ['notEmpty'],
                ['string::length', 50]
            ], 
            'text' => [['notEmpty']],
            'image' => [['image::valid'], ['file::size', 1024]]
        ]);
    }
}
```

The filter example above contains validation rules using the **Spiral Validator** package. This filter can be requested 
in a controller method and will be automatically validated before being passed to the method. 
Inside a controller method, you don't need to validate the data. When some of the filter rule has an error, 
`Spiral\Filters\Exception\ValidationException` exception will be thrown. Spiral will automatically catch this exception 
via the `Spiral\Filter\ValidationHandlerMiddleware` middleware and return a response with the error message via 
`Spiral\Filters\ErrorsRendererInterface`.

Or you can use the `Spiral\Validation\ValidatorInterface` interface to validate the data manually:

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
    }
}
```

Links and materials to read more:
1. [Spiral Validation](https://spiral.dev/docs/validation-spiral/current/en)
2. [Request Filters](https://spiral.dev/docs/filters-configuration/current/en)
