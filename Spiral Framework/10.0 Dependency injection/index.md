10.0 Dependency Injection

# Dependency Injection

Dependency Injection is a design pattern that allows an object to receive other objects it depends on. Spiral includes a set of tools that makes it easier to manage dependencies and create objects in your code. One of the main tools is the container, which helps you handle class dependencies and automatically "injects" them into the class. This means that instead of creating objects and setting up dependencies manually, the container takes care of it for you.

The Spiral container also follows a set of PSR-11 Container standards, which ensures compatibility with other libraries. In your code, you can access the container by asking for the `Psr\Container\ContainerInterface`.

The Spiral container allows you to use both constructor and method injections for your classes. This means that you can have dependencies automatically injected into the class through the constructor, or through a specific method.

### Links and materials to read more:
1. [Container and DI](https://spiral.dev/docs/framework-container/current)
