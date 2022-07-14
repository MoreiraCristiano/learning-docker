# Docker

## Containers

Isolated resources of machine without a hypervisor

### Namespaces e cgroups

Namespace: Isolate several resources like: network, users, pid, mount, etc.

cgroup: Also used to isolate resources but most specific to CPU and RAM

## Commands

- Run a container img

```
docker run <flags> <imagem>

Real uses of a command to run a container:

sudo docker run -d -p 3000:3000 -v todo-db:/etc/todos/ getting-started:2.0

More complex command:

sudo docker network create mysql-todo-db && sudo docker run -d -v mysql-todo-db:/var/lib/mysql --network todo-app -e MYSQL_ROOT_PASSWORD=secret -e MYSQL_DATABASE=todos mysql:5.7
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
docker build -t <tagname:version> <dockerfile dir>
```

## Volumes

Used to do data persistence

Create a volume

```
docker volume create <volume name>
docker volume ls
```

Del a volume

```
docker volume rm
```

## Network

By default all containers are in the same network

Create network

```
docker network create

--network todo-app --network-alias mysql        // provide an alias to your network
```

Network options

```
--dns 8.8.8.8
--hostname catota123        // name to container
--link containertolink      // link containers; deprecated
--expose 80                 // expose container port to HOST
--publish                   // bind port from container to host
--mac-address               // custom mac
--net=<host|bridge|none>    // change net
```

Network troubleshooting

```
sudo docker run -it --network <networkname> nicolaka/netshoot
```
