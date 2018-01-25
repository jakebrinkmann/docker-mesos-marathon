Load the following URLs in a browser:

    Mesos Master UI: http://localdocker:5050/
    Marathon UI: http://localdocker:8080/

To stop the cluster:

$ docker-compose stop

Deploying a test app via the Marathon API:

$ curl -X POST -H "Accept: application/json" -H "Content-Type: application/json" localdocker:8080/v2/apps -d \
'{"id": "hello-test","cpus": 0.1,"mem": 32,"cmd": "echo hello; sleep 5", "instances": 1}'

Deploying a Docker container via the Marathon API:

curl -X POST -H "Accept: application/json" -H "Content-Type: application/json" localdocker:8080/v2/apps -d ' \
{
    "id": "inky",
    "container": {
        "docker": {
            "image": "mesosphere/inky"
        },
        "type": "DOCKER",
        "volumes": []
    },
    "args": ["hello"],
    "cpus": 0.2,
    "mem": 32.0,
    "instances": 1
}'

