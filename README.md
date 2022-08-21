# opentelemetry-typescript-microservice
The opentelemetry demo on typescript-based microservice: **sync** and **async** communication included.

## Context
- We need a industry-standard tool to increase the **observability** of our backend services while keep the trace **data portable** for analysis.

### Targets
- **http-based synchronous** call could be traced properly - achieve this by [@opentelemetry/auto-instrumentations-node](https://github.com/open-telemetry/opentelemetry-js-contrib/tree/main/plugins/node)
- **event-based asynchronous** signals could be traced well - achieve this by [Span Link](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/overview.md#links-between-spans).

## Architecture
<p align="center"><img style="display: block; width: 600px; margin: 0 auto;" src=img/2022-08-21-18-12-05.png alt="no image found"></p>

## Step Guidance

### Start the Jaeger Service
```sh
docker-compose up -d
```
### Graphql Service
```sh
git clone git@github.com:GeekEast/opentelemetry-graphql-server.git

cd opentelemetry-graphql-server
yarn && yarn dev
```

### Restful Service

```sh
git clone git@github.com:GeekEast/opentelemetry-restful-server.git

cd opentelemetry-restful-server
yarn && yarn dev
```

### Lambda Event Consumer
```sh
git clone git@github.com/GeekEast/opentelemetry-lambda-consumer.git

cd opentelemetry-lambda-consumer
yarn && yarn stack up && yarn dev
```

## Generate Traces

- go to http://localhost:9901/api/graphql/v1 to send a graphql request, for example
```graphql
query Query {
  ORGExistUser(filter: "anything")
}
```
- then you should view the traces at http://localhost:16686

## Reference
- [opentelemetry.io](https://opentelemetry.io/)