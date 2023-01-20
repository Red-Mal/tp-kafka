# tp-kafka
1. 
- Télécharger Kafka
- Démarrer Zookeeper
- Démarrer Kafka-server
- Tester avec Kefka-console-producer et kafka-console-consumer
2. Avec Docker 
 - Créer le fichier docker-compose.yml
 - Démarrer les conteneurs docker : zookeeper et kafka-broker
 - Tester avec Kafka-console-producer et kafka-console-consumer
3. 
En Utilisant KAFKA et Stpring Cloud Streams, Créer :
- Un Service Producer KAFKA via un Rest Controler
- Un Service Consumer KAFKA
- Un Service Supplier KAFKA
- Un Service de Data Analytics Real Time Stream Processing avec Kaflka Streams
- Une application Web qui permet d'afficher les résultats du Stream Data Analytics en temps réel



- Télécharger Kafka
- Démarrer Zookeeper

```
start bin\windows\zookeeper-server-start.bat config/zookeeper.properties
```
<img width="677" alt="zookeeper-server-start" src="https://user-images.githubusercontent.com/57734887/212695066-b987fdef-db02-4fad-a6e3-1b07790e31bf.png">

- Démarrer Kafka-server

``` 
start bin\windows\kafka-server-start.bat config/server.properties
```
<img width="675" alt="kafka-server-start" src="https://user-images.githubusercontent.com/57734887/212694944-5f2ee61e-752b-40a7-8053-0a918c912658.png">

- Tester avec Kafka-console-producer et kafka-console-consumer

``` 
start bin\windows\kafka-console-consumer.bat --broker-list localhost:9092 --topic R4
```
<img width="1280" alt="kafka-producer-consumer" src="https://user-images.githubusercontent.com/57734887/212695293-36134d2c-43bb-4bb2-a76d-419690b7d341.png">

```
start bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic R4
```
<img width="640" alt="kafka-consumer-spring" src="https://user-images.githubusercontent.com/57734887/212695345-c81f3bd6-c5ef-4e38-8f26-f764f4c86a80.png">

 - Créer le fichier docker-compose.yml

```
version: '3'
services:
  zookeeper:
    image: confluentinc/cp-zookeeper:7.3.0
    container_name: zookeeper
    environment:
      ZOOKEEPER_CLIENT_PORT: 2181
      ZOOKEEPER_TICK_TIME: 2000

  broker:
    image: confluentinc/cp-kafka:7.3.0
    container_name: broker
    ports:
      # To learn about configuring Kafka for access across networks see
      # https://www.confluent.io/blog/kafka-client-cannot-connect-to-broker-on-aws-on-docker-etc/
      - "9092:9092"
    depends_on:
      - zookeeper
    environment:
      KAFKA_BROKER_ID: 1
      KAFKA_ZOOKEEPER_CONNECT: 'zookeeper:2181'
      KAFKA_LISTENER_SECURITY_PROTOCOL_MAP: PLAINTEXT:PLAINTEXT,PLAINTEXT_INTERNAL:PLAINTEXT
      KAFKA_ADVERTISED_LISTENERS: PLAINTEXT://localhost:9092,PLAINTEXT_INTERNAL://broker:29092
      KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR: 1
      KAFKA_TRANSACTION_STATE_LOG_MIN_ISR: 1
      KAFKA_TRANSACTION_STATE_LOG_REPLICATION_FACTOR: 1
```
<img width="1280" alt="docker-compose+kafka-producer" src="https://user-images.githubusercontent.com/57734887/212697996-bcfbede2-d45f-4ddc-bf0f-951b3de60d6a.png">

- Démarrer les conteneurs docker : zookeeper et kafka-broker

```
docker-compose up
```
<img width="1280" alt="docker-compose-up" src="https://user-images.githubusercontent.com/57734887/212698621-4ea78f93-2415-4b9e-b273-e5b6e2883087.png">

 - Tester avec Kafka-console-producer et kafka-console-consumer

```
docker exec --interactive --tty broker kafka-console-producer --bootstrap-server broker:9092 --topic R2
```
 
<img width="1247" alt="docker-compose-producer" src="https://user-images.githubusercontent.com/57734887/212699533-ccf144b5-ff1e-4715-aaff-2150e949ad9c.png">

```
docker exec --interactive --tty broker kafka-console-consumer --bootstrap-server broker:9092 --topic R2
```

<img width="1247" alt="docker-compose-consumer" src="https://user-images.githubusercontent.com/57734887/212699502-bc259cb4-1dc0-449e-b92a-951b00e4c3dd.png">

En Utilisant KAFKA et Stpring Cloud Streams, Créer :
- Un Service Producer KAFKA via un Rest Controler

- Un Service Consumer KAFKA
- 
- Un Service Supplier KAFKA
- 
- Un Service de Data Analytics Real Time Stream Processing avec Kaflka Streams
- Une application Web qui permet d'afficher les résultats du Stream Data Analytics en temps réel

 

