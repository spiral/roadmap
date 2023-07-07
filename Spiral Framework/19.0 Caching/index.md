# Caching

Caching is a technique that can significantly improve the performance of an application by storing frequently accessed data in a faster storage medium, such as memory. This reduces the need to recalculate or fetch the data from a slower source, such as a database. By implementing a caching layer, the application can quickly retrieve the data from the cache instead of recalculating it or fetching it from the slower source, which can improve the overall response time and reduce the load on the slower source.

The Spiral Framework's `spiral/cache` component allows for efficient storage and retrieval of data. It is compliant with the PSR-16 standard. In Spiral, RoadRunner is used as the underlying technology for the cache data layer, which provides several benefits. RoadRunner is written in Go, a language known for its performance and efficiency, and is designed to handle high-performance and concurrent workloads. Additionally, the RoadRunner Key-Value plugin provides a wide range of storage options, including popular solutions such as Redis Server or Memcached, as well as options that do not require a separate server, such as BoltDB. By using RoadRunner, the framework can take advantage of its performance and efficiency to handle caching more efficiently, which can ultimately improve the overall performance of the application.

### Links and materials to read more:
1. [Caching Documentation](https://spiral.dev/docs/basics-cache/current/en)
