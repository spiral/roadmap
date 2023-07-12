# gRPC

Using REST APIs for communication between microservices has been a common approach for many years. However, REST APIs have some limitations and challenges that can impact the performance, scalability, and reliability of your system. Switching from REST APIs to gRPC can help address these problems. The gRPC protocol provides an extremely efficient way of cross-service communication for distributed applications. The public toolkit includes instruments to generate client and server code-bases for many languages allowing developers to use the most optimal language for their task.

To use gRPC in your Spiral application, you need to install the `spiral/roadrunner-bridge` package and add the `Spiral\RoadRunnerBridge\Bootloader\GRPCBootloader` to the list of bootloaders in your application.

```
// Installation
protected const LOAD = [
    // ...
    \Spiral\RoadRunnerBridge\Bootloader\GRPCBootloader::class,
    \Spiral\RoadRunnerBridge\Bootloader\CommandBootloader::class,
    // ...
];
```

After installation, you need to configure the communication between RoadRunner and gRPC by modifying the `.rr.yaml` file and creating a `grpc.php` file in the `app/config` directory. In this file, you can specify services that will handle incoming events from the gRPC server.

```
# Configuration for RoadRunner and gRPC communication
server:
  command: "php app.php"

grpc:
  # GRPC address to listen
  listen: "tcp://0.0.0.0:9001"
  proto:
    - "proto/calculator.proto"
```

```
// Spiral application configuration for gRPC
return [
    /**
     * The path where generated DTO (Data Transfer Object) files will be stored.
     */
    'generatedPath' => directory('root') . '/GRPC',

    /**
     * The root dir for all proto files, where imports will be searched.
     */
    'servicesBasePath' => directory('root') . '/proto',

    /**
     * The path to the protoc-gen-php-grpc library.
     */
    'binaryPath' => directory('root').'/bin/protoc-gen-php-grpc',

    /**
     * An array of paths to proto files that should be compiled into PHP by the grpc:generate console command.
     */
    'services' => [
        //directory('root').'proto/calculator.proto',
    ],
];
```

### Links and materials to read more:
1. [gRPC in Spiral Framework](https://spiral.dev/docs/grpc-configuration/current/en)
