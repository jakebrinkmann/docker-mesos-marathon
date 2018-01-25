```
docker build -t pymoose .
```

```
$ curl -X POST -H "Accept: application/json" -H "Content-Type: application/json" localdocker:8080/v2/apps -d ' \
{
    "id": "mypythonapp",
    "container": {
        "docker": {
            "image": "mypythonapp"
        },
        "type": "DOCKER",
        "volumes": []
    },
    "cpus": 0.2,
    "mem": 32.0,
    "instances": 1
}'
```
