## CLI Commands

Command Line Interface (CLI) commands are a powerful tool in Spiral Framework. They empower you to automate tasks, perform maintenance, and much more. You can add new console commands to your application or register plugin commands using bootloaders. The component is configured by default to automatically discover commands located in the `app/src` directory.

To create a new command, you can either extend `Symfony\Component\Console\Command\Command` or `Spiral\Console\Command`. Extending the `Spiral\Console\Command` class provides some additional syntax sugar and convenience methods that can make it easier to build your command.

Spiral offers the ability to define console commands using PHP attributes. This allows for a more intuitive and streamlined approach to defining commands with clear separation of concerns.

Here's an example of defining a console command using attributes:

```php
namespace App\Api\Cli\Command;

use Spiral\Console\Attribute\Argument;
use Spiral\Console\Attribute\AsCommand;
use Spiral\Console\Attribute\Option;
use Spiral\Console\Command;
use Symfony\Component\Console\Input\InputOption;

#[AsCommand(
    name: 'app:create:user', 
    description: 'Creates a user with the given data'
)]
final class CreateUser extends Command
{
    #[Argument]
    private string $email;

    #[Argument(description: 'User password')]
    private string $password;

    #[Argument(name: 'username', description: 'The user name')]
    private string $userName;

    #[Option(shortcut: 'a', name: 'admin', description: 'Set the user as admin')]
    private bool $isAdmin = false;

    public function __invoke(): int
    {
        $user = new User(
            email: $this->email,
            password: $this->password,
        );
        
        $user->setIsAdmin($this->isAdmin);
        
        // Save user to database...

        return self::SUCCESS;
    }
}
``` 

Links and materials to read more:
1. [Console Application - User Commands](https://spiral.dev/docs/console-commands/current)