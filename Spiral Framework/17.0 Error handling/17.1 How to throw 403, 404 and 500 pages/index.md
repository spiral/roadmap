## How to throw and handle 403, 404 and 500 pages

In Spiral Framework, you can throw HTTP level error pages from your controllers and middleware using specific exceptions. Here are the exceptions for 403, 404, and 500 HTTP status codes:

- 403 Forbidden: `Spiral\Http\Exception\ClientException\ForbiddenException`
- 404 Not Found: `Spiral\Http\Exception\ClientException\NotFoundException`
- 500 Internal Server Error: `Spiral\Http\Exception\ClientException\ServerErrorException`

When these exceptions are thrown, the default error handling middleware intercepts them and renders an error page. You can customize the error page renderer by implementing the `Spiral\Http\ErrorHandler\RendererInterface`.

### Links and materials to read more:
1. [Error Handling Documentation](https://spiral.dev/docs/http-errors/current/en)
