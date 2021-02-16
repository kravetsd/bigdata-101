## Installing kafka to Cloudera VM:

Since cloudera vm is based on Centos 6 :
```
Version of cloudera OS:
[cloudera@quickstart ~]$ lsb_release -a
LSB Version:	:base-4.0-amd64:base-4.0-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	CentOS
Description:	CentOS release 6.7 (Final)
Release:	6.7
Codename:	Final
[cloudera@quickstart ~]$ 



Compatible kafka:          
[cloudera@quickstart opt]$ ll /tmp/kafka_2.11-0.9.0.0.tgz 
-rw-r--r-- 1 root root 35600524 Feb  8 21:54 /tmp/kafka_2.11-0.9.0.0.tgz
[cloudera@quickstart opt]$ 



Creating topic:
[cloudera@quickstart kafka_2.11-0.9.0.0]$ bin/kafka-topics.sh --create --topic 'dkravets-bigdata-101' --zookeeper 'localhost:2181' --replication-factor 1 --partition 1
Created topic "dkravets-bigdata-101".


Checking tpics:
[root@quickstart kafka_2.11-0.9.0.0]# bin/kafka-topics.sh --list --zookeeper localhost:2181
dkravets-bigdata-101
[root@quickstart kafka_2.11-0.9.0.0]# 


starting a pconsile producer:
                                          given to allow fail-over.            
[root@quickstart kafka_2.11-0.9.0.0]# bin/kafka-topics.sh --list --zookeeper localhost:2181
dkravets-bigdata-101
[root@quickstart kafka_2.11-0.9.0.0]# bin/kafka-console-producer.sh --broker-list localhost:9092 --topic dkravets-bigdata-101
Hello Bigdata 1010 Epam from Dmitriy Kravets!


Starting a console consumer:
[root@quickstart kafka_2.11-0.9.0.0]#  bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic dkravets-bigdata-101 --from-beginning --zookeeper localhost:2181
Hello Bigdata 1010 Epam from Dmitriy Kravets!

```