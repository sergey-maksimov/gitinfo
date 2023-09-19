[[TOC]]
## <a id="git">Что такое GIT?</a>
**Git** — это система контроля версий, которая помогает отслеживать изменения в проекте. Этот инструмент можно использовать как для индивидуальной, так и для командной работы.
Скачать Git для Windows можно по ссылке [Download for Windows](https://git-scm.com/download/win)

## <a id="commit">Что такое коммит?</a>
**Коммит** — это одна из основных сущностей в Git (и в других системах контроля версий). Коммит гарантирует, что изменения будут сохранены в истории и при необходимости к ним можно будет «откатиться»

## <a id="hash">Что такое хеш? Хеширование коммитов</a>
**Хеширование** (от англ. hash, «рубить», «крошить», «мешанина») — это способ преобразовать набор данных и получить их «отпечаток» (англ. fingerprint).
**Информация о коммите** — это набор данных: когда был сделан коммит, содержимое файлов в репозитории на момент коммита и ссылка на предыдущий, или родительский (англ. parent), коммит.
Git хеширует (преобразует) информацию о коммите с помощью алгоритма SHA-1 (от англ. Secure Hash Algorithm — «безопасный алгоритм хеширования») и получает для каждого коммита свой уникальный хеш — результат хеширования.
Git хранит таблицу соответствий **хеш → информация о коммите**. Если вы знаете хеш, вы можете узнать всё остальное: автора и дату коммита и содержимое закоммиченных файлов. Можно сказать, что хеш — основной идентификатор коммита.
Все хеши и таблицу хеш → информация о коммите Git сохраняет в служебные файлы. Они находятся в скрытой папке **.git** в репозитории проекта.

## <a id="head">Файл HEAD</a>
Файл **HEAD** (англ. «голова», «головной») — один из служебных файлов папки .git. Он указывает на коммит, который сделан последним (то есть на самый новый).
Когда вы делаете коммит, Git обновляет refs/heads/master — записывает в него хеш последнего коммита. Получается, что HEAD тоже обновляется, так как ссылается на refs/heads/master.
При работе с Git указатель HEAD используется довольно часто. Мы уже упоминали, что многие команды Git принимают в качестве параметра хеш коммита. Если нужно передать последний коммит, то вместо его хеша можно просто написать слово HEAD — Git поймёт, что вы имели в виду последний коммит.

## <a id="status">Статусы файлов в Git</a>
Одна из ключевых задач Git — отслеживать изменения файлов в репозитории.
* **untracked** (англ. «неотслеживаемый») - новые файлы в Git-репозитории помечаются как untracked, то есть неотслеживаемые. Git «видит», что такой файл существует, но не следит за изменениями в нём. У untracked-файла нет предыдущих версий, зафиксированных в коммитах или через команду git add
* **staged** (англ. «подготовленный») - после выполнения команды git add файл попадает в staging area (от англ. stage — «сцена», «этап [процесса]» и area — «область»), то есть в список файлов, которые войдут в коммит. В этот момент файл находится в состоянии staged. Staging area также называют index (англ. «каталог») или cache (англ. «кеш»), а состояние файла staged иногда называют indexed или cached.
* **tracked** (англ. «отслеживаемый») — это противоположность untracked. Оно довольно широкое по смыслу: в него попадают файлы, которые уже были зафиксированы с помощью git commit, а также файлы, которые были добавлены в staging area командой git add. То есть все файлы, в которых Git так или иначе отслеживает изменения.
* **modified** (англ. «изменённый») означает, что Git сравнил содержимое файла с последней сохранённой версией и нашёл отличия. Например, файл был закоммичен и после этого изменён.
![Типичный жизненный цикл файла в Git](https://pictures.s3.yandex.net/resources/M2_T5_1686651284.png)
>Файл может быть одновременно в staged и modified. Да, так может быть, если файл уже добавили в список на коммит через git add, а после этого изменили.

>Файл может быть tracked и staged. Да, файл считается tracked, если он staged.

## <a id="readme">Для чего нужен файл readme.md?</a>
Чтобы другие пользователи, а также потенциальные клиенты или работодатели могли понять, что представляет собой проект, его нужно описать.

Как правило, в README.md проекта можно найти следующую информацию:
1. Название проекта и его краткое описание: кем создан, для чего, какие решает задачи и какие закрывает проблемы.
2. Технологии, которые применяются в проекте. В чём его отличие от аналогичных.
3. Документация проекта — подробная инструкция о том, что представляет собой проект.
4. Планы проекта, если они есть.

В файле readme.md используется специальный язык разметки - **Markdown**. Шпаргалка по Markdown [Github](https://gist.github.com/fomvasss/8dd8cd7f88c67a4e3727f9d39224a84c)

## <a id="commands">Основные команды:</a>
* **git init** - инициализация Git-репозитория в проекте
* **git status** - посмотреть состояние или состояние репозитория
* **rm -r .git или rm -rf .git** - "разгитить" папку при случайной инициализации не той папки
* **git add** - подготовить файл к сохранению, **git add --all** - подготовить все файлы к сохранению, **git add .** - добавить в репозиторий текущую папку со всеми файлами
* **git commit -m "Что изменилось"** - делаем коммит
* **git log** - просмотреть историю коммитов
* **git log --oneline** - посмотреть сокращенный лог
* **git remote add** - привязать удаленный репозиторий к локальному. Пример: *git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git*
* **git remote -v** - убедиться что локальный и удаленный репозитории связаны
* **git push** - отправить изменения на удаленный репозиторий. В первый раз данную команду необходимо вызывать с флагом -u (для связи локальной ветки и одноименной удаленной) и параметрами origin (имя удаленного репозитория) и main или master (название текущей ветки). Пример: *git push -u origin main*
