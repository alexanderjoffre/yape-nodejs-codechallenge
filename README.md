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

## 3. prepare transactions microservice
### 3.1 Move into the micro service for transactions folder
```bash
cd ms-transactions
```
### 3.2 Install dependencies
```bash
npm i
```
### 3.3 Set up initial data into Mongo DB
```bash
npm run migrations
```
### 3.4 Configure environment variables
create a file in this directory called .env and copy the following code into this and save it:
```
APP_PORT=3000
APP_ID=ms-transactions

MONGODB_CONNECTION_URL=mongodb://localhost:27017/yape-anti-fraud

KAFKA_BROKER=localhost:9092
KAFKA_CLIENT_ID=ms-transactions
KAFKA_GROUP_ID=ms-transactions
```
### 3.4 Initiate service
```bash
npm run start
```
NOTE: to see the full documentation, once it was initiated, you can visite *[ms-transactions API Docs](http://localhost:3000/docs)*