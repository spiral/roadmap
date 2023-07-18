## Memory Leaks

In the context of long-living processes, memory management becomes a crucial aspect. Since the application stays in memory for a long time, even a small memory leak might lead to process restart. RoadRunner, the application server used by Spiral, will monitor memory consumption and perform a soft reset, but it is best to avoid memory leaks in your application source code.

Memory leaks can occur when memory resources are allocated but not released after they are no longer needed. In the context of PHP, this can happen when large amounts of data are processed, or when resources like file handles or database connections are not properly closed.

Spiral Framework and all of its components are written with memory management in mind, but you still have to make sure that your domain code is not leaking. This includes being careful with global state, static properties, and closures, as they can inadvertently hold onto references to objects, preventing them from being garbage collected.

### Links and materials to read more:
1. [Memory Leaks in Spiral Framework](https://spiral.dev/docs/start-workers/3.4/en)
