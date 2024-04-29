# lab02
```sh
hex@hex-VirtualBox:~/sunflowercactus/workspace$ export GITHUB_USERNAME=sunflowercactus

hex@hex-VirtualBox:~/sunflowercactus/workspace$ export GITHUB_EMAIL=sobikfox@gmail.com

hex@hex-VirtualBox:~/sunflowercactus/workspace$ alias edit=nvim

hex@hex-VirtualBox:~/sunflowercactus/workspace$ source scripts/activate

hex@hex-VirtualBox:~/sunflowercactus/workspace$ mkdir ~/.config

hex@hex-VirtualBox:~/sunflowercactus/workspace$ cat > ~/.config/hub <EOF
> github.com:
> - user: ${GITHUB_USERNAME}
>   oauth_token: ${GITHUB_TOKEN}
>   protocol: ssh
> EOF

hex@hex-VirtualBox:~/sunflowercactus/workspace$ git config --global hub.protocol ssh

hex@hex-VirtualBox:~/sunflowercactus/workspace$ mkdir projects/lab02 && cd projects/lab02

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ git init
Инициализирован пустой репозиторий Git в /home/hex/sunflowercactus/workspace/projects/lab02/.git/

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ git config --global user.name ${GITHUB_USERNAME}

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ git config --global user.email ${GITHUB_EMAIL}

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ git config -e --global

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ git remote add origin git@github.com:sunflowercactus/lab02.git

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ git pull origin main
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Распаковка объектов: 100% (3/3), 873 байта | 174.00 КиБ/с, готово.
Из github.com:sunflowercactus/lab02
 * branch            main       -> FETCH_HEAD
 * [новая ветка]     main       -> origin/main

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ touch TEST.md

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ git status 
Текущая ветка: master
Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	TEST.md

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ git add TEST.md

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ git commit -m "added TEST.md"
[master 0814844] added TEST.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 TEST.md

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ git push --set-upstream origin master
Перечисление объектов: 6, готово.
Подсчет объектов: 100% (6/6), готово.
При сжатии изменений используется до 4 потоков
Сжатие объектов: 100% (3/3), готово.
Запись объектов: 100% (6/6), 1.11 КиБ | 1.11 МиБ/с, готово.
Всего 6 (изменения 0), повторно использовано 0 (изменения 0)
remote: 
remote: Create a pull request for 'master' on GitHub by visiting:
remote:      https://github.com/sunflowercactus/lab02/pull/new/master
remote: 
To github.com:sunflowercactus/lab02.git
 * [new branch]      master -> master
Ветка «master» отслеживает внешнюю ветку «master» из «origin».

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ git pull origin master
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Распаковка объектов: 100% (3/3), 1002 байта | 1002.00 КиБ/с, готово.
Из github.com:sunflowercactus/lab02
 * branch            master     -> FETCH_HEAD
   c45e6a4..71221a5  master     -> origin/master
Обновление c45e6a4..71221a5
Fast-forward
 .gitignore | 4 ++++
 1 file changed, 4 insertions(+)
 create mode 100644 .gitignore

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ git log
commit 71221a53a44f27cb19ac84aa7a5b93f9c6c2d446 (HEAD -> master, origin/master)
Author: soboleva_dasha <115922130+sunflowercactus@users.noreply.github.com>
Date:   Tue Apr 30 00:28:14 2024 +0300

    Create .gitignore

commit c45e6a4c1cdbf3c11d7e245c202f1970ec16024b
Author: sunflowercactus <sobikfox@gmail.com>
Date:   Tue Apr 30 00:24:19 2024 +0300

    added TEST.md

commit c613581103b476e00c8577e25c564194217b1338 (origin/main)
Author: soboleva_dasha <115922130+sunflowercactus@users.noreply.github.com>
Date:   Tue Apr 30 00:23:34 2024 +0300

    Create README.md


hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ mkdir sources && mkdir include && mkdir examples

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ cat > sources/print.cpp <<EOF
> #include <print.hpp>
> 
> void print(const std::string& text, std::ostream& out)
> {
>   out << text;
> }
> 
> void print(const std::string& text, std::ofstream& out)
> {
>   out << text;
> }
> EOF

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ cat > include/print.hpp <<EOF
> #include <fstream>
> #include <iostream>
> #include <string>
> 
> void print(const std::string& text, std::ofstream& out);
> void print(const std::string& text, std::ostream& out = std::cout);
> EOF

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ cat > examples/example1.cpp <<EOF
> #include <print.hpp>
> 
> int main(int argc, char** argv)
> {
>   print("hello");
> }
> EOF

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ cat > examples/example2.cpp <<EOF
> #include <print.hpp>
> 
> #include <fstream>
> 
> int main(int argc, char** argv)
> {
>   std::ofstream file("log.txt");
>   print(std::string("hello"), file);
> }
 EOF
hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab02$ edit README.md
```









