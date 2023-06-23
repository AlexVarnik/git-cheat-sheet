# Шпаргалка по Git

## 1. Инициализируем репозиторий

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

## 2. Добавляем файлы в репозиторий

`git add` - **Подготовить файлы к сохранению**

git add --all # подготовили к сохранению все файлы в репозитории

Добавлять файлы можно и по одному, без ключа --all.  
$ git add todo.txt  
$ git add readme.txt  
$ git status  

Также можно добавить текущую папку целиком — в этом случае все файлы в ней тоже будут добавлены.  
$ git add . # добавить всю текущую папку  
$ git status  

## 3. Делаем commit

`git commit` - **Выполнить commit**

Сделать коммит можно командой git commit c ключом -m (от англ. message — «сообщение»), который присваивает коммиту сообщение.

`$ git commit -m "Мой первый коммит!"`

**Разница между `git add` и `git commit`**: команда `git add` сообщает Git, какие именно файлы нужно сохранить и какую их версию. Затем с помощью команды `git commit` происходит само сохранение. 

## 4. Просматриваем историю коммитов

`git log` - **Просмотреть историю коммитов**.

```bash
$ git log
commit b47bf3eab5ff907c4a6ebe34b676d95bdc51d5df (HEAD -> main, git-describe-repo/main)
Author: AlexV <alexvarnik@gmail.com>
Date:   Fri Jun 23 10:34:51 2023 +0300

    `добавлены разделы до 7-го включительно`

commit 0341bd0bf797082b8f7cc5112df2d28116b80937
Author: AlexV <alexvarnik@gmail.com>
Date:   Thu Jun 22 14:58:56 2023 +0300

    создан четвертый раздел
```

- Git преобразует информацию о коммитах с помощью алгоритма SHA-1 и для каждого из них рассчитывает уникальный идентификатор — хеш.
- Хеш — основной идентификатор коммита и позволяет узнать его автора, дату и содержимое закоммиченных файлов.
- Все хеши, а также таблицу соответствий хеш → информация о коммите Git хранит в папке .git.

`git log --oneline` - Получить сокращённый лог.

В сокращённом логе выводятся сокращённые хеши — их можно использовать точно так же, как и полные.


## 5. GitHub
### 5.1. Регистрация

1. В правом верхнем углу главной страницы GitHub нажмите на Sign up (англ. «зарегистрироваться»).

2. На экране будут последовательно появляться поля для ввода.
2.1. Введите адрес электронной почты (англ. Enter your email).
2.2. Придумайте пароль (англ. Create a password).
2.3. Введите имя пользователя (англ. Enter a username).
3. Платформа спросит, хотите ли вы получать на почту рассылку с обновлениями и новостями (англ. Would you like to receive product updates and announcements via email?). Введите y, если хотите получать рассылку, или n, если не хотите.
Нажмите кнопку Continue (англ. «продолжить»).
4. Нажмите кнопку Continue (англ. «продолжить»).
5. GitHub предложит вам пройти капчу. Сделайте это.
6. После прохождения капчи нажмите Create account (англ. «создать аккаунт»).
7. Введите короткий код, который будет отправлен на указанный вами почтовый адрес.

### 5.2. Создание репозитория на GitHub

1. Зайдите в свой профиль по ссылке `https://github.com/username`.
2. Создайте репозиторий. Для этого перейдите на вкладку Repositories (англ. «репозитории»), а затем нажмите на зелёную кнопку New (англ. «новый») справа.
3. Укажите имя репозитория, выберите тип Публичный или Приватный, и нажмите кнопку `Create repository`.

### 5.3 Генерируем ssh-ключ

1. Для генерации ssh-пары можно использовать команды:  
`$ ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub"`  
или  
`$ ssh-keygen -t rsa -b 4096 -C "электронная почта, к которой привязан ваш аккаунт на GitHub"`

### 5.4 Привязываем SSH-ключ к GitHub

1. Скопируйте содержимое файла с публичным ключом в буфер обмена.  
`# скопировать содержимое ключа в буфер обмена:`  
`$ clip < ~/.ssh/id_rsa.pub`  
`# для ed25519:`  
`$ clip < ~/.ssh/id_ed25519.pub`  
Если clip не сработает, выведите содержимое файла с помощью cat ~/.ssh/id_rsa.pub или cat ~/.ssh/id_ed25519.pub и скопируйте вывод в буфер обмена из консоли.  
2. Перейдите на GitHub и выберите пункт __Settings__ (англ. «настройки») в меню аккаунта.
3. В меню слева нажмите на пункт __SSH and GPG keys__.
4. В открывшейся вкладке выберите __New SSH key__ (англ. «новый SSH-ключ»).
5. В поле Title (англ. «заголовок») напишите название ключа. Например, Personal key (англ. «личный ключ»).
6. В поле Key type (англ. «тип ключа») должно быть Authentication Key (англ. «ключ аутентификации»).
7. В поле Key скопируйте ваш ключ из буфера обмена.
8. Нажмите на кнопку __Add SSH key__ (англ. «добавить SSH-ключ»).
9. Проверьте правильность ключа с помощью следующей команды.
`$ ssh -T git@github.com.`  
Если это первый раз, когда вы используете Git, то появится предупреждение, на которое нужно ответить __`y`__.  
Затем на экране появится приветствие:  
`i %ВАШ_АККАУНТ%! You've successfully authenticated, but GitHub does not provide shell access.`

## 6. Связываем локальный и удалённый репозитории

### 6.1 Привязать удалённый репозиторий к локальному

`git remote add` - Привязать удалённый репозиторий к локальному.  

Перейдите на страницу удалённого репозитория, выберите тип SSH и скопируйте URL. Кнопка справа позволит сделать это мгновенно.

Откройте консоль, перейдите в каталог локального репозитория и введите команду git remote add (от англ. remote — «удалённый» и add — «добавить»).

$ cd ~/dev/first-project
$ git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git

Команде необходимо передать два параметра: имя удалённого репозитория и его URL. В качестве имени используйте слово origin. А URL вы скопировали со страницы удалённого репозитория.

`origin` (англ. «источник») — стандартный псевдоним, с помощью которого можно обращаться к главному удалённому репозиторию (обычно такой репозиторий один). Это значительно упрощает работу.

### 6.2 Убедиться, что репозитории связаны

`git remote -v` - Убедиться, что репозитории связаны.

$ git remote -v
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (fetch)
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (push)

В выводе вы должны увидеть две строчки, аналогичные тем, что показаны выше.
Флаг `-v` — короткая форма флага `--verbose` (англ. «подробный»). Он позволяет показать больше информации в выводе.

## 7. Синхронизируем локальный и удалённый репозитории

Самая первая ветка в репозитории появляется автоматически и называется main (англ. «основная») или master. Её имя нужно указывать при отправке коммитов на удалённый репозиторий или при получении их из него.

`git push` - Отправить изменения на удалённый репозиторий.

В первый раз эту команду нужно вызвать с флагом -u и параметрами origin (имя удалённого репозитория) и main или master (название текущей ветки). Флаг -u свяжет локальную ветку с одноимённой удалённой. Как вы связывали локальный и удалённый репозитории в предыдущем пункте, так же и здесь нужно дополнительно связать ветки.

$ git push -u origin main `# Если команда приведёт к ошибке, попробуйте заменить main на master.`

Появится экран с информацией. При взаимодействии с удалёнными репозиториями Git выводит в консоль отладочную информацию: количество объектов (файлов), которые отправляются на сервер, информацию о прогрессе сжатия и записи и так далее.

Если вы указывали кодовую фразу при настройке SSH-ключей, её нужно будет ввести.  
Зайдите в репозиторий first-project на GitHub. Вы увидите, что в репозитории появились файлы с изменениями.

## 8. Статусы файлов в Git

__Статусы `untracked/tracked`, `staged` и `modified`__
Одна из ключевых задач Git — отслеживать изменения файлов в репозитории. Для этого каждый файл помечается каким-либо статусом. Рассмотрим основные.
- __`untracked`__ (англ. «неотслеживаемый»)

Мы говорили, что новые файлы в Git-репозитории помечаются как untracked, то есть неотслеживаемые. Git «видит», что такой файл существует, но не следит за изменениями в нём. У untracked-файла нет предыдущих версий, зафиксированных в коммитах или через команду git add.

- __`staged`__ (англ. «подготовленный»)

  После выполнения команды git add файл попадает в staging area (от англ. stage — «сцена», «этап [процесса]» и area — «область»), то есть в список файлов, которые войдут в коммит. В этот момент файл находится в состоянии staged.
  В одном из предыдущих уроков мы сравнили коммит с фотографией. Можно развить эту аналогию и сказать, что команда git add добавляет персонажей (текущее содержимое файла или нескольких файлов) на сцену (англ. stage) для общей фотографии, а git commit делает снимок всей сцены целиком. 
  
```  Staging area, index и cache
Staging area также называют index (англ. «каталог») или cache (англ. «кеш»), а состояние файла staged иногда называют indexed или cached.
Все три варианта могут встречаться в документации и в качестве флагов команд Git. А также в интернете — например, в вопросах и ответах на сайте Stack Overflow.
```

- __`tracked`__ (англ. «отслеживаемый»)

Состояние tracked — это противоположность untracked. Оно довольно широкое по смыслу: в него попадают файлы, которые уже были зафиксированы с помощью git commit, а также файлы, которые были добавлены в staging area командой git add. То есть все файлы, в которых Git так или иначе отслеживает изменения.

- __`modified`__ (англ. «изменённый»)

Состояние modified означает, что Git сравнил содержимое файла с последней сохранённой версией и нашёл отличия. Например, файл был закоммичен и после этого изменён.

``` Для файлов в состояниях staged и modified обычно не указывают,
    что они также tracked, потому что это состояние подразумевается.
```

- Статусом `untracked` помечается файл, о существовании которого Git знает, но не следит за изменениями в нём. Этот статус — противоположность `tracked`, в который попадают все файлы, отслеживаемые Git.
- Файл переходит в статус `staged` после выполнения `git add`.
- Статус `modified` означает, что файл был изменён.
- Большинство файлов в проектах «шагает» по следующему циклу: «изменён» → «добавлен в список на коммит» → «закоммичен» → «изменён» → и так далее.






