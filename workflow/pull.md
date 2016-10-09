# Как сделать pull request

Перед тем как сделать свой первый пулл, мы рекомендуем пройти курс по основам Git на [GitHowTo](http://githowto.com/ru/setup) и посмотреть первую лекцию курса [«Javascript»](https://github.com/urfu-2016/javascript-slides).

- [Регистрация на GitHub](how-to-pull-request.md#Регистрация-на-github)
- [Как сделать pull request прямо на GitHub](how-to-pull-request.md#Как-сделать-pull-request-прямо-на-github)
- [Как сделать pull request в windows](how-to-pull-request.md#Как-сделать-pull-request-в-windows)
- [Как сделать pull request в linux](how-to-pull-request.md#Как-сделать-pull-request-в-linux)
- [Как закешировать пароль](https://help.github.com/articles/caching-your-github-password-in-git/)

> Для упрощения, workflow не включает в себя создание git-веток  
> Работаем только с __одной master-веткой__

> Если с вашим пуллом беда, например, сделан не с master-ветки  
> попросить пометить его меткой __invalid__, и вы сможете сделать новый!

## Регистрация на GitHub

Если у вас нет аккаунта на Github – регистрируемся по ссылке http://github.com/join  
<img width="780" alt="github-signup" src="https://cloud.githubusercontent.com/assets/4534405/19143150/5dffcfbc-8bbb-11e6-8ab7-747dfbe433fa.png">

Если есть – просто входим по ссылке http://github.com/login  
<img width="333" alt="github-login" src="https://cloud.githubusercontent.com/assets/4534405/19143216/c96e668c-8bbb-11e6-96b6-583957a31b16.png">

## Как сделать pull request прямо на GitHub

**Шаг 1.** Заходим в основной репозиторий задачи https://github.com/urfu-2016/demo-task-1  
И делаем форк задачи к себе. Для этого жмём «fork» в правом верхнем углу.  

<img width="334" alt="fork" src="https://cloud.githubusercontent.com/assets/4534405/19143250/0e61e156-8bbc-11e6-9b1b-54ec5e6c9a80.png">

> Форк (fork) можно расматривать, как личную копию основного репозитория.

**Шаг 2.** Заходим к себе https://github.com/gogoleff/demo-task-1.

> Вместо gogoleff свой логин.

<img width="999" alt="forked" src="https://cloud.githubusercontent.com/assets/4534405/19143270/4a6ffdc2-8bbc-11e6-84ce-eb66e5a0080f.png">

**Шаг 3.** Нажимаем на файл, который хотим изменить. Затем кнопку редактирования.

<img width="996" alt="edit" src="https://cloud.githubusercontent.com/assets/4534405/19143293/6f4ae788-8bbc-11e6-87c8-684037a38b22.png">

**Шаг 4.** Редактируем файл до готовности прямо здесь (или вставляем код из любимого редактора)

<img width="995" alt="progress" src="https://cloud.githubusercontent.com/assets/4534405/19143333/aa8f6d50-8bbc-11e6-9dad-9e1fccd373d1.png">

**Шаг 5.** Когда всё готов создадим коммит.   
Для этого внизу в поле вводим поясняющий текст, и нажимаем «Commit changes».

> Коммит (commit) – можно рассматривать, как утверждение кода, создание версии (как в wiki).
К каждой версии можно вернуться. Каждый новый коммит – новая версия вашего кода.

<img width="759" alt="commit" src="https://cloud.githubusercontent.com/assets/4534405/19143375/e233f0e6-8bbc-11e6-8c90-12ed81d0f007.png">

**Шаг 6.** Создаём pull request. Для этого выбираем пункт меню «Pull requests».  
И нажимаем кнопку «New pull request».

> Пулл (pull request) - сравнение кода в личном репозитории с кодом основного.
Так мы увидим изменения, которые вы сделали. Обычно пулл затем вливают в основной репозиторий,
но мы этого делать не будем :)

<img width="997" alt="pull" src="https://cloud.githubusercontent.com/assets/4534405/19143403/1c64d9c4-8bbd-11e6-8281-befdb864c670.png">

**Шаг 7.** Нажимаем кнопку «Create pull request»

<img width="992" alt="pull-start" src="https://cloud.githubusercontent.com/assets/4534405/19143433/5b21f444-8bbd-11e6-8255-9404e2f63334.png">

**Шаг 8.** Вводим своё __ФИО__ и нажимаем кнопку «Create pull request»

<img width="776" alt="pull-create" src="https://cloud.githubusercontent.com/assets/4534405/19143462/8eeeaede-8bbd-11e6-8bb8-f3bac93961d7.png">

**Готово!**

Если нужны правки, просто повторяем шаги со 2 по 5.

## Как сделать pull request в windows

Устанавливаем Git https://git-scm.com/download/

После установки, запускаем Git Bash  
(ярлык для запуска можно найти в меню Пуск).

Далее смотрим shell команды в разделе [как сделать pull request в linux](how-to-pull-request.md#Как-сделать-pull-request-в-linux).

## Как сделать pull request в linux

В linux уже установлен git и обычно настроен.

**Шаг 1.** Выполняем следующие команды в терминале:  

```bash
# Добавляем свою почту и имя (укажите из вашего профиля на github)
git config --global user.email "sergey@zhigalov.com"
git config --global user.name "Zhigalov Sergey"

# Клонируем репозиторий (вместо gogoleff – ваш логин)
git clone https://github.com/gogoleff/demo-task-1.git

# Заходим в созданную папку с клоном
cd demo-task-1

# Решаем задачу в любимом редакторе...

# Добавляем все изменённые файлы через пробел
git add math.js

# git add необходимо выполнять после каждого изменения файла

# Коммитим (утверждаем изменения)
git commit -m "Моё решение задачи"

# Отправляем ветку с коммитом в удалённый личный (origin) репозиторий
# (может попросить ввод логина и пароля)
git push origin master
```

**Шаг 2.** Создаём pull request

**Шаг 3.** Если нужны правки. Вносим их в любимом редакторе, и снова делаем коммит.

```bash
# Добавляем все изменённые файлы через пробел
git add math.js

# Коммитим
git commit -m "Мои исправления"

# Отправляем новый коммит в удалённый репозиторий
git push origin master
```
