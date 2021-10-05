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

first step: pull image of filebeat 7.14.0

```sh
docker pull docker.elastic.co/beats/filebeat:7.14.0
```
second step: create filebeat folder

```sh
mkdir filebeat
cd filebeat
```

third step: copy filebeat.yml and nginx.yml to filebeat folder

fourth step: run container of preconfiguration
```sh
docker run \
docker.elastic.co/beats/filebeat:7.14.0 \
setup -E setup.kibana.host=ip_kibana:5601 \
-E output.elasticsearch.hosts=["ip_elasticsearch:9200"]
```

fifth step: copy log folders inside the container
 ```sh
 docker run -d \
  --name=filebeat \
  --user=root \
  --volume="$(pwd)/filebeat.yml:/usr/sahre/filebeat/filebeat.yml"\
  --volume="$(pwd)/nginx.yml:/usr/sahre/filebeat/modules.d/nginx.yml"\
  --volume="/var/log/nginx:/var/log/nginx" \
  docker.elastic.co/beats/filebeat:7.14.0 filebeat -e -strict.perms=false \
  -E output.elasticsearch.hosts=["ip_elasticsearch:9200"] 
 ```