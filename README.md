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
`git remote set -url origin <url address> установка адреса
`git remote set -url --push origin <address url>
`git remote add <name repo> - добавляем связь с ещё одним репозиторием
    и теперь nameOfGroupRepos покажет 2 группы **fetch и **push
    Затем для сохранения нужно набирать `git push -u <origin>[or new repoName]/<branchName>
    Также `git fetch --all` может затянуть с обеих репо. изменения в локальный
    и с помощью `git log <имя удаленной ветки для кот. выводится log> ^<имя локальнов ветки>`
    просмотреть нужно ли их сливать в единию локальную, если да, то 
    `git merge <nameRepo>/<nameBranch>` командой слить их

    ЕАК-ЖЕ МОЖНО ИХ ОБЪЕДИНИТЬ ПОД ЕДИНЫМ ИМЕНЕМ, чтобе одной командой "спушить"

`git remote add <nameOfGroupRepos> <address первого из репо>`, затеп 2 раза повторить команду
`git remote set-url --add --push <nameOfGroupRepos> <addressOfRepo1>`
`git remote set-url --add --push <nameOfGroupRepos> <addressOfRepo2>`, теперь команда `git remote -v`
покажет все эти пути. и с помощью команды оной, общей команды  `git push -u <имя общего репо> <name of the branch>`можно "запушить" в оба репозитория

                                    *лекция 2
`git diff <file.name>` - просмотр изменений в конкретном файле перед сохранением.
`git diff`             - просмотр всех изменений во всех файлах

`git log`              - просмотр истории коммитов
`git diff <hash1> <hash2> <fileName> - можно просмотреть разницу внесенных изменений в том порядке 
                                     в котором введены hash1 и hash2

`git branch -a`         -используется для вывода списка всех веток в локальном репозитории,
                        а также веток, которые доступны на удалённых репозиториях.

`git branch`            - Просмотреть только локальные ветки
`git branch -r`         - Просмотреть только удалённые ветки
`git checkout -b newBranch remotes/source/newBranch`    -Создать новую локальную ветку 
                            и отслеживать удалённую ветку
`git diff main origin/main` - Сравнить локальную ветку с удалённой

`git branch -d <branch_name>` - удаление веток. Команда удаляет локальную ветку только
                если все изменения из неё уже слиты в другую ветку или она больше не используется.
                Если ветка содержит несохранённые изменения, используйте флаг -D:
`git push <remote_name> --delete <branch_name>` - Для удаления ветки в удалённом репозитории
`git fetch --prune`             -Это удаляет все несуществующие ссылки на удалённые ветки