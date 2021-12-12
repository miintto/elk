# Elastic Stack

- Elasticsearch
- Kibana
- Logstash

# 1. Quick Start
## 1.1 Set Env
~~~bash
$> cp .env.example .env
$> vim .env

ELK_VERSION=7.15.2

ELASTIC_USERNAME=elastic
ELASTIC_PASSWORD=....
~~~

## 1.2 Check config files
~~~bash
$> docker-compose config
~~~

## 1.3 Run
~~~bash
$> docker-compose up -d
~~~

## 1.4 Check running processes
~~~bash
$> docker ps
~~~
