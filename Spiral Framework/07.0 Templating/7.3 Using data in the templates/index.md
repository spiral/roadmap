# Using data in the templates

Data can be passed to the templates using the `with` method of the `ViewInterface`. This method accepts an array of data that will be available in the template.

```php
return $views->get('home')
   ->with(['name' => 'John Doe']);
```

### Links and materials to read more:
1. [Spiral Views](https://spiral.dev/docs/views-configuration/current/en)
