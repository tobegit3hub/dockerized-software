# Cinder Docker

## Introduction

This repo is the docker image of [cinder](https://github.com/openstack/cinder).

## Usage

```
docker run -d -e RABBITMQ_NODENAME=my-rabbit -p 5672:5672 -p 15672:15672 rabbitmq:3-management
```

```
docker run -d -p 5000:5000 -p 35357:35357 tobegit3hub/keystone_docker
```

```
docker run -d -p 8776:8776 tobegit3hub/cinder_docker
```

## Cinder client

Create test user.

```
docker run -i -t --net=host tobegit3hub/keystone_docker bash
source openrc
keystone user-create --name=admin --pass=ADMIN_PASS --email=admin@example.com
```

Use cinder command-lient.

```
docker run -i -t --net=host tobegit3hub/cinder_docker bash
source openrc
cinder list
```
