### Table of Contents </br>
- [Создание read-only пользователя в PostgreSQL](#postgresql_create_readonly_user)
- [Создание dump-а БД](#postgresql_pgdump)
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
</br>
##### Создание dump-а БД<a name="postgresql_pgdump"></a></br>
```sudo -Hu postgres pg_dump -d dbname | bzip2 > dbname.sql.bz2```
</br>
#### Зачистка wal логов PostgreSQL<a name="postgresql_pg_resetwal"></a></br>
```pg_resetwal -f /var/lib/postgres/data/```
</br>
##### Проверка списка доступных расширений <a name="postgresql_show_available_extensions"></a></br>
```postgres$ psql -c 'SELECT name, comment FROM pg_available_extensions ORDER BY name;'```
</br>
##### Liquibase — Waiting for changelog lock….<a name="liquibase_lock"></a></br>
Following SQL query returns locked column as true.</br>
```SELECT * FROM DATABASECHANGELOGLOCK;```

To remove database lock:</br>
```UPDATE DATABASECHANGELOGLOCK SET locked=false, lockgranted=null, lockedby=null WHERE id=1;```

