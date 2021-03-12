# Running a Local Kafka Broker

To run a single instance of Kafka broker on your local machine. Please follow the belong steps.

This guide will assume Kafka version `2.5.1`

## 1. Pull the repo

```
git clone ssh://git@github.com/JSchillinger/kafka-docker.git
```

## 2. Modify docker-compose.yml

Modify docker-compose.yml and change the value of `KAFKA_ADVERTISED_HOST_NAME` to your local IP address. For example if you local machine IP address is `10.11.0.100`

```
KAFKA_ADVERTISED_HOST_NAME: 10.11.0.100
```

## 3. Boot Docker up with  docker-compose

Run/Boot container up via docker-compose

```
docker-compose up
```

Once this is booted up you should have access to the following
- Kafka Broker - localhost:9092
- Kafdrop Monitoring - http://localhost:9000

## 4. Usage of the Kafka broker

In the application that needs to connect to Kafka, to redirect it to use the local instance, add the following as environment variable

```
-Dkafka.bootstrap.server=localhost:9092
-Dkafka.replication.factor=1
-Dkafka.isr.config.value=1
```
