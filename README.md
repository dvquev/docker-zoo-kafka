# Docker Zookeeper+Kafka

Docker build to deploy Zookeeper and Kafka in containers.

To deploy the Kafka Broker on Docker container clone the project in your folder then build the image:

* Build docker image
```
docker build -t docker-zoo-kafka .
```
* Run container

```
docker run -p 2181:2181 -p 9092:9092 -e ADVERTISED_HOST=127.0.0.1  -e NUM_PARTITIONS=1 docker-zoo-kafka:latest
```

Environment Parameters
-	ADVERTISED_HOST sets Kafka Broker config advertised.listeners to PLAINTEXT://[ADVERTISED_HOST]
-	NUM_PARTITIONS sets Kafka Broker config num.partitions to [NUM_PARTITIONS]

Test If the Kafka Node is working properly:
Connect to the docker instance: 

```
docker exec -it CONTAINER-ID bash
```

All Kafka executable scripts are stored in:
**/opt/kafka_2.12-2.3.0/bin/**

```
bash# cd /opt/kafka_2.12-2.3.0/bin/
```

* Run consumer

```
bash# ./kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test
```

* Run producer

```
bash# ./kafka-console-producer.sh --broker-list localhost:9092 --topic test
```

For Kafka documentation & more: <https://kafka.apache.org/quickstart>


## Credits

	
(Based on Kafka Docker: <https://hub.docker.com/r/johnnypark/kafka-zookeeper>)
