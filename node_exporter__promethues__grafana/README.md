# Docker Swarm with Node-Exporter, Prometheus, Grafana 

This Sample Environment:

* 3 Nodes Docker Swarm Cluster: demo1, demo2, demo3
* Docker Registry is on the demo1 Node.
* Grafana and Promethus Server are deployed on the demo1 Node.
* Grafana data will be save to ${HOME}/data/grafana.

Notes:

* If want to backup Grafana settings, just backup this ${HOME}/data/grafana folder.

How To Start This Sample
----

#### Build Images
```shell script
docker-compose -f docker-compose.yml build
```

#### Push to Registry
```shell script
docker-compose -f docker-compose.yml push
```

#### Deploy Service
```shell script
docker stack deploy -c docker-compose.yml cluster
```

#### Label Nodes
```shell script
docker node update --label-add node=one demo1
docker node update --label-add node=two demo2
docker node update --label-add node=three demo3
docker node update --label-add node-exporter=true demo1 demo2 demo3
```

Check Service
----

#### Check Services Status
```shell script
docker service ls
```

```shell script
ID                  NAME                    MODE                REPLICAS            IMAGE                              PORTS
iguqnfidllq4        cluster_grafana         global              1/1                 grafana/grafana:7.1.3              *:3000->3000/tcp
0szb61tg0efn        cluster_node-exporter   global              3/3                 prom/node-exporter:v1.0.1
ddz1mdss9ki3        cluster_prometheus      global              1/1                 demo1:5000/rmq-prometheus:latest   *:9090->9090/tcp
```

#### Check each Service Startup Message
```shell script
docker service ps --no-trunc {service_name}
```
ex. 
```shell script
docker service ps --no-trunc cluster_grafana
```

Service Web UI
----

#### Promethus Server

http://your-ip:9090

#### Grafana

http://your-ip:3000