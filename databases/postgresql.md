### Table of Contents </br>
- [Создание read-only пользователя в PostgreSQL](#postgresql_create_readonly_user)
- [Создание dump-а БД](#postgresql_pgdump)
- [Восстановление dump-а БД](#postgresql_pgdump_restore)
- [Зачистка wal логов PostgreSQL](#postgresql_pg_resetwal)
- [Проверка списка доступных расширений](#postgresql_show_available_extensions)
- [Liquibase — Waiting for changelog lock….](#liquibase_lock)


##### Создание пользователя и базы </br>
123
3232
3232

--- 
##### Создание read-only пользователя в PostgreSQL <a name="postgresql_create_readonly_user"></a> </br>
Источник: https://gist.github.com/oinopion/4a207726edba8b99fd0be31cb28124d0  </br>
</br>
Create a group </br>
```CREATE ROLE readaccess;```
</br>
Grant access to existing tables </br>
```GRANT USAGE ON SCHEMA public TO readaccess;```</br>
```GRANT SELECT ON ALL TABLES IN SCHEMA public TO readaccess;```</br>
</br>
Grant access to future tables </br>
```ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT ON TABLES TO readaccess;```
</br>
Create a final user with password </br>
```CREATE USER user WITH PASSWORD 'secret';```
```GRANT readaccess TO user;```
</br>

---
##### Создание dump-а БД<a name="postgresql_pgdump"></a></br>
```sudo -Hu postgres pg_dump -d dbname | bzip2 > dbdump.sql.bz2```
</br>

---
##### Восстановление dump-а БД<a name="postgresql_pgdump_restore"></a></br>
```bzip2 -d dbdump.sql.bz2 |sudo -Hu postgres psql dbname```
</br>

---
##### Зачистка wal логов PostgreSQL<a name="postgresql_pg_resetwal"></a></br>
Нужно остановить сервер PostgreSql</br>
Выполняем команду pg_controldata указывая путь до базы postgresql</br>
```/usr/lib/postgresql-8.4/bin/pg_controldata /opt/backup/postgresql/8.4/data/```</br>
нас интересуют строчки:</br>
```Latest checkpoint's NextXID: 0/1186399159```</br>
```Latest checkpoint's NextOID: 4716704```</br>
Выполняем команду pg_resetwal коророй указываем NextOID и NextXID (команда выполняется из под пользователя postgres)</br>
```pg_resetwal  -o 4716704 -x 1186399159 -f /var/lib/pgpro/std-12/data/```</br>
Запускаем сервер PostgreSql</br>
</br>

---
##### Проверка списка доступных расширений <a name="postgresql_show_available_extensions"></a></br>
```postgres$ psql -c 'SELECT name, comment FROM pg_available_extensions ORDER BY name;'```
</br>

---
##### Liquibase — Waiting for changelog lock….<a name="liquibase_lock"></a></br>
Following SQL query returns locked column as true.</br>
```SELECT * FROM DATABASECHANGELOGLOCK;```</br>
To remove database lock:</br>
```UPDATE DATABASECHANGELOGLOCK SET locked=false, lockgranted=null, lockedby=null WHERE id=1;```




================================================================================</br>
================================================================================</br>
================================================================================</br>
================================================================================</br>
================================================================================</br>
================================================================================</br>
================================================================================</br>
================================================================================</br>



Killing Idle Sessions
```
SELECT pg_terminate_backend(pg_stat_activity.pid)
FROM pg_stat_activity
WHERE pg_stat_activity.datname = '[your database name goes here]'
  AND pid <> pg_backend_pid();
```




Основное
Инициализация БД
postgresql-setup initdb
или:

sudo su - postgres -c "initdb -E UTF8 -D '/var/lib/pgsql/data'"
Поддержка русского:
В файл /var/lib/pgsql/data/postgresql.conf добавляем:

client_encoding = UTF8
Доступ по паролю:
vi /var/lib/pgsql/data/pg_hba.conf
должно быть так (host .. md5):

host    all             all             127.0.0.1/32            md5
host    all             all             ::1/128                 md5
Подключиться в консоли:
sudo -u postgres psql
Создать пользователя и БД(с поддержкой русского):
CREATE USER jira WITH password 'jira123';
CREATE DATABASE jira5db WITH OWNER jira ENCODING 'UTF8' TEMPLATE = template0;
GRANT ALL privileges ON DATABASE jira5db TO jira;
Посмотреть список баз данных:
\l
Подключиться к БД:
\connect database_name
Список таблиц:
\dt *
Описание таблиц

\d *
Удалить БД:
DROP DATABASE jira5db;
Дамп БД:
pg_dump -c -h 192.168.0.1 -U test_user test_database > ./dump.sql
Залить дамп:
cat dump.sql | psql -h 192.168.0.1 test_database test_user
Если при создании БД выдается ошибка createdb: database creation failed: ERROR: new encoding (UTF8) is incompatible with the encoding of the template database (SQL_ASCII)
Все БД создаются из темплейтов, в данном случае у нас просто нет темплейта для UTF8 - переделаем существующий template1 на UTF8:

UPDATE pg_database SET datistemplate = FALSE WHERE datname = 'template1';
DROP DATABASE template1;
CREATE DATABASE template1 WITH TEMPLATE = template0 ENCODING = 'UNICODE' LC_COLLATE = 'en_US.UTF-8' LC_CTYPE = 'en_US.UTF-8';
UPDATE pg_database SET datistemplate = TRUE WHERE datname = 'template1';

