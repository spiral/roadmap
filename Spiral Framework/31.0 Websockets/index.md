# Websockets

Websockets are a protocol that provides full-duplex communication channels over a single TCP connection. They are designed to be implemented in web browsers and web servers, but can be used by any client or server application. Websockets are an important part of the real-time web, enabling the development of interactive web applications with real-time, two-way communication.

In the context of the Spiral Framework, websockets are implemented using the `spiral/roadrunner-bridge` package and the Centrifugo server. The Centrifugo server is a scalable real-time messaging server in language-agnostic way. It works in conjunction with the RoadRunner server to handle websocket connections and communication.

The integration of Centrifugo with Spiral provides efficient management of real-time data transmission, making it an ideal solution for applications that require real-time updates and notifications. It also provides scalability, allowing for the easy expansion of your application as it grows. Centrifugo provides a powerful and flexible toolset that can be easily customized to meet the specific needs of your application.

To use websockets in your Spiral application, you need to install the `spiral/roadrunner-bridge` package and add the `Spiral\RoadRunnerBridge\Bootloader\CentrifugoBootloader` to the list of bootloaders in your application. //code

```php
// Installation
protected const LOAD = [
    // ...
    \Spiral\RoadRunnerBridge\Bootloader\CentrifugoBootloader::class,
    // ...
];
```

After installation, you need to configure the communication between RoadRunner and Centrifugo by modifying the `.rr.yaml` file.

```php
# Configuration for RoadRunner and Centrifugo communication
rpc:
  listen: tcp://0.0.0.0:6001

server:
  command: "php app.php"
  relay: pipes

centrifuge:
  proxy_address: "tcp://0.0.0.0:10001"
  grpc_api_address: "centrifugo:10000"
```

You also need to configure the Centrifugo server by creating a `config.json` file and specifying the communication settings between Centrifugo and RoadRunner.

```php
# Configuration for RoadRunner and Centrifugo communication
rpc:
  listen: tcp://0.0.0.0:6001

server:
  command: "php app.php"
  relay: pipes

centrifuge:
  proxy_address: "tcp://0.0.0.0:10001"
  grpc_api_address: "centrifugo:10000"
```

In your Spiral application, you will need to create a `centrifugo.php` file in the `app/config` directory. In this file, you can specify services that will handle incoming events from the Centrifugo server, as well as any interceptors that should be applied to the events.

```php
// Spiral application configuration for Centrifugo
use RoadRunner\Centrifugo\Request\RequestType;

return [
    'services' => [
        RequestType::Connect->value => ConnectService::class,
        RequestType::Subscribe->value => SubscribeService::class,
        RequestType::Refresh->value => RefreshService::class,
        RequestType::Publish->value => PublishService::class,
        RequestType::RPC->value => RPCService::class,
    ],
    'interceptors' => [
        RequestType::Connect->value => [
            Interceptor\AuthInterceptor::class,
        ],
        RequestType::Subscribe->value => [
            Interceptor\AuthInterceptor::class,
        ],
        RequestType::RPC->value => [
            Interceptor\AuthInterceptor::class,
        ],
        '*' => [
            Interceptor\TelemetryInterceptor::class,
        ],
    ],
];
```

### Links and materials to read more:
1. [Websockets in Spiral Framework](https://spiral.dev/docs/websockets-configuration/current/en)
