# standalone-hbase

The container [standalone-hbase](https://registry.hub.docker.com/u/tobegit3hub/standalone-hbase/) is based on Ubuntu 14.04, Oracle Java 7 and HBase trunk(currently 0.99).

## Usage

1. Build the image or not, `docker build -t tobegit3hub/standalone-hbase .`
2. `docker run -d --name standalone-hbase -p 2181:2181 -p 16000:16000 -p 16010:16010 -p 16020:16020 -p 16030:16030 tobegit3hub/standalone-hbase`
3. Go to <127.0.0.1:16010> or `docker logs standalone-hbase`

## Not ready

The port of RegionServer is allocated randomly so you may not access <127.0.0.1:16010>.