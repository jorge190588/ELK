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

Fourth step: run the docker-compose file

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

third step: copy docker-filebeat.yml, filebeat.yml and nginx.yml to filebeat folder

fourth step: modify the file filebeat.yml 
look for this configuration and indicate the IP of the monitoring server
  ```sh
  setup.kibana:
  host: "ip_kibana:5601"

  output.elasticsearch:
  hosts: ["ip_elasticsearch:9200"]
```


fifth step: run the docker-compose file of filebeat in monitoring server
 ```sh
docker-compose -f docker-filebeat.yml up -d
 ```