---
layout: post
title:  "Kafka on Docker"
---
**Kafka on Docker**

<pre>
  <code>
  docker run -d --name=kafka -p 9092:9092 apache/kafka
  </code>
</pre>

<pre>
  <code>
  >asa-welle@asa-welle-GF63-Thin-10SC:~/github-pages-site/skills-github-pages$ docker exec -ti kafka /opt/kafka/bin/kafka-console-producer.sh --bootstrap-server :9092 --topic hurricaneian
  >Ft. Myers Beach is under 15' of surge.
  [2025-04-01 22:16:48,788] WARN [Producer clientId=console-producer] The metadata response from the cluster reported a recoverable issue with correlation id 5 : {hurricaneian=UNKNOWN_TOPIC_OR_PARTITION} (org.apache.kafka.clients.NetworkClient)
  >Sanibel is under 12' of surge.
  >Sanibel causeway bridge is out.
  >Pine Island Bridge is out.
  >asa-welle@asa-welle-GF63-Thin-10SC:~/github-pages-site/skills-github-pages$ 
  </code>
</pre>

<pre>
  <code>
  asa-welle@asa-welle-GF63-Thin-10SC:~$ docker exec -ti kafka /opt/kafka/bin/kafka-console-consumer.sh --bootstrap-server :9092 --topic hurricaneian --from-beginning
  Ft. Myers Beach is under 15' of surge.
  Sanibel is under 12' of surge.
  Sanibel causeway bridge is out.
  Pine Island Bridge is out.
  Processed a total of 4 messages
  </code>
</pre>
