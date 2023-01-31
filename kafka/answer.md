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

- Issue Kafka Connect Standalone Script
- used command : ` connect-standalone.sh $KAFKA_HOME/config/connect-standalone.properties /kafka/confFiles/connect-file-source.properties`

![img_10.png](img_10.png)

- Creating consumer 
![img_11.png](img_11.png)
- Verifying the events are coming to consumer 
![img_13.png](img_13.png)
- listing topics
![img_12.png](img_12.png)

---
## #4 : USING KAFKA CONNECT TO WRITE TO A DESTINATION FILE TASK

## #5 : KAFKA ADMINISTRATION TASK
- Listing Kafka consumer groups
![img_14.png](img_14.png)
- Check kafka consumer offsets
![img_15.png](img_15.png)
- Add apk url 
![img_16.png](img_16.png)
- Current running connectors 
![img_17.png](img_17.png)
- Active tasks
![img_18.png](img_18.png)
- Status 
![img_19.png](img_19.png)
- Configuration
![img_20.png](img_20.png)
- Trying to change the offset 
![img_21.png](img_21.png)
As we see, we can't change it when it is active
- After deactivating it
![img_22.png](img_22.png)
- Check target destination file
![img_23.png](img_23.png)

## #6 USING KAFKA TO READ FROM DATABASE
- Installing MySQL Docker Container
![img_24.png](img_24.png)
![img_25.png](img_25.png)
- Connecting sql 
![img_26.png](img_26.png)
- Running first query
![img_27.png](img_27.png)
- Verify tables and row creation
![img_28.png](img_28.png)
- Creating `connect-jdbc-source.properties` file with appropriate values
![img_30.png](img_30.png)
- Text version of the content: 
``` 
#--------------------------------------------------
#Content of connect-jdbc-source.properties
#--------------------------------------------------

#Name of the connector
name=Kafka-jdbc-source-task-1

#Connector class to be used.
connector.class=io.confluent.connect.jdbc.JdbcSourceConnector

#JDBC connector URL for mysql. make sure the mysql driver is in classpath.
connection.url=jdbc:mysql://172.18.0.1:3306/srcdb?user=root&password=root&allowPublicKeyRetrieval=true

#List of tables to publish. you can also use blacklists
table.whitelist=src_events

#No. of parallel tasks - Ideally one per table
tasks.max=1

#How frequently to poll from the database for new records
poll.interval.ms=2000

#mode - incrementing or timestamp+incrementing
mode=incrementing
incrementing.column.name=event_id

#Topic name to be created - This will create a topic with the prefix you specify, with
the table name appended
topic.prefix=src_events_
```
- Issuing standalone mode 
![img_31.png](img_31.png)
- Inserting a few records and verifying them from consumer side
![img_32.png](img_32.png)
![img_33.png](img_33.png)
- Dropping the topic
![img_34.png](img_34.png)

## 7 Using KAFDROP
- Kafdroop docker installation 
![img_35.png](img_35.png)

- Verify it is up 
![img_36.png](img_36.png)
- Web GUI
![img_37.png](img_37.png)