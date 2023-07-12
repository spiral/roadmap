# Environment variables

Environment variables are a great way to separate the configuration of your application from the code itself. This makes it easy to store sensitive information like database credentials, API keys, and other configs that you don't want to hardcode into your application.

Spiral integrates with Dotenv through the `Spiral\DotEnv\Bootloader\DotenvBootloader` class. This bootloader is responsible for loading the environment variables from the `.env` file and making them available to the application. It is a common practice to include a `.env.sample` file in a new project which can be used as a guide for setting up the environment variables.

You can access environment variables using `Spiral\Boot\EnvironmentInterface` or via a short function `env()`.

```php
// Accessing environment variables using Spiral\Boot\EnvironmentInterface
use Spiral\Boot\EnvironmentInterface;

final class GithubClient
{
    public function __construct(
        private readonly EnvironmentInterface $env
    ) {}

    public function getAccessToken(): ?string
    {
        return $this->env->get('GITHUB_ACCESS_TOKEN');
    }
}
```


Remember that the values in `.env` will be pre-processed, the following changes will take place:
```php
// Accessing environment variables via a short function env()
return [
    'access_token' => env('GITHUB_ACCESS_TOKEN'),
    // ...
];
```

- `true` or `(true)` will be converted to boolean `true`
- `false` or `(false)` will be converted to boolean `false`
- `null` or `(null)` will be converted to `null`
- `empty` will be converted to an empty string `''`

The quotes around strings will be stripped automatically.

### Links and materials to read more:
1. [Environment Variables](https://spiral.dev/docs/start-configuration/current/en)
