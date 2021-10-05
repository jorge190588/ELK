# Aplication monitoring
## Install ELK

This steps is for install ELK Stack in a server with an operative sistema Ubuntu

First step: create ELK folder
```sh
mkdir ELK
cd ELK
```
Second step: copy the docker-compose file in ELK folder 

Third Steps: Create the necessary folders to store Elasticsearch and Logstash Data inside of ELK folder

```sh
cd ELK
mkdir elasticsearch
mkdir elasticsearch/data
mkdir logstage
mkdir logstage/pipeline
```

Four step: install JDK
```sh
sudo apt-get install openjdk-11jre-headless
```

Five step: run the docker-compose file

```sh
docker-compose up -d
```
## Install filebeat
