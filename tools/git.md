### Table of Contents </br>
[Основные термины Git](#git_decription) </br>
[Структура файлов Git в проекте](#git_structure_project) </br>
[Форматированный вывод истории коммитов Git](#git_format_log)</br>

</br>
---
</br>

#### Основные термины Git <a name="git_decription"></a> </br>
</br>

#### Структура файлов Git в проекте <a name="git_structure_project"></a> </br>

Cтруктура каждого проекта, работающего под управлением Git, состоит из трех проектов:</br>
+ служебная директория (git directory), хранилище метаданных и базу данных всех объектов проекта.</br>
+ рабочая директория (working directory), папка, в которой  файлы твоего проекта.</br>
+ область подготовленных файлов (staging area). Под областью подготовленных файлов подразумевается обычный файл, расположенный в служебной директории и содержащий информацию об изменениях, которые войдут в следующий коммит.</br>
</br>

#### Форматированнный вывод истории коммитов <a name="git_format_log"></a> </br>
```
git log --graph --abbrev-commit --decorate --all --format=format:"%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(dim white) - %an%C(reset) %C(bold green)(%ar)%C(reset)%C(bold yellow)%d%C(reset)%n %C(white)%s%C(reset)"
```
