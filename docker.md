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
### Umgebungsvariablen setzen
```
docker run -e EVAR1=val -e EVAR2=val ... <image>
```
Achtung! Jede einzelne Umgebungsvariable muss mit `-e` eingeleitet werden.

## Netzwerk

### Netzwerk erstellen
```
docker create network <name>
```
### Container in Netzwerk starten
```
docker run --network=<name> <image>
```
Hinweis: Docker übernimmt die Adressauflösung innerhalb eines Docker-Netzwerks. Das heißt,
man kann andere Container sowohl über ihre IP-Adresse als auch über ihren Namen (`--name`)
ansprechen.
### Nachsehen, welche Container in einem Netzwerk eingebunden sind
```
docker inspect network <network-name>
```
### IP-Adressen von Containern herausfinden
```
docker inspect network <network-name>
```
Oder im interaktiven Terminal (`-it`):
```
cat /etc/hosts        (letzte Zeile)
```
### Gemeinsames Netzwerk mit --link
Achtung! Die Docker-Dokumentation rät von dieser Option ab und sagt voraus, dass sie vielleicht
in Zukunft abgeschafft wird! Es wird stattdessen geraten, networks zu verwenden.
```
docker run --name <this-container> --link <other-container> <image>
```
Vorteil: Mit dieser Option ist es möglich, Aliasse in einem Netzwerk zu definieren:
```
docker run --name <this-container> --link <other-container>:<alias> <image>
```
Der Name von `other-container` taucht (zusammen mit dem Alias) in `/etc/hosts` von `this-container` auf.
`this-container` kann den anderen Host also über dessen IP-Adresse, den Namen `other-container` sowie über den Alias
erreichen.
