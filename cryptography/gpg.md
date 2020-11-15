### Table of Contents </br>
[Генерация новой пары ключей](#gpg_gen_key) </br>
[Просмотр ключей](#gpg_view_keys) </br>
[Экспорт ключей](#gpg_export_keys) </br>

---

#### Генерация новой пары ключей <a name="gpg_gen_key"></a> </br>
```
gpg --gen-key
```

#### Просмотр ключей <a name="gpg_view_keys"></a> </br>
Просмотр публичных ключей
```
gpg -k
```
Просмотр приватных ключей
```
gpg -K
```

#### Экспорт ключей <a name="gpg_export_keys"></a> </br>
Экспорт публичных ключей
```
gpg --export --armor keyid > public.gpg
```
Экспорт приватных ключей
```
gpg -K
```
