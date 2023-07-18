## Debugging with Xdebug

Xdebug is a powerful debugging and profiling tool for PHP. It provides a range of features like stack traces, breakpoints, and profiling information. Xdebug can be a valuable tool when debugging long-living processes in Spiral Framework.

However, keep in mind that using Xdebug with long-living processes can have a significant impact on performance. Therefore, it's recommended to use it in a development environment and disable it in production.

Xdebug can be installed as a PHP extension and configured in your `php.ini` file. Once installed, you can use it with various IDEs like PhpStorm, VS Code, etc., which provide built-in support for Xdebug.

Remember, debugging long-living processes requires a different approach compared to traditional web requests due to their persistent nature.

### Links and materials to read more:
1. [Xdebug](https://xdebug.org/docs/)
2. [Debugging in Spiral Framework](https://spiral.dev/docs/basics-debugging/current/en)
