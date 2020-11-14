### Table of Contents </br>
[Основные термины ElasticSearch](#es_decription) </br>
[Основные операции с ElasticSearch](#es_operations) </br>
[Конфигурационный файл ElasticSearch](#es_config_file)</br>

---

### Основные термины ElasticSearch <a name=es_decription></a></br>
</br>

### Основные операции с ElasticSearch <a name=es_operations></a></br>

Получение всей информацию о состоянии кластера</br>
```
curl -XGET 'http://localhost:9200/_cluster/stats?human&pretty'
```
Компактный вывод информации о «здоровье» кластера</br>
```
curl http://localhost:9200/_cluster/health/
```

Получение индексов</br>
```
curl 'http://localhost:9200/_cat/indicies?v'
```


delete indicies</br>
elasticsearch-curator</br>

### Конфигурационный файл ElasticSearch <a name=es_config_file></a></br>
