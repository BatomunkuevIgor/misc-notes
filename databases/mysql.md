```CREATE DATABASE `zabbix` CHARACTER SET utf8 COLLATE utf8_general_ci;```
```GRANT ALL PRIVILEGES ON zabbix.* TO 'zabbix'@'localhost' IDENTIFIED BY 'password' WITH GRANT OPTION;```


```UPDATE user SET password=PASSWORD("password") where User='zabbix';```


```mysqladmin -u root password 'НОВЫЙ_ПАРОЛЬ'```
```mysqladmin -u root -p'ТЕКУЩИЙ_ПАРОЛЬ' password 'НОВЫЙ_ПАРОЛЬ'```



```mysqldump -uroot -p database > database.sql```





```CREATE DATABASE `zabbix` CHARACTER SET utf8 COLLATE utf8_general_ci;```
```GRANT ALL PRIVILEGES ON zabbix.* TO 'zabbix'@'localhost' IDENTIFIED BY 'password' WITH GRANT OPTION;```

