<img src="https://user-images.githubusercontent.com/37063580/152669957-472c2ade-1b45-4b0a-9160-b79439466eb7.png" width="120"/>

# ELK Stack

ELK 스택을 이용한 웹 어플리케이션 모니터링 시스템

- **Elasticsearch**: 검색 엔진 및 NoSQL 데이터베이스
- **Logstash**: 로그 데이터 파이프라인
- **Kibana**: 데이터 시각화 인터페이스


# 1. Architecture

<img src="https://user-images.githubusercontent.com/37063580/152670118-3dd3b27d-e9ca-4a01-9988-c1567bab6a85.png"/>

## 1.1 [Web Application Server](http://kakao.miintto.com)
  - AWS Lightsail 로 운영
    - Amazon Linux AMI 2 (1GB RAM / 1 vCPU / 40GB SSD)
  - Django 프레임워크 사용
  - Filebeat 사용하여 Logstash로 로그 데이터 전송

## 1.2 RDB
  - PostgreSQL 12.7 (1GB RAM / 1 vCPU / 40GB SSD)

## 1.3 ELK Cluster
  - AWS Lightsail 로 운영
    - Amazon Linux AMI 2 (4GB RAM / 2 vCPU / 80GB SSD)
  - Docker-Compose 로 ELK 스택을 한 인스턴스에 구성
    - 각 컨테이너마다 메모리 1GB씩 할당


# 2. Structure

~~~bash
$> git clone https://github.com/miintto/elk-stack.git
$> cd elk-stack
$> tree
.
├── docker-compose.yml  # Service 정의
├── elasticsearch       # Elastirsearch
│   ├── Dockerfile
│   └── config
│       └── elasticsearch.yml
├── kibana              # Kibana
│   ├── Dockerfile
│   └── config
│       └── kibana.yml
└── logstash            # Logstash
    ├── Dockerfile
    ├── config
    │   └── logstash.yml
    └── pipeline
        └── logstash.conf
~~~


# 3. Quick Start

## 3.1 Requirement
  - Docker: 20.10.7
  - Docker-Compose: 2.2.3

## 3.1 Set Env
~~~bash
$> cp .env.example .env
$> vim .env

ELK_VERSION=7.16.3

ELASTIC_USERNAME=elastic
ELASTIC_PASSWORD=....
~~~

## 3.2 Check config files
~~~bash
$> docker-compose config
~~~

## 3.3 Run
~~~bash
$> docker-compose up -d
~~~

## 3.4 Check running processes
~~~bash
$> docker ps
~~~
