
[Apache Mesos](http://mesos.apache.org/) manages and schedules resource allocation in a datacenter, as if they came from a single pool, and provides an API messaging framework to allow task execution and monitoring. 

## Building

(_Grab a coffee, this will take some time..._)
```bash
docker build -t mesos-base ./mesos-base/
```

## Running

```bash
docker-compose up -d
```

Visit the Mesos web page:
* [localhost:5050/](http://localhost:5050/)

![capture](https://user-images.githubusercontent.com/4110571/29088152-e2a8f5d6-7c3d-11e7-8df7-fd8344a083b9.PNG)

Test framework:
```bash
$ docker exec -it mesos-agent1 ./src/examples/python/test-framework 127.0.0.1:5050
```

## Links

* [Apache Mesos - Getting Started](http://mesos.apache.org/documentation/latest/getting-started/)
* [Docker Hub - mesosphere/mesos](https://hub.docker.com/r/mesosphere/mesos/)
* [mesosphere/docker-containers](https://github.com/mesosphere/docker-containers/tree/master/mesos)
* [ZooKeeper Getting Started Guide](http://zookeeper.apache.org/doc/trunk/zookeeperStarted.html)

