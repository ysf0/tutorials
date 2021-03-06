############################

############################
# BROKER PLATFORMS KAFKA
############################

############################

# Apache Kafka
- Kafka is open source and developing by Apache. But Confluent company is a upstream fork of Apache Kafka which has additional features.s
- Kafka is a broker. Publishers send messages to topics, and the consumers read the messages from subscribed topics.
- Kafka stores the messages in files which named __segment file__. In this way the messages are not store only on RAM.

# Zookeeper
Kafka requires Zookeeper for the following reasons:
- store leader and follower informations
- which nodes are up/available in cluster
- list of topics
- which topics are storing in which nodes and partition lists
- Quotas - how much data is each client allowed to read and write
- ACLs - who is allowed to read and write to which topic (old high level consumer) - Which consumer groups exist, who are their members and what is the latest offset each group got from each partition.

In the "/kafka-server/bin/" directory there are command line scripts which can easily allow developer to call the APIs of Kafka server. Examples:

```sh
# first we start the kafka server
/bin/kafka-server-start.sh "config/server.properties"

/bin/kafka-topics.sh --Zookeeper "localhost:2181" --delete --topic "DEMO"

/bin/kafka-console-producer.sh --broker-list "localhost:9092" --topic "sampleTopic"

/bin/kafka-topics.sh --create --Zookeeper "localhost:2181" --replication-factor "1" --partitions "1" --topic "sampleTopic"
```

As it can be seen on above example, operations like creating or removing topics requires Zookeeper's socket information. Because this requests are not sending to Kafka, they sending directly to Zookeeper. But the commands like consuming or publishing messages are sending directly to Kafka server.

If we read the script file: (source-id: 372), we will see that it calls this class: (source-id: 373). As it can be seen inside the Scala class "org.I0Itec.zkclient.ZkClient", it sends request to Zookeeper via Zookeeper client.

Kafka client APIs are offers methods like listing the all topics (source-id: 374):

```java
KafkaConsumer<String, String> consumer = new KafkaConsumer<String, String>(props);
topics = consumer.listTopics();
```

Kafka can send requests to Zookeeper to create or delete topics. Those APIs are considered as admin operations. (source-id: 375) title: "Running from JAR", paragraph: 2 + (source-id: 376)

# Consumer and Publisher API
- producer example:

```java
Properties props = new Properties();
props.put(ProducerConfig.BOOTSTRAP_SERVERS_CONFIG, "localhost:9990,localhost:9991");//Kafka servers which are on the same cluster
props.put(ProducerConfig.CLIENT_ID_CONFIG, "client99");
props.put(ProducerConfig.KEY_SERIALIZER_CLASS_CONFIG, LongSerializer.class.getName()); // record key serializer
props.put(ProducerConfig.VALUE_SERIALIZER_CLASS_CONFIG, StringSerializer.class.getName());// record value serializer
props.put(ProducerConfig.PARTITIONER_CLASS_CONFIG, CustomPartitioner.class.getName()); // the details are below
// other props may come here...

Producer<String, String> producer = new KafkaProducer<String, String>(props);

// we create a message here
final ProducerRecord<Long, String> record = new ProducerRecord<>("my-topic", "my-key", "my-value");

// we send the message
RecordMetadata metadata = producer.send(record).get();

print("record sent to partition: " + metadata.partition() );
print("record sent to offset: " + metadata.offset() );
```

- consumer example:

Consumer'lar sadece spesific 1 partition ve topic'ten de ??ekebilir:

```java
// example using Spring Boot
@KafkaListener(topicPartitions = @TopicPartition(topic = "topicName", partitions = { "0", "1" }))
```

Yada t??m topic'teki t??m partition'lardan okuyabilir:

```java
// Example without Spring Boot (core Java).
KafkaConsumer<String, String> consumer = new KafkaConsumer<String, String>(props);

// we should subscribe to get a message form that topic
consumer.subscribe("my-topic")

ConsumerRecords<String, String> records = consumer.poll(100); // 100 is the time in milliseconds consumer will wait if no record is found at broker.

while(true){
    //we loop one by one for all messages from that topic
    for (ConsumerRecord<String, String> record : records){
            //we got the message
            print(record.offset(), record.key(), record.value());
    }
    consumer.commitAsync(); // or 'commitSync' to block the thread
}

consumer.close();
```

# CustomPartitioner
CustomPartitioner includes a method which is calling before we send a message to Kafka server. This method returns the partition number for that record (message).   

```java
import java.util.Map;
import org.Apache.Kafka.clients.producer.Partitioner;
import org.Apache.Kafka.common.Cluster;

public class CustomPartitioner implements Partitioner{

  private static final int PARTITION_COUNT=50;

  @Override
  public void configure(Map<String, ?> configs) {
  }

  @Override
  public int partition(String topic, Object key, byte[] keyBytes, Object value, byte[] valueBytes, Cluster cluster) {

    // custom (any) logic here...
    Integer keyInt=Integer.parseInt(key.toString());
    return keyInt % PARTITION_COUNT;
  }

  @Override
  public void close() {
  }
}
```

As seen above each partition ID is an integer. Therefore TopicPartition is creating using topic name and partition ID:

```java
TopicPartition(String topic, int partition) 
```

source: (source-id: 377)

# committing an offset
"Committing an offset" means that consumer client got the message. That means a spesific record is "consumed".

As default Kafka server has a topic which stores the offsets. Kafka follows the offsets from this partititon. In other words, Kafka knows which record (message) consumed via that partition. (source-id: 378) title: "Atomic multi-partition writes", paragraph: 3.

- # record (or message)
    The each message which send by client to Kafka server. Each record is key-value. Kafka guarantees the consumption order.

- # Broker
    Each kafka server (node).

- # Kafka cluster
    A group of nodes can create one cluster.

- # partition
    It is the same thing with the "partition" term that we use on other NoSQL databases. In many NoSQL databases, we distribute the data depending on the partition ID. In most NoSQL databases as default the partition ID is the hash of the data (on Kafka the "record"). In kafka we can implement CustomPartitioner class to choose the partition of each record.

    Some rules:
    - A broker may store multiple topics.
    - Each topic must store at least in one partition.
    - 1 partition must have only 1 topic.

    Partition ID and topics are both unique together. In other words, "user-created-topic" has partition ID "1", but "warnings-topic" may also have partition ID "1". Both these partitions are completly different and independed.

    Topics are logical consepts, partition are physically divided portions.

    Partitions are like queues. We can consume a record from partition using partition id and topic name. (source-id: 379) title: "KafkaConsumer", 3rd code example.

    To understant clearly we can give real examples:
    - Topic: "completed-payment-transactions", Partition: Store-ID.
    - Topic: "order-started", Partition: Store-ID.

    Each store should have is equivalent partition ID. Examples:
    - store-id: 100 ---> partition-id: 1
    - store-id: 200 ---> partition-id: 2
    - store-id: 400 ---> partition-id: 4

    The partition-ID's on Kafka start from zero. So we should find a mathematical operation to find the equivalent partition ID from store ID.

    (source-id: 379) title: "KafkaConsumer", 3rd code example is written on Python. But the same object exist also on Java. TopicPartition instance is creating using topic name and the partition ID. (source-id: 377):
    
    ```java
    TopicPartition(String topic, int partition)
    ```

    Kafka does not store which client/consumer readed which data. Therefore each client should remember it's own offset (topic-offset ve partition-ID) he read last. But kafka has another feature: It stores the last readed record (offset) for each "__consumer group__".

    But even Kafka has this feature it is recommended to implement idempotent consumer functions. If we can not implement idempotent functions, it is recommended to write the unique information from consumed messages to a cold storage. So we can verify if the new consumed message is consumed already or not. 

- # offset
    offset meaning in IT: the distance to an element within a data object.

    Each record has an offset in a specific partition. This value never changes.

- # replication factor
    her partition'un ka?? adet broker'da klonlanaca????n?? belirtebiliyoruz. mesaj??m??z?? X node'unun A partition'una g??nderelim. X node'u mesaj?? ald??????nda di??er node'lar??n ilgili partition'lar??na yollar. bu ??ekilde bir makinemiz down oldu??unda, di??er makineler mesaj?? saklamaya ve da????tmaya devam edecektir.

    her partition i??in __leader__ ve __follower (or in-sync replicas or ISR)__ broker'lar vard??r. follower'lar (ilgili partition i??in) sadece data'n??n klonlanmas??nda g??revlidirler. ayn?? zamanda leader ????kerse follower'lardan biri leader olarak devreye girmektedir. kaynak: (source-id: 381) "Replication: Kafka Partition Leaders, Followers, and ISRs." ba??l??????. + Di??er kaynak: (source-id: 382) "What is Replication?" ba??l?????? "Leader for a partition:" ile ba??layan 7inci paragraf.

    X partition'a bir mesaj at??ld??. Bu mesaj X partition'un liderine yollanmam???? olsun. O zaman bu iste??i alan node, ilgili mesaj?? o partition'un liderine forward eder. kaynak: (source-id: 383) "Kafka topic partition" ba??l?????? 5inci paragraf.

    bir topic yaratma ??rne??i:

    ```sh
    /bin/kafka-topics.sh --create --Zookeeper "localhost:2181" --replication-factor "1" --partitions "1" --topic "test"
    ```

    Bu komutta:
    
    - replication-factor parametresinde, bu topic ve ona ba??l?? partition'??n ka?? adet node(broker)'da tutulaca????n?? belirttik.
    - partitions ile bu topic'e ba??l?? ka?? farkl?? partition olmas?? gerekti??ini belirlemi?? olduk
    - Zookeeper parametresi ba??ka yerde anlat??l??yor (bu konu i??in ??nemsiz bilgi)

- # committed record
    - record is committed only if all follower's are got the record successfully. kaynak: (source-id: 381) "Kafka Architecture: Kafka Replication ??? Replicating to Partition 0" ba??l??????, 1inci paragraf.
    - Client mesaj??n commit edilip edilmedi??ini API arac??l?????? ile bilebiliyor. kaynak: (source-id: 385) "KAFKA REPLICATION: 0 TO 60 IN 1 MINUTE" ba??l?????? , 3??nc?? paragraf??n ilk c??mlesi.
    - Consumer'lar sadece commit edilmi?? record'lar?? okuyabiliyor. kaynak: (source-id: 381) "Kafka Architecture: Kafka Replication ??? Replicating to Partition 0" ba??l??????, 1inci paragraf.

- # acknowledgment (or ACK)
  producer (client) taraf??nda ayarlanan bir parametredir. bu parametre ??u de??erleri alabilir:
  - 0: client iste??i atar. iste??in bir yere ula????p ula??mad?????? ile hi?? ilgilenmez.
  - 1: client sadece leader'??n iste??i ald??????ndan emin olana kadar bekler. hata al??rsa tekrar istek atar.
  - all: o partition i??in t??m follower'lar??n bu record'u ald??????ndan emin olana kadar bekler. hata al??rsa tekrar istek atar.

  kaynak: (source-id: 387) "Apache Kafka ack-value" ba??l??????.

# Kafdrop
Kafka i??in a????k kaynakl?? GUI monitoring uygulamas??. Kafdrop Kafka API'sini kullanarak web aray??zde monitor etti??i bilgileri g??steriyor. Sadece temel ??zellikleri i??eriyor. 

# MirrorMaker
Kafka default'ta (tek ba????na) multi DC hizmeti mevcut de??il. Bunun i??in Kafka sunucusundan ba????ms??z yaz??l??mlardan yararlanmak gerekiyor. Bunlar biride MirrorMaker.

MirrorMaker Kafka'lardan ba????ms??z olarak aya??a kald??r??l??yor. Aya??a kald??r??rken t??m data center'lardaki her Kafka'n??n IP-port bilgileri config ile MirrorMaker'e veriliyor. Ayn?? zamanda MirrorMaker'a, hangi Kafka'lardaki topic'lerin hangi Kafka'lara sync olaca???? gibi bilgiler veriliyor. Bu bilgiler do??rultusunda MirrorMaker consumer ve producer olarak davran??p, data center'lar aras??nda bu Kafka'lar?? sync etmeye ??al??????yor.

'Confluent' firmas??n??n geli??tirdi??i 'Replicator', 'MirrorMaker'a alternatiftir.

# Kafka connect
Kafka'dan ba????ms??z ??al????an bir instance'd??r. 2 farkl?? connector'?? vard??r:
- __Source connector__

  farkl?? ba????ms??z sistemlerden (??rne??in veritabanlar??ndan), data okur ve bunlar?? Kafka'da topic'lere kaydeder. ??rnek: PostgreSQL'deki bir tablodaki her de??i??ikli??in, Kafka'da topic alt??nda event'lerde g??rmek isteyebiliriz.

  Kafka connect, de??i??iklikleri okuyaca???? sistemin connector'??ne ihtiya?? duyar. ??rnek "MySQL connector jar"'??n?? path'e eklemek zorunday??z. Yukar??da "debezium" gibi arac?? uygulamalar kullanmak durumunday??z.

- __Sink connector__

  source'nin tersine, Kafka topic'lerindeki data'lar??n ba????ms??z bir sisteme kaydedilmesini sa??lar. ??rnek: her Kafka'daki data'n??n ElasticSearch'e kaydedilmesini isteyebiliriz.
