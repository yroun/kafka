# Kafka, Apache

### install

```
yum install -y java-1.8.0-openjdk-devel.x86_64
wget https://downloads.apache.org/kafka/3.4.0/kafka_2.13-3.4.0.tgz
```

### cmd

```
kafka-topics.sh --list --bootstrap-server localhost:9092
kafka-topics.sh --create --topic topic --partition 3 --replication-factor 2 --bootstrap-server localhost:9092
kafka-topics.sh --describe --topic topic --bootstrap-server localhost:9092
kafka-topics.sh --alter --topic topic --partition 3 --bootstrap-server localhost:9092
kafka-topics.sh --delete --topic topic --bootstrap-server localhost:9092
kafka-configs.sh --alter --entity-type topics --entity-name topic --add-config retention.ms=86400000 --bootstrap-server localhost:9092
```

### producer

```
kafka-console-producer.sh --topic topic --bootstrap-server localhost:9092
kafka-console-producer.sh --topic topic --request-required-acks 1 --bootstrap-server localhost:9092
kafka-console-producer.sh --topic topic --message-send-max-retries 50 --bootstrap-server localhost:9092
kafka-verifiable-producer.sh --topic topic --max-messages 100
```

### consumer

```
kafka-console-consumer.sh --topic topic --from-beginning --bootstrap-server localhost:9092
kafka-console-consumer.sh --topic topic --group group --from-beginning --bootstrap-server localhost:9092
kafka-console-consumer.sh --topic topic --group group --property print.key=true --property key.separator="-" --from-beginning --bootstrap-server localhost:9092

kafka-consumer-groups.sh --list --bootstrap-server localhost:9092
kafka-consumer-groups.sh --describe --group group --bootstrap-server localhost:9092

```

### config/server.properties

```
broker.id=N
listeners=PLAINTEXT://localhost:PORT_N
log.dirs=/path/to/kafka-logs-N
```

## file sync

### config/connect-standalone.properties

```
key.converter.schemas.enable=false
value.converter.schemas.enable=false
```

### run file sync

```
connect-standalone.sh config/connect-standalone.properties config/connect-file-sink.properties
```


