# Git-Commands

### Настройка
| Command | Description |
| --- | --- |
| `git config --global user.name "Antonezka"` | Настройка имени для коммитов |
| `git config --global user.email "Antonezka@mail.ru"` | e-mail для коммита |

### Создание репозитория и файла
| Command | Description |
| --- | --- |
| `git init` | Инициализация локального репозитория в текщей директории |
| `git init folder-name` | Инициализация локального репозитория в указанной директории |

### Клонирование репозитория
| Command | Description |
| --- | --- |
| `git clone ssh://git@github.com/[username]/[repository-name].git` | Создание локальной копии удаленного репозитория в одноименную директорию|
| `git clone ssh://git@github.com/[username]/[repository-name].git FolderName` | Создание локальной копии удаленного репозитория в директорию "FolderName"|
| `git clone ssh://git@github.com/[username]/[repository-name].git .` | Создание локальной копии удаленного репозитория в текущую директорию|



### Просмотр содержимого папки
| Command | Description |
| --- | --- |
| `pwd` | Вывод текущего пути (сокращение от PRINT WORK DIRECTORY) |
| `ls` | Показать содержимое папки |
| `ls -l` | Отображение расширенной информации о файлах и папках |
| `ls -a` | то же, но показывать и скрытые файлы и папки |
| `ls -a -1` | то же, но в один столбец |
| `ls -hF -1 --sort=extension` | Отображение содержимого папки «красиво, в один столбец» |
| `ls build/css` | Отображение содержимого папки ТЕКУЩАЯ_ПАПКА/build/css |
| `ls /d/projects` | Отображение содержимого папки D:/projects |

### Перемещение по файловой системе
| Command | Description |
| --- | --- |
| `cd projects` | Переход в папку projects, которая есть текущей папке |
| `cd /d/projects` | Переход в папку projects, расположенную по адресу D:/projects |
| `cd /c/Program\ Files` | Переход в папку C/:Program Files |
| `cd .` | Текущая директория |
| `cd ..` | Переход к родительской папке |
| `cd ~` | Домашняя директория |
| `cd -` | Переход к последней рабочей папке |

### Создание папок и файлов
```
mkdir project                        # создать папку с именем «project»
mkdir project project/css project/js # создать несколько папок
mkdir -p project/{css,js}            # то же, что выше

touch index.html                     # создать файл
touch index.html css/style.css js/script.js # создать файлы (папки css/ и js/ должны уже существовать)
nano index.html                  		 # создать файл и открыть через редактор nano для его изменения
```

### Копирование файлов
```
cp index.html catalog.html # копирование файла index.html в тот же каталог с переименованием в catalog.html
cp index.html old/         # копирование файла index.html в папку old/ (все произойдет в текущей папке)
cp temp/ temp2/ -r         # дублирование каталога
```

### Переименование или перемещение файлов
```
mv index.html old              # перемещение файла в папку
mv index.html old/new_name.txt # перемещение файла в папку с переименованием файла
mv order.txt orderNew.txt      # переименовать файл
```

### Удаление папок и файлов
```
rm ghost.png             # удалить файл
rm -rf old               # удалить папку и всё из нее
```

### Алиасы
Для команд можно создавать алиасы (синонимы). Для этого в папке C:/Users/ИМЯ_ПОЛЬЗОВАТЕЛЯ/.bashrc (Windows) нужно вписать строки, наподобие alias pro='cd /d/projects' (одна строка в файле — один алиас).
```
alias                 # отобразит алиасы, которые уже заданы в системе   
alias c='clear'       # создаст алиас который будет очищать консоль
unalias c             # удалит алиас " c "
unalias -a            # удалит все записанные алиасы
git config --global alias.br branch # создат глобальный алиас br
```

### Просмотр изменений
```
git status              # показать состояние репозитория (отслеживаемые, изменённые, новые файлы и пр.)
git diff                # сравнить рабочую директорию и индекс (неотслеживаемые файлы ИГНОРИРУЮТСЯ)
git diff --color-words  # сравнить рабочую директорию и индекс, показать отличия в словах (неотслеживаемые файлы ИГНОРИРУЮТСЯ)
git diff index.html     # сравнить файл из рабочей директории и индекс
git diff HEAD           # сравнить рабочую директорию и коммит, на который указывает HEAD (неотслеживаемые файлы ИГНОРИРУЮТСЯ)
git diff --staged       # сравнить индекс и коммит с HEAD
git diff master feature # посмотреть что сделано в ветке feature по сравнению с веткой master
git diff --name-only master feature # посмотреть что сделано в ветке feature по сравнению с веткой master, показать только имена файлов
git diff master...feature # посмотреть что сделано в ветке feature с момента (коммита) расхождения с master
```

### Добавление изменений в индекс
```
git add .        # добавить в индекс все новые, изменённые, удалённые файлы из текущей директории и её поддиректорий
git add text.txt # добавить в индекс указанный файл (был изменён, был удалён или это новый файл)
git add -i       # запустить интерактивную оболочку для добавления в индекс только выбранных файлов
git add -p       # показать новые/изменённые файлы по очереди с указанием их изменений и вопросом об отслеживании/индексировании
```

### Удаление изменений из индекса
```
git reset            # убрать из индекса все добавленные в него изменения (в рабочей директории все изменения сохранятся), антипод git add
git reset readme.txt # убрать из индекса изменения указанного файла (в рабочей директории изменения сохранятся)
```

### Отмена изменений
```
git checkout text.txt      # ОПАСНО: отменить изменения в файле, вернуть состояние файла, имеющееся в индексе
git reset --hard           # ОПАСНО: отменить изменения; вернуть то, что в коммите, на который указывает HEAD (незакомиченные изменения удалены из индекса и из рабочей директории, неотслеживаемые файлы останутся на месте)
git clean -df              # удалить неотслеживаемые файлы и директории
```

### Коммиты
```
git commit -m "Name of commit"    # зафиксировать в коммите проиндексированные изменения (закоммитить), добавить сообщение
git commit -a -m "Name of commit" # проиндексировать отслеживаемые файлы (ТОЛЬКО отслеживаемые, но НЕ новые файлы) и закоммитить, добавить сообщение
```

### Отмена коммитов и перемещение по истории
Если коммиты были отправлены в удаленный репозиторий
```
git revert HEAD --no-edit    # создать новый коммит, отменяющий изменения последнего коммита без запуска редактора сообщения
git revert b9533bb --no-edit # то же, но отменяются изменения, внесённые коммитом с указанным хешем (b9533bb)
```
Если коммиты НЕ были отправлены в удаленный репозиторий
```
# ВНИМАНИЕ! Опасные команды, можно потерять незакоммиченные изменения
git commit --amend -m "Название"  # «перекоммитить» изменения последнего коммита, заменить его новым коммитом с другим сообщением (сдвинуть текущую ветку на один коммит назад, сохранив рабочую директорию и индекс «как есть», создать новый коммит с данными из «отменяемого» коммита, но новым сообщением)
git reset --hard @~      # передвинуть HEAD (и ветку) на предыдущий коммит, рабочую директорию и индекс сделать такими, какими они были в момент предыдущего коммита
git reset --hard 75e2d51 # передвинуть HEAD (и ветку) на коммит с указанным хешем, рабочую директорию и индекс сделать такими, какими они были в момент указанного коммита
git reset --soft @~      # передвинуть HEAD (и ветку) на предыдущий коммит, но в рабочей директории и индексе оставить все изменения
git reset --soft @~2     # то же, но передвинуть HEAD (и ветку) на 2 коммита назад
git reset @~             # передвинуть HEAD (и ветку) на предыдущий коммит, рабочую директорию оставить как есть, индекс сделать таким, каким он был в момент предыдущего коммита (удобнее, чем git reset --soft @~, если индекс нужно задать заново)
# Почти как git reset --hard, но безопаснее: не получится потерять изменения в рабочей директории
git reset --keep @~      # передвинуть HEAD (и ветку) на предыдущий коммит, сбросить индекс, но в рабочей директории оставить изменения, если возможно (если файл с изменениями между коммитами менялся, будет выдана ошибка и переключение не произойдёт)
```

### Временно переключиться на другой коммит
```
git checkout b9533bb # переключиться на коммит с указанным хешем (переместить HEAD на указанный коммит, рабочую директорию вернуть к состоянию, на момент этого коммита)
git checkout master  # переключиться на коммит, на который указывает master (переместить HEAD на коммит, на который указывает master, рабочую директорию вернуть к состоянию на момент этого коммита)
```

### Переключиться на другой коммит и продолжить работу с него
```
git checkout -b new-branch 5589877   # создать ветку new-branch, начинающуюся с коммита c хешем 5589877 (переместить HEAD  на указанный коммит, рабочую директорию вернуть к состоянию, на момент этого коммита, создать указатель на этот коммит (ветку) с указанным именем)
```

### Восстановление изменений
```
git checkout 5589877 index.html  # восстановить в рабочей директории указанный файл на момент указанного коммита (и добавить это изменение в индекс) (git reset index.html для удаления из индекса, но сохранения изменений в файле)
```

### Копирование коммита (перенос коммитов)
```
git cherry-pick 5589877          # скопировать на активную ветку изменения из указанного коммита, закоммитить эти изменения
git cherry-pick master~2..master # скопировать на активную ветку изменения из master (2 последних коммита)
git cherry-pick -n 5589877       # скопировать на активную ветку изменения из указанного коммита, но НЕ КОММИТИТЬ (подразумевается, что мы сами потом закоммитим)
git cherry-pick master..feature  # скопировать на активную ветку изменения из всех коммитов ветки feature с момента её расхождения с master (похоже на слияние веток, но это копирование изменений, а не слияние), закоммитить эти изменения; это может вызвать конфликт
git cherry-pick --abort    # прервать конфликтный перенос коммитов
git cherry-pick --continue # продолжить конфликтный перенос коммитов (сработает только после решения конфликта)
```

### Удаление файла
```
git rm text.txt    # удалить отслеживаемый неизменённый файл и проиндексировать это изменение
git rm -f text.txt # удалить отслеживаемый изменённый файл и проиндексировать это изменение
git rm -r log/     # удалить всё содержимое отслеживаемой директории log/ и проиндексировать это изменение
git rm ind*        # удалить все отслеживаемые файлы с именем, начинающимся на «ind» в текущей директории и  проиндексировать это изменение
git rm --cached readme.txt # удалить из отслеживаемых индексированный файл (ФАЙЛ ОСТАНЕТСЯ НА МЕСТЕ) (часто используется для нечаянно добавленных в отслеживаемые файлов)
```

### Перемещение/переименование файлов
```
git mv text.txt test_new.txt # переименовать файл «text.txt» в «test_new.txt» и проиндексировать это изменение
git mv readme_new.md folder/ # переместить файл readme_new.md в директорию folder/ (должна существовать) и проиндексировать это изменение
```

### История коммитов
```
git log master             # показать коммиты в указанной ветке
git log -2                 # показать последние 2 коммита в активной ветке
git log -2 --stat          # показать последние 2 коммита и статистику внесенных ими изменений
git log -p -22             # показать последние 22 коммита и внесенную ими разницу на уровне строк
git log --graph -10        # показать последние 10 коммитов с ASCII-представлением ветвления
git log --since=2.weeks    # показать коммиты за последние 2 недели
git log --after '2018-06-30' # показать коммиты, сделанные после указанной даты
git log index.html         # показать историю изменений файла index.html (только коммиты)
git log -5 index.html      # показать историю изменений файла index.html, последние 5 коммитов (только коммиты)
git log -p index.html      # показать историю изменений файла index.html (коммиты и изменения)
git log -G'myFunction' -p  # показать все коммиты, в которых менялись строки с myFunction (в кавычках регулярное выражение)
git log -L '/<head>/','/<\/head>/':index.html # показать изменения от указанного до указанного регулярных выражений в указанном файле
git log --grep fix         # показать коммиты, в описании которых есть буквосочетание fix (регистрозависимо,
только коммиты текущей ветки)
git log --grep fix -i      # показать коммиты, в описании которых есть буквосочетание fix (регистроНЕзависимо,
только коммиты текущей ветки)
git log --grep 'fix(ing|me)' -P # показать коммиты, в описании которых есть совпадения для регулярного выражения 
(только коммиты текущей ветки)
git log --pretty=oneline   # однострочный вывод истории
git log --pretty=oneline --author=<your name>  # показать коммиты определенного пользователя
git log --pretty=format:"%h - %an, %ar : %s" -4 # показать последние 4 коммита с форматированием выводимых данных
git log --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short # мой формат вывода, висящий на алиасе оболочки
git log master..branch_99  # показать коммиты из ветки branch_99, которые не влиты в master
git log branch_99..master  # показать коммиты из ветки master, которые не влиты в branch_99
git log master...branch_99 --boundary -- graph # показать коммиты из указанных веток, начиная с их расхождения
(коммит расхождения будет показан)
```
```
--pretty="..." — определяет формат вывода.
%h — укороченный хэш коммита
%d — дополнения коммита («головы» веток или теги)
%ad — дата коммита
%s — комментарий
%an — имя автора
--graph — отображает дерево коммитов в виде ASCII-графика
--date=short — сохраняет формат даты коротким и симпатичным
```
```
git show 60d6582           # показать изменения из коммита с указанным хешем
git show HEAD~             # показать данные о предыдущем коммите в активной ветке
git show @~                # аналогично предыдущему
git show HEAD~3            # показать данные о коммите, который был 3 коммита назад
git show my_branch~2       # показать данные о коммите, который был 2 коммита назад в указанной ветке
git show @~:index.html     # показать контент указанного файла на момент предыдущего (от HEAD) коммита
git show :/"подвал"        # показать самый новый коммит, в описании которого есть указанное слово (из любой ветки)
```
```
gitk                       # показывает историю изменений
```

### История изменений указателей (веток, HEAD)
```
git reflog -20             # показать последние 20 изменений положения указателя HEAD
git reflog --format='%C(auto)%h %<|(20)%gd %C(blue)%cr%C(reset) %gs (%s)' -20 # то же, но с указанием давности действий
```

### Ветки
```
git branch                 # показать список веток
git branch -v              # показать список веток и последний коммит в каждой
git branch new_branch      # создать новую ветку с указанным именем на текущем коммите
git branch new_branch 5589877 # создать новую ветку с указанным именем на указанном коммите
git branch -f master 5589877  # переместить ветку master на указанный коммит
git branch -f master master~2 # переместить ветку master на 2 коммита назад
git checkout new_branch    # перейти в указанную ветку
git checkout -b new_branch # создать новую ветку с указанным именем и перейти в неё
git checkout -B master 5589877 # переместить ветку с указанным именем на указанный коммит и перейти в неё
git merge hotfix           # влить в ветку, в которой находимся, данные из ветки hotfix
git merge hotfix -m "Горячая правка" # влить в ветку, в которой находимся, данные из ветки hotfix (указано сообщение коммита слияния)
git merge hotfix --log     # влить в ветку, в которой находимся, данные из ветки hotfix, показать редактор описания коммита, добавить в него сообщения вливаемых коммитов
git merge hotfix --no-ff   # влить в ветку, в которой находимся, данные из ветки hotfix, запретить простой сдвиг указателя, изменения из hotfix «останутся» в ней, а в активной ветке появится только коммит слияния
git branch -d hotfix       # удалить ветку hotfix (используется, если её изменения уже влиты в главную ветку)
git branch --merged        # показать ветки, уже слитые с активной
git branch --no-merged     # показать ветки, не слитые с активной
git branch -a              # показать все имеющиеся ветки (в т.ч. на удаленных репозиториях)
git branch -m old_branch_name new_branch_name # переименовать локально ветку old_branch_name в new_branch_name
git branch -m new_branch_name # переименовать локально ТЕКУЩУЮ ветку в new_branch_name
git push origin :old_branch_name new_branch_name # применить переименование в удаленном репозитории
git branch --unset-upstream # завершить процесс переименования
```

### Теги
```
git tag v1.0.0               # создать тег с указанным именем на коммите, на который указывает HEAD
git tag -a -m 'В продакшен!' v1.0.1 master # создать тег с описанием на том коммите, на который смотрит ветка master
git tag -d v1.0.0            # удалить тег с указанным именем(ами)
git tag -n                   # показать все теги, и по 1 строке сообщения коммитов, на которые они указывают
git tag -n -l 'v1.*'         # показать все теги, которые начинаются с 'v1.*'
```

### Временное сохранение изменений без коммита
при ошибке Cannot pull with rebase: you have unstaged changes
```
git stash        # временно сохранить незакоммиченные изменения и убрать их из рабочей директории
git stash pop    # вернуть сохраненные командой git stash изменения в рабочую директорию (apply + drop для всех файлов в stash)
git stash list   # посмотреть количество отложенных временно сохраненных незакоммиченных изменений
git stash show   # посмотреть последнее отложенное временно сохраненное незакоммиченное изменение
git stash apply  # вернуть последнее отложенное временно сохраненное незакоммиченное изменение в рабочую директорию, но в stash ОНО ОСТАНЕТСЯ
git stash drop   # удалить последнее изменение, добавленное в stash
git stash clear  # очистить stash
```

### Удалённые репозитории
```
git remote -v              # показать список удалённых репозиториев, связанных с локальным
git remote remove origin   # убрать привязку удалённого репозитория с сокр. именем origin
git remote add origin https://github.com:nicothin/test.git # добавить удалённый репозиторий (с сокр. именем origin)
с указанным URL
git remote rm origin       # удалить привязку удалённого репозитория
git remote show origin     # получить данные об удалённом репозитории с сокращенным именем origin
git fetch origin           # скачать все ветки с удаленного репозитория (с сокр. именем origin),
но не сливать со своими ветками
git fetch origin master    # то же, но скачивается только указанная ветка
git checkout --track origin/github_branch # создать локальную ветку github_branch (данные взять из удалённого репозитория
с сокр. именем origin, ветка github_branch) и переключиться на неё
git push origin master     # отправить в удалённый репозиторий (с сокр. именем origin) данные своей ветки master
git push --tags						 # отправка тэгов на удаленный репозиторий
git pull origin            # влить изменения с удалённого репозитория (все ветки) (аналог merge)
git pull origin master     # влить изменения с удалённого репозитория (только указанная ветка)
git pull --rebase origin master     # влить изменения с удалённого репозитория (только указанная ветка) (аналог rebase)
```

### Конфликт слияния
```
git merge feature                # влить в активную ветку изменения из ветки feature
git merge-base master feature    # показать хеш последнего общего коммита для двух указанных веток
git checkout --ours index.html   # оставить в конфликтном файле (index.html) состояние ветки,
В КОТОРУЮ мы вливаем (в примере — из ветки master)
git checkout --theirs index.html # оставить в конфликтном файле (index.html) состояние ветки,
ИЗ КОТОРОЙ мы вливаем (в примере — из ветки feature)
git checkout --merge index.html  # показать в конфликтном файле (index.html) сравнение содержимого сливаемых веток
(для ручного редактирования)
git checkout --conflict=diff3  --merge index.html # показать в конфликтном файле (index.html) сравнение содержимого
сливаемых веток плюс то, что было в месте конфликта в коммите, на котором разошлись сливаемые ветки
git reset --hard  # прекратить это прерванное слияние, вернуть рабочую директорию и индекс как было в момент коммита,
на который указывает HEAD, а я пойду немного поплачу
git reset --merge # прекратить это прерванное слияние, но оставить изменения, не закоммиченные до слияния (для случая,
когда слияние делается не на чистом статусе)
git reset --abort # то же, что и строкой выше
```

### «Перенос» ветки
```
git rebase master # перенести все коммиты (создать их копии) активной ветки так, будто активная ветка ответвилась от master
на нынешней вершине master (часто вызывает конфликты)
git rebase --onto master feature # перенести коммиты активной ветки на master, начиная с того места, в котором активная ветк
а отделилась от ветки feature
git rebase --abort # прервать конфликтный rebase, вернуть рабочую директорию и индекс к состоянию до начала rebase
git rebase --continue # продолжить конфликтный rebase (сработает только после разрешения конфликта и индексации
такого разрешения)

#ОТМЕНА rebase
git reflog feature -2        # смотрим лог перемещений ветки, которой делали rebase (в этом примере — feature),
видим последний коммит ПЕРЕД rebase, на него и нужно перенести указатель ветки
git reset --hard feature@{1} # переместить указатель ветки feature на один коммит назад, обновить рабочую директорию и индекс
```

### Разное
```
clear                 # очистить консоль
df -h                 # показать статистику использования пространства на дисках
grep -i -n --color 'carousel' index.html css/style.css     # найти слово carousel в двух указанных файлах 
                      (с игнором регистра), вывести строки с этим словом и номера строк (искомое слово подсветить)
grep word -r project  # найти слово word во всех файлах в папке project
find . -iname '*ind*' # найти в текущей папке (и подпапках) все файлы, имена которых содержат ind и показать списком
ls -a >> file.txt     # записать в file.txt результат вывода команды ls -a
ls src/less/mixins    # показать содержимое папки с указанным путем без перехода в неё
echo  "Some text"     # вывод текста в консоль 
chmod +x ./fileName   # сделать файл исполняемым 
whoami                # выводит имя пользователя 
git blame README.md --date=short -L 5,8 # показать строки 5-8 указанного файла и коммиты, в которых строки были добавлены
git archive -o ./project.zip HEAD # создать архив с файловой структурой проекта по указанному пути (состояние репозитория, соответствующее указателю HEAD)
.gitignore						# создаtn файл с регулярными выражениями для untracked files
```

# Vim-Commands
```
# Нажатия кнопок
ESC     — переход в командный режим
i       — переход в режим редактирования текста
ZQ (зажат Shift, поочередное нажатие) — выход без сохранения
ZZ (зажат Shift, поочередное нажатие) — сохранить и выйти

# Нажатия кнопок
ESC     — переход в командный режим
i       — переход в режим редактирования текста
ZQ (зажат Shift, поочередное нажатие) — выход без сохранения
ZZ (зажат Shift, поочередное нажатие) — сохранить и выйти

# Ввод в командном режиме
:q!             — выйти без сохранения
:wq             — сохранить файл и выйти
:w filename.txt — сохранить файл как filename.txt
```
