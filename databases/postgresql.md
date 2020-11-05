# Table of Contents
[Создание read-only пользователя в PostgreSQL](#postgresql_create_readonly_user)



##### Создание пользователя и базы </br>
---
---
##### Создание read-only пользователя в PostgreSQL <a name="postgresql_create_readonly_user"></a> </br>
Источник: https://gist.github.com/oinopion/4a207726edba8b99fd0be31cb28124d0  </br>
 </br>
Create a group
```
CREATE ROLE readaccess;
```
 </br>
Grant access to existing tables
```
GRANT USAGE ON SCHEMA public TO readaccess;
GRANT SELECT ON ALL TABLES IN SCHEMA public TO readaccess;
```
 </br>
Grant access to future tables
```
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT ON TABLES TO readaccess;
```
 </br>
Create a final user with password
```
CREATE USER user WITH PASSWORD 'secret';
GRANT readaccess TO user;
```
