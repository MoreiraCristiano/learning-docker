# Docker

## Containers

Isolated resources of machine without a hypervisor

### Namespaces e cgroups

Namespace: Isolate several resources like: network, users, pid, mount, etc.

cgroup: Also used to isolate resources but most specific to CPU and RAM

## Commands

- Exec a img of a container

```
docker run <flags> <imagem>
```

- Stop a container

```
docker stop <container id>
```

- Start a container

```
docker start <container id>
```

- Remove a container

```
docker rm <container id>        // Remove the container
docker rmi
```

- List containers

```
docker container ls
docker ps

docker ps -a            // containers historic
```

- Exec something in specific container

```
docker container exec <container id>

docker container exec -it <container id> <bash/sh>    // Iterativity with container (usually bash)
```

- See images and more infos

```
docker images

docker image inspect <imagename:version>
```

- Logs

```
docker logs -f <container id>    // live log
```

## Flags:

- -d: Background container (do not lock my terminal)
- -p: Bind a port of a container to a port of host

## Create an image

### Dockerfile

Definition file of docker image

```
FROM debian             // Image to be utilized
RUN apt-get update      // Run commands on img build
WORKDIR /app            // Default dir of container when it starts
COPY /app/src /app      // Copies of host file/app to container folder
EXPOSE 80               // Exposition of port
CMD npm start           // Run commands after container is up
```

Real example of Dockerfile

```
FROM node:12-alpine
RUN apk add --no-cache python2 g++ make
WORKDIR /app
COPY ..
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
```

### Build a Dockerfile

```
docker build -t <tag name> <dockerfile dir>
```
