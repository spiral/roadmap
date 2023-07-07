## Why to use cache

Caching is a technique used to store frequently accessed data in a faster storage medium, such as memory, instead of a slower source like a database. This can significantly improve the performance of an application by reducing the need to recalculate or fetch the data from the slower source every time it is needed.

By implementing a caching layer, the application can quickly retrieve the data from the cache instead of recalculating it or fetching it from the slower source. This can improve the overall response time of the application and reduce the load on the slower source.

In Spiral, RoadRunner is used as the underlying technology for the cache data layer, which provides several benefits. RoadRunner is written in Go, a language known for its performance and efficiency, and is designed to handle high-performance and concurrent workloads.

### Links and materials to read more:
1. [Caching Documentation](https://spiral.dev/docs/basics-cache/current/en)
