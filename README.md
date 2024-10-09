# Installation Guide

## Candidate: Alexander Esteban Joffre Aguirre

## 1. Run Dependencies with docker
Execute the following command:
```bash
docker-compose up
```

## 2. Set up kafka topics

Run the following commands to create the 3 required kafka services to ensure the correct application behavior:

- `trx-created`
```bash
docker exec -it kafka /opt/kafka/bin/kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic trx-created
```

- `trx-approved`
```bash
docker exec -it kafka /opt/kafka/bin/kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic trx-approved
```

- `trx-rejected`
```bash
docker exec -it kafka /opt/kafka/bin/kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic trx-rejected
```