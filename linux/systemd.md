### Table of Contents </br>
[Добавление dns серверов в систему](#systemd_add_dns_servers) </br>
[Очистка dns кэша](#systemd_flush_dns_cache) </br>

---

#### ***Добавление dns серверов в систему*** <a name=systemd_add_dns_servers></a></br>
Для добавления своих DNS серверов необходимо прописать в файле /etc/systemd/resolved.conf
```
$ cat /etc/systemd/resolved.conf
<...>
[Resolve]
DNS=8.8.8.8 8.8.4.4
<...>
```
Необходимо перезагрузить systemd-resolved.service или перезагрузить компьютер.

---

#### ***Очистка dns кэша*** <a name=systemd_flush_dns_cache></a></br>
Для добавления своих DNS серверов необходимо прописать в файле /etc/systemd/resolved.conf

```sudo systemd-resolve --flush-caches```
