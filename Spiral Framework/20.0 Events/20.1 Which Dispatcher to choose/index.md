### Which dispatcher to choose

When choosing an event dispatcher, it's important to consider the needs of your application. Spiral Framework provides a default event dispatcher that you can use, but you can also create your own if you need more control over the dispatching process. The default dispatcher calls listeners synchronously in the order they are returned from a ListenerProvider. It returns the same Event object it was passed after it is done invoking listeners and does not return to the Emitter until all listeners have executed.

### Links and materials to read more:
1. [Spiral Framework Events Documentation](https://spiral.dev/docs/advanced-events/3.7/en)
