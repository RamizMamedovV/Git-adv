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

вношу изменения для семинара - потом нужно удалить!!!