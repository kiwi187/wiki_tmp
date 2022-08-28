## Создать ключи

    ssh-keygen

после либо согласиться с предложенным названием либо задаться  свое...

    Generating public/private rsa key pair.
    Enter file in which to save the key (C:\Users\Администратор/.ssh/id_rsa):

Далее предложит ввести 2 раза пароль

    Enter passphrase (empty for no passphrase): 
    Enter same passphrase again: 

Если все ок то прочтете нечто вроде этого:

    Your identification has been saved in C:\Users\Администратор/.ssh/id_rsa.
    Your public key has been saved in C:\Users\Администратор/.ssh/id_rsa.pub.
    The key fingerprint is:
    SHA256:dlPRo8qG+f98ZRdH12o2kVspIbVVlpue2VGw1YYqtNg Администратор@WIN-I7J595AMR2O
    The key's randomart image is:
    +---[RSA 3072]----+
    |           .o+o=X|
    |          . .oO*O|
    |         + ..+oO=|
    |        . E.o *=.|
    |        S+oo o..B|
    |       .o.+.   +=|
    |         o     .o|
    |          .  .  .|
    |           ...o. |
    +----[SHA256]-----+

## Добавьте публичный ключ

Переходин в настройки репозитория.. Ключи доступа

Название любое.

Ключ копируем из созданых ключей `pub` (публичный)

## Настройка Git

`git config --list --show-origin` Посмотреть все настройки

`git config --global user.name "John Doe"` Установить имя пользователя

`git config --global user.email johndoe@example.com` Установить e-mail

`git config --global core.editor "d:\0000\Program Files\Portable Sublime Text\sublime_text.exe"` Редактор по умолчанию

`git remote add origin <репозиторий>` Установить соединение с репозиторием под названием origin

`git branch -M main` Переименовать ветку с мастера на маин для гитхаба

## Управление

`git add -A` Добавить все файлы в индекс

`git commit -m"Coment"` Закомитить (создать контрольную точку)

`git push -u origin main` Залить в репозиторий