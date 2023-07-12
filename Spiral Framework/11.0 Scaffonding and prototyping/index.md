# Scaffolding and prototyping

Spiral Framework provides powerful tools for scaffolding and prototyping, which can significantly speed up the development process. These tools allow developers to quickly generate application code for various classes using a set of console commands.

## Scaffolding

Spiral provides a scaffolder component that enables developers to quickly and easily generate application code for various classes, using a set of console commands. These include application bootloaders, console commands, application configs, HTTP controllers, middleware, request filters, and queue job handlers.

The scaffolder component can be customized to fit your needs by replacing declaration generators and their options using the scaffolder configuration file. You can customize the class namespace, postfix, and declaration type for each available class declaration type.

```php
// Example of using the PrototypeTrait in a class
namespace App\Endpoint\Web;

use Spiral\Prototype\Traits\PrototypeTrait;

class HomeController
{
    use PrototypeTrait;

    public function index()
    {
        return $this->views->render('profile', [
            'user' => $this->users->findByName('Antony')
        ]);
    }
}
```

## Prototyping

Spiral comes with a development extension that speeds up the development of application services, controllers, middleware, and other classes via AST modification. This extension includes IDE-friendly tooltips for most common framework components and Cycle Repositories.

To use the prototyping abilities of the framework, add `Spiral\Prototype\Traits\PrototypeTrait` to any of your classes. Once it's added, your IDE will immediately suggest available classes and Cycle Repositories to you.

```php
// Example of customizing the scaffolder configuration
use Spiral\Scaffolder\Declaration;

return [
    'declarations' => [
        Declaration\MiddlewareDeclaration::TYPE => [
            'class' => Declaration\MiddlewareDeclaration::class,
        ],
        Declaration\CommandDeclaration::TYPE => [
            'namespace' => 'Endpoint\Console',
        ],
        Declaration\JobHandlerDeclaration::TYPE => [
            'namespace' => 'Endpoint\Queue',
            'postfix' => 'Job',
        ],
    ],
];
```

### Links and materials to read more:
1. [Prototyping](https://spiral.dev/docs/basics-prototype/current/en)
2. [Scaffolding](https://spiral.dev/docs/basics-scaffolding/current/en)
