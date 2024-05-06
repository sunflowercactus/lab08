[![Build Status](https://app.travis-ci.com/sunflowercactus/lab05.svg?token=ZKuaH6W5sCjAp1m4YkJJ&branch=master)](https://app.travis-ci.com/github/sunflowercactus/lab05)
# lab05
```sh
hex@hex-VirtualBox:~$ export GITHUB_USERNAME=sunflowercactus

hex@hex-VirtualBox:~$ GITHUB_TOKEN=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

hex@hex-VirtualBox:~$ cd ${GITHUB_USERNAME}/workspace

hex@hex-VirtualBox:~/sunflowercactus/workspace$ pushd .

~/sunflowercactus/workspace ~/sunflowercactus/workspace

hex@hex-VirtualBox:~/sunflowercactus/workspace$ source scripts/activate

hex@hex-VirtualBox:~/sunflowercactus/workspace$ sudo apt install ruby-full
[sudo] пароль для hex: 
Чтение списков пакетов… Готово
Построение дерева зависимостей       
Чтение информации о состоянии… Готово
Уже установлен пакет ruby-full самой новой версии (1:2.7+1).
Следующий пакет устанавливался автоматически и больше не требуется:
  gir1.2-goa-1.0
Для его удаления используйте «sudo apt autoremove».
Обновлено 0 пакетов, установлено 0 новых пакетов, для удаления отмечено 0 пакетов, и 0 пакетов не обновлено.

hex@hex-VirtualBox:~/sunflowercactus/workspace$ sudo gem install travis

hex@hex-VirtualBox:~/sunflowercactus/workspace$ git clone git@github.com:sunflowercactus/lab03.git projects/lab05

Клонирование в «projects/lab05»...
remote: Enumerating objects: 32, done.
remote: Counting objects: 100% (32/32), done.
remote: Compressing objects: 100% (22/22), done.
remote: Total 32 (delta 4), reused 28 (delta 3), pack-reused 0
Получение объектов: 100% (32/32), 10.26 КиБ | 3.42 МиБ/с, готово.
Определение изменений: 100% (4/4), готово.

hex@hex-VirtualBox:~/sunflowercactus/workspace$ cd projects/lab05

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab05$ git remote remove origin

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab05$ git remote add origin git@github.com:sunflowercactus/lab05.git

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab05$  cat > .travis.yml <<EOF
> language: cpp
> EOF

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab05$ cat >> .travis.yml <<EOF
> 
> script:
> - cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
> - cmake --build _build
> - cmake --build _build --target install
> EOF

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab05$ cat >> .travis.yml <<EOF
> 
> addons:
>   apt:
>     sources:
>       - george-edison55-precise-backports
>     packages:
>       - cmake
>       - cmake-data
> EOF

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab05$ ex -sc '1i|[![Build Status](https://app.travis-ci.com/sunflowercactus/lab05.svg?token=ZKuaH6W5sCjAp1m4YkJJ&branch=master)](https://app.travis-ci.com/github/sunflowercactus/lab05)' -cx README.md

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab05$ git add .travis.yml

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab05$ git add README.md

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab05$ git commit -m"added CI"

[master 654807b] added CI
 2 files changed, 15 insertions(+)
 create mode 100644 .travis.yml

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab05$ git push origin master

Перечисление объектов: 36, готово.
Подсчет объектов: 100% (36/36), готово.
При сжатии изменений используется до 4 потоков
Сжатие объектов: 100% (25/25), готово.
Запись объектов: 100% (36/36), 10.75 КиБ | 10.75 МиБ/с, готово.
Всего 36 (изменения 6), повторно использовано 30 (изменения 4)
remote: Resolving deltas: 100% (6/6), done.
To github.com:sunflowercactus/lab05.git
 * [new branch]      master -> master
```
