# Deploy High Availability RabbitMQ Cluster on Docker Swarm Cluster

1. Service deploy on docker swarm cluster.
2. Using haproxy to do load balance.
3. Using consul to find and create rabbitmq cluster service.

## How to change demo setting to yours?

1. change docker `registry url` to yours in `docker-compose.yml`.
2. change `rmq settings` to yours in `docker-compose.yml`.
3. change `network setting` to yours in all `yml files`.
3. change `node settings`, `rmq settings`, `docker node label settings` to yours in `Makefile` and `docker-compose.yml`.

## How to build docker image

```
$ make build
```

## How to start demo

```
$ make run
```

Chinese Tutorial
----
[42KIM-架設高可用性RabbitMQ叢集](https://42kim.com/2019/10/17/1015/)