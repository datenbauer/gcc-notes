# Docker

### restart a stopped container
```
// without output
docker start container_name
// with output
docker start -ai container_name
```
### restart a running container
```
docker restart container_name
```

## stop all containers and delete them
```
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
```