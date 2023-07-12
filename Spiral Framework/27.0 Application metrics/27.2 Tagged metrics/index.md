# Tagged Metrics

Tagged (or labeled) metrics allow you to attach additional metadata to your metrics, which can be useful for filtering, grouping, and aggregating the data. This can increase granularity, improve organization, and simplify querying.

```
// Using tagged (also known as labeled) metrics allows you to attach additional metadata to your metrics, which can be useful for filtering, grouping, and aggregating the data.

// Using the .rr.yaml file:
metrics:
  address: 127.0.0.1:2112

  collect:
    registered_users:
      type: histogram
      help: "Total registered users counter."
      labels: [ "type" ]

// In the example, the registered_users metric is declared with a label called type. When adding data to the metric, you can specify the value for the type label, such as customer, admin, etc.

use Spiral\RoadRunner\Metrics\MetricsInterface; 

class UserRegistrationHandler
{
    public function __construct(
        private readonly MetricsInterface $metrics
    ) {
    }

    public function handle(User $user): void
    {
        // Store user in database

        $this->metrics->add('registered_users', 1, ['customer']);
        
        // or
        
        $this->metrics->add('registered_users', 1, ['admin']);
    }
}
```

### Links and materials to read more:
1. [Application Metrics](https://spiral.dev/docs/advanced-prometheus-metrics/current/en)
