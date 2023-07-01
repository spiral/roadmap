# Singletons

Singletons are a design pattern that restricts a class to a single instance, providing a global point of access to it. This pattern is useful when exactly one object is needed to coordinate actions across the system.

In the Spiral Framework, Singletons are implemented via an interface or in a bootloader. One key point to keep in mind is that when a class is not explicitly defined as a Singleton, a new instance will be generated for each request.

This approach proves beneficial when there's a need to preserve data or maintain a connection between requests within the object properties.

1. [Singletons](https://refactoring.guru/design-patterns/singleton)
2. [Bootloaders](https://spiral.dev/docs/framework-bootloaders/current/en)