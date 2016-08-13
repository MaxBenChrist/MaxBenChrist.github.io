---
layout: post
title:  "Connect to Apache Kafka from Python using SSL"
date:   2016-08-13 19:00:00 +0100
categories: Kafka, kafka-python, Python, pykafka
comments: True
tldr: I will show you how to establish an encrypted SSL connection to an Apache Kafka Instance from Python.
---

__TLDR: I will show you how to establish an encrypted SSL connection to an Apache Kafka Instance from Python__

---
<br>

### What is Apache Kafka?

[Apache Kafka](http://kafka.apache.org){:rel="nofollow"} is a centralized message stream which is fast, scalable, durable and distributed by design. It takes messages from event producers and then distributes them among message consumers:

![Kafka distributes messages](/images/20160803_ssl_kafka_overview.png){:rel="nofollow"}

Kafka originates from Linkedin where it is able to process [1.4 trillion messages](https://engineering.linkedin.com/blog/2016/04/kafka-ecosystem-at-linkedin){:rel="nofollow"} per day that sum up to [1.34 PB ](https://engineering.linkedin.com/apache-kafka/how-we_re-improving-and-advancing-kafka-linkedi) of information each week. In the Linkedin stack, every message gets consumed by about four message consumers/applications on average. Other companies followed and now, for example [Zalando](https://tech.zalando.de/blog/data-integration-in-a-world-of-microservices/){:rel="nofollow"}, [Uber](https://eng.uber.com/tech-stack-part-two/){:rel="nofollow"} or [Netflix](http://techblog.netflix.com/2016/02/evolution-of-netflix-data-pipeline.html){:rel="nofollow"} are making Kafka part of their architectures.

Inside Kafka, the message stream is divided into topics to make sure that messages are only passed to consumers that subscribed to it. The messages themselves are serialized, stateless objects. You can think of them as being lines of a log file, full .txt files or .csv tables. It is recommended to use small objects because Kafka is well optimized for shorter messages, for example the engineers of Linkedin agreed on a limit of 1 MB per message. So it is probably not a good idea to stream full images or videos into Kafka without splitting them into small chunks.

Further, it is possible to use Kafka as a persistency layer by specifying an offset time. This means that messages will be passed to the subscribed consumers  after buffering them up to the specified time.

### What is interesting about Apache Kafka?

In general, the CAP Theorem states that is not possible for distributed systems to guarantee consistency, availability and partition tolerance at the same time. The design of Kafka focuses on [maintaining highly available and strongly consistent replicas](https://engineering.linkedin.com/kafka/intra-cluster-replication-apache-kafka){:rel="nofollow"} (strong consistency means that all replicas are byte-to-byte identical). Kafka clusters were designed to support replicas within a single datacenter, where network partitioning is rare. Hence, partition tolerance over several data-centers is not guaranteed, which is why it probably should not be installed as a permanent data storage layer.[^1]

Kafka can be used to enable a service-oriented architecture based on micro services such as [happening at Zalando](https://tech.zalando.de/blog/data-integration-in-a-world-of-microservices/){:rel="nofollow"}. In such architecture, the interdependencies of monolithic applications are avoided by small modular components that communicate based on events/messages. This allows rapid prototyping and development as well as a data-driven proceeding in general. It should be pointed out that in such an architecture, Kafka is the single point of failure. If the central messaging service goes down, the micro services will not be able to communicate. If you are interested in the topic of (complex) event processing in distributed system, I recommend the book *"The power of events"* by David Luckham.

Another use case would be to use Kafka as a buffer before filling records into more permanent data layers. Here, Kafka allows to stack up messages to load them into the database bulkwise. Netflix is using Kafka in this way to buffer the output of [*"virtually every application"* ](http://techblog.netflix.com/2016/04/kafka-inside-keystone-pipeline.html){:rel="nofollow"} before processing it further.

### Setting up an instance of Kafka with SSL

![Kafka distributes messages](/images/20160803_ssl_kafka_ssl.png){:rel="nofollow"}

Kafka can encrypt connections to message consumers and producers by SSL. Instructions on how to set this up can be found in different places. For example, you can take the [Confluence platform documentation](http://docs.confluent.io/3.0.0/kafka/ssl.html){:rel="nofollow"} (the Confluence platform can be understood as a sophisticated wrapper/ecosystem around Kafka) or the [Apache Kafka documentation](http://kafka.apache.org/documentation.html#security_ssl){:rel="nofollow"}. Those instructions are based on ```keytool```, a java utility, to generate and sign SSL certificates. If we want to use those certificates in Python, we have to extract the credentials.

### Connect to Kafka using Python  

![Kafka distributes messages](/images/20160803_ssl_kafka_python.png){:rel="nofollow"}

The following Python packages allow to connect to Kafka:

*   ```pykafka```: [https://github.com/Parsely/pykafka](https://github.com/Parsely/pykafka){:rel="nofollow"}

*   ```kafka-python```: [https://github.com/dpkp/kafka-python](https://github.com/dpkp/kafka-python){:rel="nofollow"}

*   ```confluent-kafka-python```: [https://github.com/confluentinc/confluent-kafka-python](https://github.com/confluentinc/confluent-kafka-python){:rel="nofollow"}


But if you want to establish a SSL connection from Python, firstly you have to make sure you have the needed certificates and private keys in JKS containers as explained in the instructions from above.
Then, there are two ways to access certificates from Python:

*    Export certificates and keys from the JKS container to PEM format to use them inside ```kafka-python```
*    Import certificates and keys directly in Python by using for example the ```pyjks``` package

I was successful with the first approach, which is why I did not follow through with the second one. If you were successful with the second approach, just leave a comment under this post, I would like to hear about your experiences.

#### Extract the keys

After configuring your Apache Kafka instance, you have two JKS containers: 'kafka.client.keystore.jks' and 'kafka.client.truststore.jks'. The first one contains the signed client certificate, its private key and the 'CARoot' certificate used to sign them. The second one contains the certificate with which the client certificate and key were signed. Therefore, everything we need is contained in the 'kafka.client.keystore.jks' file. To get an overview of its content you can call:

``` shell
keytool -list -rfc -keystore kafka.client.keystore.jks
```

Now lets get to work. First, we will extract the client certificate:

``` shell
keytool -exportcert -alias localhost -keystore kafka.client.keystore.jks \
        -rfc -file certificate.pem
```

Next we will extract the clients key. This is not supported directly by ```keytool```, which is why we have to convert the keystore to pkcs12 format first and then extract the private key from that:

``` shell
keytool -v -importkeystore -srckeystore kafka.client.keystore.jks \
        -srcalias localhost -destkeystore cert_and_key.p12 -deststoretype PKCS12
openssl pkcs12 -in cert_and_key.p12 -nocerts -nodes
```

The second command only prints the key to STDOUT. From there it can be copied and pasted into 'key.pem'. Make sure to copy the lines inclusive between -----BEGIN PRIVATE KEY----- and -----END PRIVATE KEY-----. Finally we will extract the CARoot certificate:

``` shell
keytool -exportcert -alias CARoot -keystore kafka.client.keystore.jks -rfc \
        -file CARoot.pem
```

#### Connect by ```kafka-python```

Now we have the three files 'certificate.pem', 'key.pem', 'CARoot.pem'.
With ```kafka-python``` they can be passed as argument of the constructor of the consumer and producer:

``` python
from kafka import KafkaConsumer, KafkaProducer

consumer = KafkaConsumer(bootstrap_servers='my.server.com',
                          security_protocol='SSL',
                          ssl_check_hostname=True,
                          ssl_cafile='CARoot.pem',
                          ssl_certfile='certificate.pem',
                          ssl_keyfile='key.pem')

producer = KafkaProducer(bootstrap_servers='my.server.com',
                          security_protocol='SSL',
                          ssl_check_hostname=True,
                          ssl_cafile='CARoot.pem',
                          ssl_certfile='certificate.pem',
                          ssl_keyfile='key.pem')

# Write hello world to test topic
producer.send("test", bytes("Hello World"))
producer.flush()

# Read and print all messages from test topic
consumer.assign([TopicPartition(TOPIC, 0)])
consumer.seek_to_beginning(TopicPartition(TOPIC, 0))
for msg in consumer:
    print(msg)

```

#### Connect by ```pykafka```

In a similar way you can pass those files as arguments to ```pykafka```:


``` python
from pykafka import KafkaClient, SslConfig

config = SslConfig(cafile='CARoot.pem',
                   certfile='certificate.pem',
                   keyfile='key.pem')

client = KafkaClient(hosts='my.server.com',
                     ssl_config=config)

topic = client.topics["test"]

# Write hello world to test topic
with topic.get_sync_producer() as producer:
   producer.produce('Hello World')

# Print all messages from test topic
consumer = topic.get_simple_consumer()
for message in consumer:
   if message is not None:
       print('{} {}'.format(message.offset, message.value))

```

It is done, yeah! Now you are able to established SSL connections and write your own consumers and producers with either the ```kafka-python``` or ```pykafka``` packages.


-----
[^1]: It should be mentioned that the behavior and reliability of Kafka can be altered by several parameters such as the [*"acks"*](https://kafka.apache.org/090/javadoc/index.html?org/apache/kafka/clients/producer/KafkaProducer.html){:rel="nofollow"} flag. However, a full discussion would go beyond the scope of this post.
