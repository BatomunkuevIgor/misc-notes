### Table of Contents </br>
- [Создание read-only пользователя в PostgreSQL](#postgresql_create_readonly_user)
</br>
---</br>
##### Создание пользователя и базы </br>
---
##### Создание read-only пользователя в PostgreSQL <a name="postgresql_create_readonly_user"></a> </br>
Источник: https://gist.github.com/oinopion/4a207726edba8b99fd0be31cb28124d0  </br>
 </br>
Create a group </br>
```
CREATE ROLE readaccess;
```
Grant access to existing tables </br>
```
GRANT USAGE ON SCHEMA public TO readaccess;
GRANT SELECT ON ALL TABLES IN SCHEMA public TO readaccess;
```
Grant access to future tables </br>
```
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT ON TABLES TO readaccess;
```
Create a final user with password </br>
```
CREATE USER user WITH PASSWORD 'secret';
GRANT readaccess TO user;
```
