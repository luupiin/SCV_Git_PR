![Logo](30c29ce4cc08523ecc6e1f205bc207d0.jpeg)


# Работа с Git и GitHub

## 1. Проверка наличия установленного Git
В терминале выполнить команду `git --version`.
Если Git установлен, появится сообщение с информацией о версии программы. Иначе будет сообщение об ошибке.

## 2. Установка Git 
Загружаем последнюю версию файла с сайта  https://git-scm.com/downloads.
Устанавливаем с настройками по умолчанию

## 3. Настройка Git
При первом использование Git необходимо представиться. Для этого в терминале нужно ввести в терминале две команды:
```
git config --global user.name «Ваше имя английскими буквами»
git config --global user.email ваша почта@example.com
```

## 4. Инициализация репозитория 
Для создания репозитория необходимо выполнить команду `git init` в папке с репозиторием и у вас создаться папка репозиторий.Теперь Git отслеживает изменения файлов вашего проекта.

![gitinit](gitinit.png)

## 5. Команды изменений в репозитории

* `git add <Название проекта>` или `git add --all`   -Добавление файла(файлов) к следующему коммиту.
![gitadd](gitadd.png)

*  `git status`   -Получить информацию от Git о его текущем состоянии .
![status](status.png)
* `git commit -m "NameCommit"`  -Создание коммита.
![commit](commit.png)
* `git diff `  -Разница между текущим файлом и последним файлом занесенным в коммит.


![diff](diff.png)

## 6. Git log История коммитов

Для вывода истории коммитов нам понадобится команда `git log`.Она выведет всю историю коммитов с их Хеш-кодами.Команда `git log` используется для просмотра истории коммитов, начиная с самого свежего и уходя к истокам проекта. По умолчанию, она показывает лишь историю текущей ветки, но может быть настроена на вывод истории других, даже нескольких сразу, веток.

![log](gitlog.png)

## 7. Переключение между ветками 
Команда `git checkout ` позволяет перемещаться между ветками.При переключении ветки происходит обновление файлов в рабочем каталоге в соответствии с версией, хранящейся в этой ветке, а Git начинает записывать все новые коммиты в этой ветке.Так же для возврата в последнюю ветку вам понадобится команда:
* `git checkout master`.

![checkout](gitcheckout.png)


## 8. Ингорирование файлов 
Для того, чтобы исключить из отслеживания в репозитории определённые файлы и папки необходимо создать там файл `.gitignore` и записать в него их название или шаблоны, соответствующие таким файлам или папкам.Для обозначение списка файлов можно записать их в 
"` *.<расширение файла> `"

![gitignore](gitignore.png)

## 9. Создание веток Git

Почти каждая система контроля версий в той или иной форме поддерживает ветвление. Используя ветвление, Вы отклоняетесь от основной линии разработки и продолжаете работу независимо от неё, не вмешиваясь в основную линию.Ветка в Git — это простой перемещаемый указатель на один из таких коммитов. 

По умолчанию, имя основной ветки в Git — `master`. Как только вы начнёте создавать коммиты, ветка `master` будет всегда указывать на последний коммит. Каждый раз при создании коммита указатель ветки `master` будет передвигаться на следующий коммит автоматически.

Для создания новой ветки нам понадобится команда:
```
git branch <имя новой ветки>
```
В Git есть возможность создать большое количество веток и просмотр всех веток можно осуществить с помощью команды:
```
git branch
```
Текущая ветка в которой вы сейчас находитесь будет отмечена звездочкой.


### Пример:
Сейчас вы находить в ветке `*master` 

![gitbranch](gitbranch.png)

Так как мы создали новые ветки и находимся в ветке `*master`, нам нужно переключить на новую ветку `*Branch_name`,чтобы уже работать на данной ветке нам понадобится команда: 
* `git checkout Branch_name`

## 10.Слияние веток 

Процедура объединения веток называется слияние (merge). Для слияния текущей ветки с какой-либо другой используется команда. `git merge имя_ветки`. В результате выполнения этой команды в текущей ветке появится новый коммит. Этот коммит будет иметь два предка – последние коммиты обоих веток, участвующих в слиянии.Содержимое этого коммита будет включать содержимое коммитов обоих веток.

### Пример:
![merge](gitmerge.png)


## 11. Конфликты при слиянии.

При слиянии может возникнуть ситуация, когда фрагмент в каком-либо файле проекта в различных ветках отредактирован по разному. Такая ситуация называется конфликт (conflict).

В случае возникновения конфликтов git заносит в создаваемый при объединении коммит файл, содержащий текст обоих версий. Начало конфликтного фрагмента помечается строкой, начинающиеся с символов <<<<<<< и содержащей имя первой ветки, а заканчивается строкой, начинающиеся с символов >>>>>>> и содержащей имя вливаемой ветки. Версии из каждой ветки разделяются строкой с символами =======. Такой файл получает статус не объединенный (unmerged).

### Пример:

![conflicts](conflict.png)

Когда у вас покажется данное сообщение вам нужно принять решение нажав на одну из предложенных кнопок:
* Accept Current Change
* Accept Incoming Change 
* Accept Both Changes
* Compare Changes 

После данного выбора вам нужно будет произвести коммит с помощью команды 
* `git commit -a -m <Название коммита>`


## 12. Удаление веток

Если ветка потеряла свою актуальность, мы можем её удалить локально при помощи команды `git branch -d название ветки`. Здесь важно отметить, что вы не можете удалить ветку, если вы сейчас в ней — обязательно нужно переключить её.

* Параметр *-d* является в Git **-delete**, который удаляет ветвь только в том случае, если она уже была полностью объединена с веткой `master`.

Если же удаляемая вами ветка не была полностью объединена с веткой `master` (не был произведен коммит ветки, которую мы собираемся удалить), то вам понадобится команда `git branch -D название ветки` 

* Параметр *-D* является командой **--delete--force**,который удаляет ветку в независимости от ее объединенного статуса

![delete](gitbranchdelete.png)

## 13. Работа с удаленными репозиториями

Удалённые репозитории представляют собой версии вашего проекта, сохранённые в интернете или ещё где-то в сети. У вас может быть несколько удалённых репозиториев, каждый из которых может быть доступен для чтения или для чтения-записи. Взаимодействие с другими пользователями предполагает управление удалёнными репозиториями, а также отправку и получение данных из них. Управление репозиториями включает в себя как умение добавлять новые, так и умение удалять устаревшие репозитории, а также умение управлять различными удалёнными ветками, объявлять их отслеживаемыми или нет и так далее.

1.  `git clone`

Команда `git clone` используется для создания копии определенного репозитория или ветви внутри репозитория.

Когда вы клонируете репозиторий, вы не получаете один файл, как это может быть в других централизованных системах контроля версий. При клонировании с помощью Git вы получаете весь репозиторий - все файлы, все ветви и все коммиты.

2. `git push`

`git push` обновляет удаленную ветку локальными фиксациями. Это одна из четырех команд в Git, которая запрашивает взаимодействие с удаленным репозиторием. Вы также можете думать о `git push` как о обновлении или публикации.

### Как использовать git push?

После того, как вы внесете и зафиксируете изменения локально, вы можете поделиться ими с удаленным репозиторием с помощью `git push`. Передача изменений на удаленный сервер делает ваши коммиты доступными для других пользователей, с которыми вы, возможно, сотрудничаете. Это также обновит все открытые запросы на извлечение в ветке, над которой вы работаете.



