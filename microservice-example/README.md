# Workshop with Distributed tracing
* .Net 6
* [OpenTelemetry](https://opentelemetry.io/)
* [Zipkin](https://zipkin.io/)

## List of projects/services
1. WebApi => An ASP.NET Core Web API 
2. WorketService => A background Worker Service


## Step 1 :: Run services
```
$cd WebApi
$dotnet run --project WebApi

$cd WorkerService
$dotnet run --project WorkerService
```

## Step 2 :: Run with docker compose

```
$docker-compose build
$docker-compose up -d

$docker-compose ps
NAME                                   COMMAND                  SERVICE             STATUS              PORTS
microservice-example-rabbitmq-1        "docker-entrypoint.s…"   rabbitmq            running             4369/tcp, 5671/tcp, 0.0.0.0:5672->5672/tcp, 15671/tcp, 15691-15692/tcp, 25672/tcp, 0.0.0.0:15672->15672/tcp
microservice-example-webapi-1          "dotnet WebApi.dll"      webapi              running             0.0.0.0:5000->5000/tcp
microservice-example-workerservice-1   "dotnet WorkerServic…"   workerservice       restarting
microservice-example-zipkin-1          "start-zipkin"           zipkin              running (healthy)   9410/tcp, 0.0.0.0:9411->9411/tcp

$docker-compose logs --follow
```

## Step 3 :: Testing in workshop
* Call API => http://localhost:5000/SendMessage)
* Check rabbitmq in url http://localhost:15672
  * user = guest
  * password = guest
* Check tracing in Zipkin => http://localhost:9411/zipkin

