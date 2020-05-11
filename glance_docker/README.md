# Glance Docker Image

## Usage

```
docker run -d -p 9292:9292 tobegit3hub/glance_docker
```

## Glance client

```
docker run -i -t --net=host tobegit3hub/glance_docker bash
```

```
source openrc

glance image-list
```

