# lab03
```sh
hex@hex-VirtualBox:~/sunflowercactus/workspace$  export GITHUB_USERNAME=sunflowercactus

hex@hex-VirtualBox:~/sunflowercactus/workspace$ pushd .

~/sunflowercactus/workspace ~/sunflowercactus/workspace ~/sunflowercactus/workspace ~

hex@hex-VirtualBox:~/sunflowercactus/workspace$ source scripts/activate

hex@hex-VirtualBox:~/sunflowercactus/workspace$ git clone git@github.com:sunflowercactus/lab02.git projects/lab03
Клонирование в «projects/lab03»...
remote: Enumerating objects: 29, done.
remote: Counting objects: 100% (29/29), done.
remote: Compressing objects: 100% (21/21), done.
Получение объектов: 100% (29/29), 7.79 КиБ | 7.79 МиБ/с, готово.
remote: Total 29 (delta 3), reused 17 (delta 1), pack-reused 0
Определение изменений: 100% (3/3), готово.

hex@hex-VirtualBox:~/sunflowercactus/workspace$ cd projects/lab03

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ git remote remove origin

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ git remote add origin git@github.com:sunflowercactus/lab03.git

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ g++ -std=c++11 -I./include -c sources/print.cpp

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ ls print.o
print.o

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ nm print.o | grep print
00000000000000a1 t _GLOBAL__sub_I__Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSo
0000000000000000 T _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSo
000000000000002a T _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSt14basic_ofstreamIcS2_E

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ ar rvs print.a print.o
ar: создаётся print.a
a - print.o

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ file print.a
print.a: current ar archive

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ g++ -std=c++11 -I./include -c examples/example1.cpp

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ ls example1.o
example1.o

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ g++ example1.o print.a -o example1

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ ./example1 && echo
hello

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ g++ -std=c++11 -I./include -c examples/example2.cpp

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ nm example2.o
                 U __cxa_atexit
                 U __dso_handle
0000000000000000 V DW.ref.__gxx_personality_v0
                 U _GLOBAL_OFFSET_TABLE_
0000000000000173 t _GLOBAL__sub_I_main
                 U __gxx_personality_v0
0000000000000000 T main
                 U __stack_chk_fail
                 U _Unwind_Resume
0000000000000126 t _Z41__static_initialization_and_destruction_0ii
                 U _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSt14basic_ofstreamIcS2_E
                 U _ZNSaIcEC1Ev
                 U _ZNSaIcED1Ev
                 U _ZNSt14basic_ofstreamIcSt11char_traitsIcEEC1EPKcSt13_Ios_Openmode
                 U _ZNSt14basic_ofstreamIcSt11char_traitsIcEED1Ev
                 U _ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEC1EPKcRKS3_
                 U _ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEED1Ev
                 U _ZNSt8ios_base4InitC1Ev
                 U _ZNSt8ios_base4InitD1Ev
0000000000000000 r _ZStL19piecewise_construct
0000000000000000 b _ZStL8__ioinit

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ g++ example2.o print.a -o example2

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ ./example2

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ cat log.txt && echo
hello

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ rm -rf example1.o example2.o print.o

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ rm -rf print.a

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ rm -rf example1 example2

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ rm -rf log.txt

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ cat > CMakeLists.txt <<EOF
> cmake_minimum_required(VERSION 3.4)
> project(print)
> EOF

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
> set(CMAKE_CXX_STANDARD 11)
> set(CMAKE_CXX_STANDARD_REQUIRED ON)
> EOF

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
> add_library(print STATIC \${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)
> EOF

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
> include_directories(\${CMAKE_CURRENT_SOURCE_DIR}/include)
> EOF

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ cmake -H. -B_build
-- The C compiler identification is GNU 9.4.0
-- The CXX compiler identification is GNU 9.4.0
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /home/hex/sunflowercactus/workspace/projects/lab03/_build

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ cmake --build _build

Scanning dependencies of target print
[ 50%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[100%] Linking CXX static library libprint.a
[100%] Built target print

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
> 
> add_executable(example1 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example1.cpp)
> add_executable(example2 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example2.cpp)
> EOF

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
> 
> target_link_libraries(example1 print)
> target_link_libraries(example2 print)
> EOF

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ cmake --build _build 

-- Configuring done
-- Generating done
-- Build files have been written to: /home/hex/sunflowercactus/workspace/projects/lab03/_build
[ 33%] Built target print
Scanning dependencies of target example2
[ 50%] Building CXX object CMakeFiles/example2.dir/examples/example2.cpp.o
[ 66%] Linking CXX executable example2
[ 66%] Built target example2
Scanning dependencies of target example1
[ 83%] Building CXX object CMakeFiles/example1.dir/examples/example1.cpp.o
[100%] Linking CXX executable example1
[100%] Built target example1

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ cmake --build _build --target print

[100%] Built target print

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ cmake --build _build --target example1

[ 50%] Built target print
[100%] Built target example1

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ cmake --build _build --target example2

[ 50%] Built target print
[100%] Built target example2

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ ls -la _build/libprint.a 

-rw-rw-r-- 1 hex hex 3286 апр 28 14:50 _build/libprint.a

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ _build/example1 && echo hello

hellohello

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ _build/example2

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ rm -rf log.txt

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ git clone https://github.com/tp-labs/lab03 tmp
Клонирование в «tmp»...
remote: Enumerating objects: 91, done.
remote: Counting objects: 100% (30/30), done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 91 (delta 23), reused 21 (delta 21), pack-reused 61
Распаковка объектов: 100% (91/91), 1.02 МиБ | 331.00 КиБ/с, готово.

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ mv -f tmp/CMakeLists.txt .

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ rm -rf tmp

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ cat CMakeLists.txt 

cmake_minimum_required(VERSION 3.4)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

option(BUILD_EXAMPLES "Build examples" OFF)

project(print)

add_library(print STATIC ${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)

target_include_directories(print PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
)

if(BUILD_EXAMPLES)
  file(GLOB EXAMPLE_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/examples/*.cpp")
  foreach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
    get_filename_component(EXAMPLE_NAME ${EXAMPLE_SOURCE} NAME_WE)
    add_executable(${EXAMPLE_NAME} ${EXAMPLE_SOURCE})
    target_link_libraries(${EXAMPLE_NAME} print)
    install(TARGETS ${EXAMPLE_NAME}
      RUNTIME DESTINATION bin
    )
  endforeach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
endif()

install(TARGETS print
    EXPORT print-config
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
)

install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/ DESTINATION include)
install(EXPORT print-config DESTINATION cmake)

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install

-- Configuring done
-- Generating done
-- Build files have been written to: /home/hex/sunflowercactus/workspace/projects/lab03/_build

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ cmake --build _build --target install

[100%] Built target print
Install the project...
-- Install configuration: ""
-- Installing: /home/hex/sunflowercactus/workspace/projects/lab03/_install/lib/libprint.a
-- Installing: /home/hex/sunflowercactus/workspace/projects/lab03/_install/include
-- Installing: /home/hex/sunflowercactus/workspace/projects/lab03/_install/include/print.hpp
-- Installing: /home/hex/sunflowercactus/workspace/projects/lab03/_install/cmake/print-config.cmake
-- Installing: /home/hex/sunflowercactus/workspace/projects/lab03/_install/cmake/print-config-noconfig.cmake

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ tree _install

_install
├── cmake
│   ├── print-config.cmake
│   └── print-config-noconfig.cmake
├── include
│   └── print.hpp
└── lib
    └── libprint.a

3 directories, 4 files

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ git add CMakeLists.txt

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$ git commit -m"added CMakeLists.txt"

[main c77a5b5] added CMakeLists.txt
 1 file changed, 36 insertions(+)
 create mode 100644 CMakeLists.txt

hex@hex-VirtualBox:~/sunflowercactus/workspace/projects/lab03$  git push origin master
Перечисление объектов: 29, готово.
Подсчет объектов: 100% (29/29), готово.
При сжатии изменений используется до 4 потоков
Сжатие объектов: 100% (20/20), готово.
Запись объектов: 100% (29/29), 6.83 КиБ | 6.83 МиБ/с, готово.
Всего 29 (изменения 3), повторно использовано 25 (изменения 2)
remote: Resolving deltas: 100% (3/3), done.
To github.com:sunflowercactus/lab03.git
 * [new branch]      master -> master
```
