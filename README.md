//   работа с новой веткой
`git checkout -b <name of  new branch>`
`git push -u origin <name of the branch>`


//  просмотр доступных веток

`git remote show origin`

// для просмотра разницы без сливания 

`git fetch`

`git log <имя удаленной ветки для кот. выводится log> ^<имя локальнов ветки>`
/* ^ - означает, эквивалент записи --not т.е. выведи разницу коммитов, которых нет в 
 локальной ветке */

// просмотр         `git diff`
// для слияния разницы `git merge`

`git pull` - содержит обе эти команды `git fetch` и`git merge`

`git remote -v` покажет пути связанные с локальным репощиторием **fetch и **push
`git remote remove origin` удаление связи
`git remote set -url origin <url address>` установка адреса
`git remote set -url --push origin <address url>`
`git remote add <name repo>` - добавляем связь с ещё одним репозиторием и теперь nameOfGroupRepos покажет 2 группы **fetch и **push Затем для сохранения нужно набирать `git push -u <origin>[or new repoName]/<branchName> Также `git fetch --all` может затянуть с обеих репо. изменения в локальный и с помощью `git log <имя удаленной ветки для кот. выводится log> ^<имя локальнов ветки>`  просмотреть нужно ли их сливать в единию локальную, если да, то  `git merge <nameRepo>/<nameBranch>` командой слить их

    ТАК-ЖЕ МОЖНО ИХ ОБЪЕДИНИТЬ ПОД ЕДИНЫМ ИМЕНЕМ, чтобе одной командой "спушить"

`git remote add <nameOfGroupRepos> <address первого из репо>`, затеп 2 раза повторить команду
`git remote set-url --add --push <nameOfGroupRepos> <addressOfRepo1>`
`git remote set-url --add --push <nameOfGroupRepos> <addressOfRepo2>`, теперь команда `git remote -v`
покажет все эти пути. и с помощью команды оной, общей команды  `git push -u <имя общего репо> <name of the branch>`можно "запушить" в оба репозитория

                                    *лекция 2
`git diff <file.name>` - просмотр изменений в конкретном файле перед сохранением.
`git diff`             - просмотр всех изменений во всех файлах

`git log`              - просмотр истории коммитов
`git diff <hash1> <hash2> <fileName> - можно просмотреть разницу внесенных изменений в том порядке в котором введены hash1 и hash2

`git branch -a`         -используется для вывода списка всех веток в локальном репозитории, а также веток, которые доступны на удалённых репозиториях.

`git branch`            - Просмотреть только локальные ветки
`git branch -r`         - Просмотреть только удалённые ветки
`git checkout -b newBranch remotes/source/newBranch`    -Создать новую локальную ветку и отслеживать удалённую ветку

`git diff main origin/main` - Сравнить локальную ветку с удалённой

`git branch -d <branch_name>` - удаление веток. Команда удаляет локальную ветку только если все изменения из неё уже слиты в другую ветку или она больше не используется. Если ветка содержит несохранённые изменения, используйте флаг -D:

`git push <remote_name> --delete <branch_name>` - Для удаления ветки в удалённом репозитории

`git fetch --prune`             -Это удаляет все несуществующие ссылки на удалённые ветки

`git blame <fileName>`          -просмотр истории изменений в файле. Кем и когда были внесены


                            ** игнорирование изменений .gitignore

`создаем файл '.gitignore' и вносим в него :`
- имена файлов
- *.txt (например группу файлв)
- FOLDER/*.log папку с файлами 
- !FOLDER/spesialFile.log   исключаем из общего списка   


            **отмена несохраненных изменений

`git restore <fileName>` вернуться к исходному - сохраненному коммиту
`git restore --staged <fileName>` отмена индексирования(git add <fileName>) при двойном наборе этой команды - вернётся к исходному - сохраненному коммиту       
`git reset --hard` для возврата к исходному коммиту, если были внесены изменения сразу в несколько файлов. включая файлу находящиеся в "индексе"- после команды (git add)
`git clean -f`  удалит также и не отслеживаемые файлы- файлы вновь созданные и еще не имеющие коммитов

`git rm --cached <fileName>`  удалить из списка отслеживаемых (tracked) фалов. и затем можно  этот файл добавить в список .gitignore



                        ** отмена сохранённых изменений

`git checkout <hesh>`последовательность действий git log, затем выбираем нужный хеш и вставляем в команду: "git checkout <hesh> <fileName>" далее git предложит набрать команду: git restore --staged <fileName> и наш файл вернётся в состояние не индексированного файла. Далее нужно набрать git restore <fileName>. и этот коммит будет удалён

`git revert <hash>` можно редактировать коммит из списка (git log) и закомитить это изменение (зафиксировать отмену изменений как отдельный коммит.Удобно для сохранения истории изменений и когда отмена изменений должна быть "официальной".)                  

`git revert --no-commit <hash>` можно удалить несколько коммитов из списка (git log) и закомитить одним коммитом (Изменения отменяются и добавляются в рабочую директорию, без коммита.	Для объединения отмены с другими изменениями или проверки перед фиксацией.)                


                            **удаление (сброс) коммитов 
        
опнятие HEAD- увказатель на текущий коммит

`git reset --soft <hash>` отменяет последний коммит, но файл остается в состоянии индекированного
`git reset --mixed <hash>` или `git reset <hash>`(так как --mixed залано по умолчанию) отменяет последний коммит, но файл теперь - в состоянии НЕиндекированного

`git reset --hard <hash>` жеско удалит все изменения до указанного хеша


                            ** изменение содержимого последнего коммента
    
`git commit --amend -m'new comment'` 
`git commit --amend --no-edit`(прежде выполнить git add для индексации) если нужно добавить какое-то действие к последнему комменту без измененияя его содержимого


                            ** отмена слияния веток
находясь в ветке main делаем `git merge <branchName>` и затем решили отменить это слияние:
`git reset --merge <hash>(предидущего коммита, до которого нужно откатиться)`

`git merge --abort` набираем в случае, если возник неразрешенный конфликт, который нет нужды решать


                            ** откладывание изменений
`git stash` переводит в состояние спрятать изменения до востребования. можно использовать нескольео раз
и затем просмотреть списое `git stash list` и при необходимости вызывать их и коммитить с помощью команды `git stash pop` - венйт последний из "кучи" спрятанных изменений
`git stash drop` - удалить спрятанные изменения

МОЖЕТ ВОЗНИКНУТЬ КОНФЛИКТ ПРИ ВЫЗОВЕ `git stash pop`,  для разрешения конфликра (заранее сохранили локальнын изменения с помощью git add and git commit) тперь выбираем какой вариант оставить -возможно оба и затем индексуем git add . и закоммитим git commit -m'commit-text'
И ОБЯЗАТЕЛЬНО НУЖНО УДАЛИТЬ ИЗ GIT STASH LIST СПРЯТАННЫЕ ИЗМЕНЕНИЯ С ПОМОЩЬЮ `git stash drop`


                            ** перемещение изменений

`git merge <branchName>`  при слиянии ветки пропадут все коммиты сделанные на той ветке
`git rebase <branchName>` при слиянии сохранятся все коммиты
`git cherry-pick <hash>`  при слиянии сохранит выбранный коммит

