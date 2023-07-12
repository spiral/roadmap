# Test Bootloaders

In some cases, you might want to replace the list of application bootloaders in your tests. This can be done by creating a child of the `App` class with the desired value.

```
class TestApplication extends App
{
    const LOAD = []; //Bootloads nothing, manual initialization is required
}
```

### Links and materials to read more:
1. [Testing Application](https://spiral.dev/docs/application-testing/current/en)
