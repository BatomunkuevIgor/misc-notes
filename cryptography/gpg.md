### Table of Contents </br>
[Генерация новой пары ключей](#gpg_gen_key) </br>
[Просмотр ключей](#gpg_view_keys) </br>
[Экспорт ключей](#gpg_export_keys) </br>
[Импорт ключей](#gpg_import_keys) </br>
[Удаление ключей](#gpg_delete_keys) </br>

---

#### Генерация новой пары ключей <a name="gpg_gen_key"></a> </br>
```gpg --gen-key```
</br>
#### Просмотр ключей <a name="gpg_view_keys"></a> </br>
Просмотр публичных ключей
```gpg -k```
</br>
Просмотр приватных ключей
```gpg -K```
</br>
#### Экспорт ключей <a name="gpg_export_keys"></a> </br>
Экспорт публичных ключей
```gpg --export --armor <KeyId> > public.gpg```
Экспорт приватных ключей
```gpg --export-secret-key --armor <KeyId> > secret.gpg```
</br>
#### Импорт ключей <a name="gpg_import_keys"></a> </br>
Импорт публичных ключей
```gpg --import public.gpg```
Импорт приватных ключей
```gpg --import secret.gpg```
</br>
#### Удаление ключей <a name="gpg_delete_keys"></a> </br>
Экспорт публичных ключей
```gpg --delete-keys <KeyId>```
Экспорт приватных ключей
```gpg --delete-secret-key <KeyId>```
