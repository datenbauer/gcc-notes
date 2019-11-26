# Docker

## Grundlagen

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
### stop all containers and delete them
```
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
```
### Alle gestoppten Container (erzwungenermaßen) entfernen 
```
docker container [-f] prune
```
### Container automatisch nach dem Stoppen entfernen
```
docker run --rm <image>
```
### Interaktives Terminal starten
```
docker run -it <image>
```

## Netzwerk

### Netzwerk erstellen
```
docker create network <name>
```
### Container in Netzwerk starten
```
docker run --network=<name> <image>
```
### Nachsehen, welche Container in einem Netzwerk eingebunden sind
```
docker inspect network <network-name>
```
