## Installation and Configuration

To use application metrics in Spiral, you first need to install the `spiral/roadrunner-bridge` package. Then, you can add the `Spiral\RoadRunnerBridge\Bootloader\MetricsBootloader` to the list of bootloaders. The metrics service does not require configuration in the application, but you must activate the service in `.rr.yaml`.

```php
// Installation
// At first, you need to install the spiral/roadrunner-bridge package.
// Once the package is installed, you can add the Spiral\RoadRunnerBridge\Bootloader\MetricsBootloader to the list of bootloaders:

protected const LOAD = [
    // ...
    \Spiral\RoadRunnerBridge\Bootloader\MetricsBootloader::class,
    // ...
];

// Configuration
// The metrics service does not require configuration in the application. However, you must activate the service in .rr.yaml:

rpc:
  listen: tcp://127.0.0.1:6001

## ...

metrics:
  ## prometheus client address (path /metrics added automatically)
  address: 127.0.0.1:2112
```

### Links and materials to read more:
1. [Application Metrics](https://spiral.dev/docs/advanced-prometheus-metrics/current/en)
