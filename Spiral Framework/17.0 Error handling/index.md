## Error Handling

Error handling in Spiral Framework is managed through a set of components that intercept and log critical errors and user-level exceptions. The framework includes a default error handling middleware `Spiral\Http\Middleware\ErrorHandlerMiddleware` which is used to intercept and log these errors. This middleware can be enabled in the global middleware list.

The framework also provides several exceptions that can be thrown from your controllers and middleware to cause HTTP level error pages. For example, you can trigger a 404 Not Found using `NotFoundException`.

### Links and materials to read more:
1. [Error Handling Documentation](https://spiral.dev/docs/http-errors/current/en)
