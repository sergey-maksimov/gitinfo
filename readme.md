# Что такое GIT?
**Git** — это система контроля версий, которая помогает отслеживать изменения в проекте. Этот инструмент можно использовать как для индивидуальной, так и для командной работы.
Скачать Git для Windows можно по ссылке [Download for Windows](https://git-scm.com/download/win)

# Что такое коммит?
**Коммит** — это одна из основных сущностей в Git (и в других системах контроля версий). Коммит гарантирует, что изменения будут сохранены в истории и при необходимости к ним можно будет «откатиться»

# Для чего нужен файл readme.md?
Чтобы другие пользователи, а также потенциальные клиенты или работодатели могли понять, что представляет собой проект, его нужно описать.

Как правило, в README.md проекта можно найти следующую информацию:
1. Название проекта и его краткое описание: кем создан, для чего, какие решает задачи и какие закрывает проблемы.
2. Технологии, которые применяются в проекте. В чём его отличие от аналогичных.
3. Документация проекта — подробная инструкция о том, что представляет собой проект.
4. Планы проекта, если они есть.

В файле readme.md используется специальный язык разметки - **Markdown**. Шпаргалка по Markdown [Github](https://gist.github.com/fomvasss/8dd8cd7f88c67a4e3727f9d39224a84c)

# Основные команды:
* **git init** - инициализация Git-репозитория в проекте
* **git status** - посмотреть состояние или состояние репозитория
* **rm -r .git или rm -rf .git** - "разгитить" папку при случайной инициализации не той папки
* **git add** - подготовить файл к сохранению, **git add --all** - подготовить все файлы к сохранению, **git add .** - добавить в репозиторий текущую папку со всеми файлами
* **git commit -m "Что изменилось"** - делаем коммит
* **git log** - просмотреть историю коммитов
* **git remote add** - привязать удаленный репозиторий к локальному. Пример: *git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git*
* **git remote -v** - убедиться что локальный и удаленный репозитории связаны
* **git push** - отправить изменения на удаленный репозиторий. В первый раз данную команду необходимо вызывать с флагом -u (для связи локальной ветки и одноименной удаленной) и параметрами origin (имя удаленного репозитория) и main или master (название текущей ветки). Пример: *git push -u origin main*
