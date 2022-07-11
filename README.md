# Docker

## Container

Isolamento de recursos dentro de um S.O sem uma camada de hypervisor

### Namespace e cgroup

Namespace: Serve para isolar alguns recursos especificos, como: usuarios, pid, rede, pontos de montagem e etc.

cgroup: Tambem serve para isolamento porem mais especifico para cpu e memoria

## Principais comandos

Executar imagem de um container

```
docker run
```

## Flags:

- -d: Nao segura o terminal (container em "background")
