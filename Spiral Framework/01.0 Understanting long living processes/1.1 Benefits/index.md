# Benefits

Long living processes provide a lot of benefits, such as:

1. **Performance Improvement**: Traditional PHP applications boot up and shut down for each HTTP request. With long-living processes, the application only needs to boot once, significantly improving the performance by reducing the overhead associated with booting up and shutting down. 
2. **Memory Efficiency**: Because processes are reused instead of being recreated for each request, memory usage can be more efficient, especially for applications with a large codebase or those that rely on significant amounts of data.
3. **Persistence**: Long-living processes allow for the persistence of certain elements (like database connections or cached data) across multiple requests, potentially leading to further improvements in speed and efficiency.
4. **Concurrency**: RoadRunner, for example, allows you to run PHP applications in a concurrent manner. This means you can handle multiple requests simultaneously without waiting for the previous one to finish, leading to better utilization of system resources and improved throughput. 
5. **Better Integration with Other Services**: Long-living processes can be more easily integrated with services like message queues, websockets, etc., which require persistent connections. 
6. **Cost Efficiency**: With less CPU and memory usage, the cost of hosting and server maintenance can be reduced.
