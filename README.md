# Apache Mesos (distributed computing) 

[Apache Mesos](http://mesos.apache.org/) manages and schedules resource allocation in a datacenter, as if they came from a single pool, and provides an API messaging framework to allow task execution and monitoring. 

![capture](https://user-images.githubusercontent.com/4110571/29088152-e2a8f5d6-7c3d-11e7-8df7-fd8344a083b9.PNG)

## Dependencies

Built using:

* Docker version 17.06.0-ce, build 02c1d87

## Steps

1. Start mesos-master (http://localdocker:5050/)
2. Register mesos-agent 
3. Submits a task for marathon (http://localdocker:8080/)
4. Simple Website (http://localdocker:5000/)
5. (?) Profit

```
HOST_IP=$(docker network inspect bridge | grep Gateway | awk '/:/{print $2}' | tr -d '"')
docker-compose up --build
```

### Master

```
docker-compose up
```

### Agent (Scheduler)

### Offerings (calls/events)

### Marathon (Executor)

## References

* [Apache Mesos](https://github.com/apache/mesos)
* [Python Framework against HTTP API](https://github.com/massenz/zk-mesos)
* [pymesos](https://github.com/douban/pymesos)
* [Docker Mesos Cluster](https://github.com/chadlung/mesos-compose)
* [Apache Mesos - Getting Started](http://mesos.apache.org/documentation/latest/getting-started/)
* [Docker Hub - mesosphere/mesos](https://hub.docker.com/r/mesosphere/mesos/)
* [mesosphere/docker-containers](https://github.com/mesosphere/docker-containers/tree/master/mesos)
* [ZooKeeper Getting Started Guide](http://zookeeper.apache.org/doc/trunk/zookeeperStarted.html)

