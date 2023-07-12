08.1 Creating forms in template

# Creating forms in template

Forms in Spiral Framework are mostly regular HTML forms that have the AJAX submission functionality on top. The form can be created using standard HTML form elements. Once the form is submitted, you can access the submitted data in your Spiral controller using the `request` object.

Here is an example of how to create a form using HTML:

```html
<form action="/submit" method="POST">
    <input type="text" id="name" name="name"><br>
    <input type="password" id="password" name="password"><br>
    <input type="submit" value="Submit">
</form>
```

And here is how you can access the submitted data in your Spiral controller:
```
use Spiral\Http\Request\InputManager;

class UserController
{
    public function submit(InputManager $input)
    {
        $name = $input->data('name');
        $password = $input->data('password');

        // Process the submitted data...
    }
}

```

Links and materials to read more:
1. [Spiral Validation](https://spiral.dev/docs/validation-spiral/current/en)