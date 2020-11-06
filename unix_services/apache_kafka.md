### Table of Contents </br>
[Основные термины kafka](#decription_kafka) </br>
[Параметры очистки журналов kafka](#retention_policy_kafka) </br>
</br>

##### Основные термины kafka <a name="decription_kafka"></a> </br>
Продюсеры пишут (пишут только последовательно, нету update, только insert)</br>
Консьюмеры читают</br>
ofsset с какой позиции читать</br>


##### How retention for topic works? How to see retention policy for topic? <a name=retention_policy_kafka"></a> </br>

    Time based retention
        Once the configured retention time has been reached for Segment, it is marked for deletion or compaction depending on configured cleanup policy. Default retention period for Segments is 7 days.
            log.retention.ms
            log.retention.minutes
            log.retention.hours
    Size Based Retention:
        In this policy, we configure the maximum size of a Log data structure for a Topic partition. Once Log size reaches this size, it starts removing Segments from its end.
        log.retention.bytes
