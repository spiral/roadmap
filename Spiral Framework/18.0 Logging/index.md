# Logging
Logging is an essential part of any application. It helps in debugging issues and keeping track of application activities. Spiral Framework uses Monolog, a popular logging library for PHP. Monolog allows for a variety of powerful log handling and storage options.

In Spiral, you can configure logging channels that handle different types of log messages. Each channel can have its own set of handlers and processors. Handlers are responsible for writing the log entries to their respective targets, such as files, databases, or external services. Processors modify the log entries before they are written, for example, by adding additional information.

To use logging in your Spiral application, you can obtain an instance of the Psr\Log\LoggerInterface from the container. This logger is configured with the settings defined in your application's configuration.

```php
// Obtaining an instance of the logger
$logger = $container->get(\Psr\Log\LoggerInterface::class);

```

You can log messages at different levels, including debug, info, notice, warning, error, critical, alert, and emergency. Each level represents a different severity of the log message.
```php
// Logging a message
$logger->info('This is an informational message');
$logger->error('An error occurred');
```

Links and materials to read more:
1. [Monolog Documentation](https://github.com/Seldaek/monolog)
2. [PSR-3 Logger Interface](https://www.php-fig.org/psr/psr-3/)