### Table of Contents </br>
[Основные термины kafka](#decription_kafka) </br>
[Консольные утилиты](#kafka_console_utilites) </br>
[Параметры очистки журналов kafka](#retention_policy_kafka) </br>

[Работа с топиками kafka](#kafka_operations_topic) </br>
[Очистка топиков](#t2) </br>
[t3](#t3) </br>

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
**Partition** - шард топика</br>
**Partition** - шард топика</br>
**Partition** - шард топика</br>
**Partition** - шард топика</br>
</br>

#### Работа с топиками kafka <a name=kafka_operations_topic> </br>
kafka-topics --zookeeper zookeeper:2181 --list</br>
kafka-topics --bootstrap-server localhost:9092 --list</br>
kafka-topics --bootstrap-server localhost:9092 --describe --topic <topic></br>
Запрос конфигов для топиков
```
kafka-topics --bootstrap-server localhost:9092 --describe-all --entity-type topics
```
Очистка топика
```
kafka-topics --bootstrap-server localhost:9092 --alter --entity-type topics --entity-name TopicName --add-config retention.ms=1000
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
