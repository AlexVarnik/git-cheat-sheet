# Шпаргалка по Git

## 1. Инициализируем репозиторий

--- 

`git init` - **Сделать папку репозиторием**

$ cd ~/dev/first-project # перешли в нужную папку

$ git init # создали репозиторий

Можно создать папку в любом месте на компьютере. Но не забывать менять в наших примерах путь ~/dev/first-project на тот, который ведёт к вашей папке.  _Не рекомендуется создавать репозиторий Git внутри другого Git-репозитория._

--- 

`rm -rf .git` - **«Разгитить» папку, если что-то пошло не так**

$ cd <папка с репозиторием> # перешли в папку

$ rm -rf .git # удалили подпапку .git

---
`git status` - **Проверить состояние репозитория**