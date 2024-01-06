  
# О проекте "Справочник по Git"
  *Данный проект основан на обучении основам Git.*
  *Здесь будет представлен проект-помощник по Git*
  ## Список команд и понятий

  ### Навигация
  * pwd (от англ. print working directory, «показать рабочую папку») — покажи, в какой я папке;
  * ls (от англ. list directory contents, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;
  * ls -a — покажи также скрытые файлы и папки, названия которых начинаются с символа .;
  * cd first-project (от англ. change directory, «сменить директорию») — перейди в папку first-project;
  * cd first-project/html — перейди в папку html, которая находится в папке first-project;
  * cd .. — перейди на уровень выше, в родительскую папку;
  * cd ~ — перейди в домашнюю директорию (/Users/Username);
  * cd / — перейди в корневую директорию.

  ### Работа с файлами и папками

1.Создание

* touch index.html (англ. touch, «коснуться») — создай файл index.html в текущей папке;
* touch index.html style.css script.js — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;
* mkdir second-project (от англ. make directory, «создать директорию») — создай папку с именем second-project в текущей папке.

2.Копирование и перемещение

  * cp file.txt ~/my-dir (от англ. copy, «копировать») — скопируй файл в другое место;
  * mv file.txt ~/my-dir (от англ. move, «переместить») — перемести файл или папку в другое место.

3.Чтение

  * cat file.txt (от англ. concatenate and print, «объединить и распечатать») — распечатай содержимое текстового файла file.txt.

4.Удаление

* rm about.html (от англ. remove, «удалить») — удали файл about.html;
* rmdir images (от англ. remove directory, «удалить директорию») — удали папку images;
* rm -r second-project (от англ. remove, «удалить» + recursive, «рекурсивный») — удали папку second-project и всё, что она содержит.


  ## Инструкция по инициализации проекта

* Чтобы Git начал отслеживать изменения в проекте, папку с файлами этого проекта нужно сделать Git-репозиторием (от англ. repository — «хранилище»).  Для этого следует переместиться в неё и ввести команду **git init** (от англ. initialize — «инициализировать»).

Например, создайте папку first-project и сделайте её Git-репозиторием: перейдите в неё с помощью команды cd и выполните git init.

* Если вы случайно сделали Git-репозиторием не ту папку, её можно «разгитить». Для этого нужно удалить скрытую подпапку .git.

```BASH
$ cd <папка с репозиторием> # перешли в папку

$ rm -rf .git # удалили подпапку .git
```

ключ -r (от англ. recursive — «рекурсивно») позволяет удалять папки вместе с их содержимым;
ключ -f (от англ. force — «заставить») избавит вас от вопросов вроде «Вы точно хотите удалить этот файл? А этот? И этот тоже?».

* Будьте осторожны: в подпапке .git хранится история изменений. Если удалить .git, то вся история проекта будет стёрта без возможности восстановления — останется только последняя версия файлов.

* После инициализации репозитория first-project запустите команду **git status** (от англ. status — «статус», «состояние») — она показывает текущее состояние репозитория.

  ## Добавляем файлы в репозиторий
* Команда **git add** позволяет подготовить файл к сохранению.
* Команда **git add --all** подготовит к сохранению сразу все файлы.
* С помощью **git add .** можно добавить в репозиторий текущую папку со всеми файлами.
* Коммит можно сделать с помощью команды **git commit**
Ключ -m позволяет присвоить коммиту сообщение. Помните, что такие сообщения должны быть информативными: чётко описывать изменения.
* Просмотреть историю коммитов — **git log**

  ## Связываем удаленный и локальный репозиторий

1.Создаем удаленный репозиторий на GitHub

2.Привязываем удалённый репозиторий к локальному: **git remote add**

Перейдите на страницу удалённого репозитория, выберите тип SSH и скопируйте URL. 
Откройте консоль, перейдите в каталог локального репозитория и введите команду git remote add (от англ. remote — «удалённый» и add — «добавить»).

```BASH
$ cd ~/dev/first-project
$ git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git 
```

*origin* (англ. «источник») — стандартный псевдоним, с помощью которого можно обращаться к главному удалённому репозиторию (обычно такой репозиторий один). Это значительно упрощает работу.

3.Убедимся, что репозитории связаны: **git remote -v**

```BASH
$ git remote -v
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (fetch)
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (push)
```
 В выводе вы должны увидеть две строчки, аналогичные тем, что показаны выше.
Флаг -v — короткая форма флага --verbose (англ. «подробный»). Он позволяет показать больше информации в выводе. 

  ## Синхронизируем ветки

Вы уже прошли весь «цикл коммита»: подготовили файлы с помощью git add, закоммитили их с комментарием командой git commit -m. Осталось загрузить содержимое локального репозитория на GitHub. За это отвечает команда **git push** (от англ. push — «толкать»).

В первый раз эту команду нужно вызвать с флагом -u и параметрами origin (имя удалённого репозитория) и main или master (название текущей ветки). 
Флаг -u свяжет локальную ветку с одноимённой удалённой. 
Как вы связывали локальный и удалённый репозитории в предыдущем уроке, так же и здесь нужно дополнительно связать ветки.
 
```BASH
$ git push -u origin main # Если команда приведёт к ошибке, попробуйте 
                          # заменить main на master.
```

При взаимодействии с удалёнными репозиториями Git выводит в консоль отладочную информацию: количество объектов (файлов), которые отправляются на сервер, информацию о прогрессе сжатия и записи и так далее.
Зайдите в репозиторий first-project на GitHub. Вы увидите, что в репозитории появились файлы с изменениями.

В дальнейшем при работе с удалённым репозиторием флаг -u можно опустить и писать просто git push.
Интерфейс GitHub позволяет удобно просмотреть все коммиты в репозитории, а также изменения в этих коммитах.


  ## Хеш — идентификатор коммита
Git преобразует информацию о коммитах с помощью алгоритма SHA-1 и для каждого из них рассчитывает уникальный идентификатор — **хеш**.
Хеш — основной идентификатор коммита и позволяет узнать его автора, дату и содержимое закоммиченных файлов.

Git хранит таблицу соответствий <u>хеш → информация о коммите</u>. Если вы знаете хеш, вы можете узнать всё остальное: автора и дату коммита и содержимое закоммиченных файлов. 
Можно сказать, что *хеш — основной идентификатор коммита*.

При работе с Git хеши будут встречаться вам регулярно. Их можно будет *передавать в качестве параметра* разным Git-командам, чтобы указать, с каким коммитом нужно произвести то или иное действие.
Все хеши и таблицу хеш → информация о коммите Git сохраняет в служебные файлы. Они находятся в скрытой папке **.git** в репозитории проекта.