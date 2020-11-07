### Table of Contents </br>
[Основные термины kafka](#decription_kafka) </br>
[Консольные утилиты](#kafka_console_utilites) </br>
[Параметры очистки журналов kafka](#retention_policy_kafka) </br>

[Работа с топиками kafka](#kafka_operations_topic) </br>
[Очистка топиков](#t2) </br>
[Tools Kafka](#kafka_tools)</br>

</br>
---</br>

#### Основные термины kafka <a name="decription_kafka"></a> </br>
**Record** - запись, состоящая из ключа и значения</br>
**Topic** - категория или имя потока, куда публикуются данные</br>
**Producer** - процесс публикующий данные в топик (пишут только последовательно, нету update, только insert)</br>
**Consumer** - процесс читающий данные из топика</br>
**Consumer group** - группа читателей из одного топика для балансировки нагрузки по чтению. Разные consumer groups читают независимо друг от друга</br>
**Ofsset** - позиция записи</br>
**Partition** - шард топика</br>
</br>
Внутренние служебные топики</br>
**__consumer_offsets** - информация о позициях чтения всех консьюмеров по всем партициям. Хранится в сжатом виде</br>
**_schema** - топик создаваемый confluent, хранит информацию по Schema Registry</br>
</br>

#### Консольные утилиты <a name=kafka_console_utilites> </br>
**kafka-configs.sh** - This tool helps to manipulate and describe entity config for a topic, client, user or broker</br>
**kafka-topics.sh** - Create, delete, describe, or change a topic.</br>
**kafka-console-producer.sh** - This tool helps to read data from standard input and publish it to Kafka.</br>
**kafka-console-consumer.sh** - This tool helps to read data from Kafka topics and outputs it to standard output.</br>
**kafka-producer-perf-test.sh** - This tool is used to verify the producer performance.</br>
</br>

#### Работа с топиками kafka <a name=kafka_operations_topic> </br>
При работе с топиками (и не только наверное) можно подключаться как к самой кафке указанеием параметра --bootstrap-server localhost:9092, так и к зукиперу указанием параметра --zookeeper zookeeper:2181 </br>
Используется что то одно либо --bootstrap-server localhost:9092, либо --zookeeper zookeeper:2181, оба использовать не надо
</br>
Создание топика
```
kafka-topics --create --zookeeper zookeeper:2181 --list>
```
</br>
Изменение количества партиций в топике (в данном примере задается количество партиций 4, можно только увеличивать)
```
kafka-topics --zookeeper zookeeper:2181 --alter --topic TopicName --partition 4</br>
```
</br>
Вывод списка топиков
```
kafka-topics --bootstrap-server localhost:2181 --list
```
</br>
Вывести описание топика
```
kafka-topics --zookeeper zookeeper:2181 --describe --topic TopicName
```
</br>
Запись в топик (с консоли, построчно руками вводим)
```
kafka-console-producer.sh --topic TopicName --zookeeper zookeeper:2181
```
</br>
Запись в топик (отправкой файла в команду)
```
kafka-console-producer.sh --topic TopicName --zookeeper zookeeper:2181 < mysource.file
```
</br>
Чтение данных с топика
```
kafka-console-consumer.sh --topic TopicName --zookeeper zookeeper:2181 --from-beginning
```


</br>
Запись в топик (отправкой файла в команду)
```
kafka-console-producer.sh --topic TopicName --zookeeper zookeeper:2181 < mysource.file
```






</br>
Запрос конфигурационных параметров для топика
```
kafka-topics --bootstrap-server localhost:9092 --describe-all --entity-type topics
```
Очистка топика динамической установкой параметра времени жизни топика (retention.ms=1000 данные в топике будут жить всего 1 секунду)
```
kafka-topics --bootstrap-server localhost:9092 --alter --entity-type topics --entity-name TopicName --add-config retention.ms=1000
```
Удаление динамических параметров (--delete-config удаляет ранее установленный параметр жизни топика)
```
kafka-topics --bootstrap-server localhost:9092 --alter --entity-type topics --entity-name TopicName --delete-config retention.ms
```
</br>

#### How retention for topic works? How to see retention policy for topic? <a name=retention_policy_kafka></a> </br>

    Time based retention
        Once the configured retention time has been reached for Segment, it is marked for deletion or compaction depending on configured cleanup policy. Default retention period for Segments is 7 days.
            log.retention.ms
            log.retention.minutes
            log.retention.hours
    Size Based Retention:
        In this policy, we configure the maximum size of a Log data structure for a Topic partition. Once Log size reaches this size, it starts removing Segments from its end.
        log.retention.bytes








#### Tools Kafka <a name=kafka_tools> </br>
kafkacat (изучить)
```
kafkacat -b 10.0.0.1 -L
```
kafkactl (изучить)


---

---