## Setting Up Environments and Preinstallations
![img.png](img.png)

## #1 : Creating Kafka Topic Task

- View the kafka related scripts in Bin directory
used command : `ls /opt/kafka_2.12-2.4.0/bin/`

![img_1.png](img_1.png)

- Kafka_home environment : `/opt/kafka_2.12-2.4.0` by using `echo $KAFKA_HOME
` command

- There is not any topic yet  
![img_2.png](img_2.png)
- Create and verify a new Kafka topic named “kafka-tst-01”, which has one partition and runs on one node
![img_3.png](img_3.png)
---

## #2 : Writing and Reading Kafka Topic Task

- Creating 2 sessions - producer and consumer and checking it
- `$KAFKA_HOME/bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic kafka-tst-01 --from-beginning`
- `$KAFKA_HOME/bin/kafka-console-producer.sh --broker-list localhost:9092 --topic kafka-tst-01`
![img_4.png](img_4.png)

- Creating another 2 sessions - a producer and a consumer, 4 in total, and check them. As you see all consumers are receiving the messages/events

![img_5.png](img_5.png)

- Create another session to read all events since beginning
- used command : `$KAFKA_HOME/bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic kafka-tst-01 --from-beginning`
![img_6.png](img_6.png)
- Kafka topic deletion and verifying it
![img_7.png](img_7.png)

---

## #3 : USING KAFKA CONNECT TO WRITE TO A DESTINATION FILE TASK

- Verifying the directories creation
![img_8.png](img_8.png)
- Verify the content of source file after insert data 
![img_9.png](img_9.png)
- 