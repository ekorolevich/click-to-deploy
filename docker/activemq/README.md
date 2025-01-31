ActiveMQ-docker
============
Dockerfile source for ActiveMQ [docker](https://docker.io) image..

## Upstream
This source repo was originally copied from:


## Disclaimer
This is not an official Google product.

## About
This image contains an installation of ActiveMQ

For more information, see the
[Official Image Marketplace Page](https://console.cloud.google.com/marketplace/product/bitnami-launchpad/activemq).

### Prerequisites

Configure [gcloud](https://cloud.google.com/sdk/gcloud/) as a Docker credential helper:

```shell
gcloud auth configure-docker
```
### Pull command

```shell
docker -- pull marketplace.gcr.io/google/activemq5
```
## Table of Contents

 [Using Docker](#using-docker)
  * [Run a  server](#run-a-activemq-server-docker)
    * [Start a activemq instance](#start-a-activemq-instance-docker)
    * [Use a persistent data volume](#use-a-persistent-data-volume-docker)
  * [Configurations](#configurations-docker)
    * [Using flags](#using-flags-docker)
    * [Authentication and authorization](#authentication-and-authorization-docker)
  * [Mongo CLI](#mongo-cli-docker)
    * [Connect to a running activemq container](#connect-to-a-running-activemq-container-docker)
    * [Connect to a remote activemq server](#connect-to-a-remote--server-docker)
* [References](#references)
  * [Ports](#references-ports)
  * [Volumes](#references-volumes)

# Using Docker

Consult [Launcher container documentation](https://cloud.google.com/launcher/docs/launcher-container)
for additional information about setting up your Docker environment.

Use the following content for the `docker-compose.yml` file, then run `docker-compose up`.

```yaml
version: '2'
services:
  activemq:
    container_name: some-activemq
    image: marketplace.gcr.io/google/activemq5
    ports:
      - '5672:5672'
      - '61613:61613' 
      - '1883:1883'
      - '61614:61614'
      - '8161:8161'
  ```




# Quick Start for ActiveMQ

You can launch the image using the `docker` command line:

## Create and set ownership of `data/` directory to `activemq` user.
```shell
mkdir data/
chown 1000:1000 data/
```

## Run `docker run` command.
```shell
docker run -e ACTIVEMQ_ADMIN_PASSWORD="setyourdesiredpassword" \
    --name='activemq' -it --rm \
    -p 5672:5672 \
    -p 61613:61613 \
    -p 1883:1883 \
    -p 61614:61614 \
    -p 8161:8161 \
    -v $PWD/data/:/opt/activemq/data \
    marketplace.gcr.io/google/activemq5
```

For more information about ActiveMQ, visit [official documentation](https://activemq.apache.org/).

