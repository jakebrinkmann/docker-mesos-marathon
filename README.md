
[Apache Mesos](http://mesos.apache.org/) manages and schedules resource allocation in a datacenter, as if they came from a single pool, and provides an API messaging framework to allow task execution and monitoring. 

## Building

(_Grab a coffee, this will take some time..._)
```bash
docker build -t mesos-base ./mesos-base/
```

## Running

```bash
docker-compose up
```

Visit the Mesos web page:
* [localhost:5050/](http://localhost:5050/)

Test framework:
```bash
$ docker exec mesos-agent1 /bin/bash
# ${MESOS_HOME}/src/examples/python/test-framework mesos-master:5050
```

## Links

* [Apache Mesos - Getting Started](http://mesos.apache.org/documentation/latest/getting-started/)
* [Docker Hub - mesosphere/mesos](https://hub.docker.com/r/mesosphere/mesos/)
* [mesosphere/docker-containers](https://github.com/mesosphere/docker-containers/tree/master/mesos)
* [ZooKeeper Getting Started Guide](http://zookeeper.apache.org/doc/trunk/zookeeperStarted.html)

