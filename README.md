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

- Logs

```
docker logs -f <container id>    // live log
```

## Flags:

- -d: Background container (do not lock my terminal)
- -p: Bind a port of a container to a port of host
