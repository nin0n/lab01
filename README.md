# lab01
Laboratory work I
Данная лабораторная работа посвещена изучению утилит для разработки проектов

Tasks
[+] 1. Ознакомиться со ссылками учебного материала
[+] 2. Выполнить инструкцию учебного материала
[+] 3. Составить отчет и отправить ссылку личным сообщением в Slack
Tutorial
$ export GITHUB_USERNAME=KatrineFe
$ export GIST_TOKEN=<сохраненный_токен>
$ alias edit=nano
$ mkdir -p ${GITHUB_USERNAME}/workspace
$ cd ${GITHUB_USERNAME}/workspace
$ pwd
/home/ekate/KatrineFe/workspace
$ cd ..
$ pwd
/home/ekate/KatrineFe
$ mkdir -p workspace/tasks/
$ mkdir -p workspace/projects/
$ mkdir -p workspace/reports/
$ cd workspace
$ wget https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz
$ tar -xf node-v6.11.5-linux-x64.tar.xz
$ rm -rf node-v6.11.5-linux-x64.tar.xz
$ mv node-v6.11.5-linux-x64 node
$ ls node/bin
node npm


$ echo ${PATH}
/home/ekate/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/bin:/var/lib/flatpak/exports/bin:/usr/bin/site_perl:/usr/bin/vendor_perl:/usr/bin/core_perl

$ export PATH=${PATH}:`pwd`/node/bin
$ echo ${PATH}
/home/ekate/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/bin:/var/lib/flatpak/exports/bin:/usr/bin/site_perl:/usr/bin/vendor_perl:/usr/bin/core_perl:/home/ekate/KatrineFe/workspace/node/bin


$ mkdir scripts
$ cat > scripts/activate<<EOF
export PATH=\${PATH}:`pwd`/node/bin
EOF
$ source scripts/activate
$ (umask 0077 && echo ${GIST_TOKEN} > ~/.gist)
Report
$ export LAB_NUMBER=01
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md


$ gist REPORT.md
Homework
Скачайте библиотеку boost с помощью утилиты wget. Адрес для скачивания https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz.
$ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
Разархивируйте скаченный файл в директорию ~/boost_1_69_0
$ mkdir ~/boost_1_69_0
$ tar -xvzf boost_1_69_0.tar.gz -C boost_1_69_0
Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории.
$ find -maxdepth 1 -type f | wc -l
12
Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории.
$ find -type f | wc -l
61191
Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).
$ find -type f -name "*.h" | wc -l
296

$ find -type f -name "*.hpp" | wc -l 
14912

$ find -type f -name "*.cpp" | wc -l
13774    

$ find -type f ! -name "*.hpp" ! -name "*.cpp" ! -name "*.h" | wc -l 
32209
Найдите полный пусть до файла any.hpp внутри библиотеки boost.
$ find -type f -iname "any.hpp"     
./boost/fusion/algorithm/query/detail/any.hpp
./boost/fusion/algorithm/query/any.hpp
./boost/fusion/include/any.hpp
./boost/spirit/home/support/algorithm/any.hpp
./boost/type_erasure/any.hpp
./boost/hana/fwd/any.hpp
./boost/hana/any.hpp
./boost/proto/detail/any.hpp
./boost/any.hpp
./boost/xpressive/detail/utility/any.hpp
Выведите в консоль все файлы, где упоминается последовательность boost::asio.
$ grep -r "boost::asio" > ~/asio-gist.txt 
Скомпилирутйе boost. Можно воспользоваться инструкцией или ссылкой.
$ ./bootstrap.sh --prefix=boost_output


$ ./b2 install -j 16
Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.
mv boost_output/lib/ ~/boost-libs/
Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
$ find . -type f -exec du -h {} + > ~/find-gist.txt
Найдите топ10 самых "тяжёлых".
$ find . -type f -exec du -h {} +|sort -rh | head -n 10
154M    ./bin.v2/libs/math/build/gcc-13.2.1/release/threading-multi/src/tr1/pch.hpp.gch
154M    ./bin.v2/libs/math/build/gcc-13.2.1/release/link-static/threading-multi/src/tr1/pch.hpp.gch
12M     ./libs/math/doc/math.pdf
4,5M    ./bin.v2/libs/wave/build/gcc-13.2.1/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/libboost_wave.a
3,7M    ./status/expected_results.xml
3,2M    ./bin.v2/libs/regex/build/gcc-13.2.1/release/link-static/threading-multi/visibility-hidden/libboost_regex.a
3,0M    ./libs/gil/io/test_images/raw/RAW_CANON_D30_SRGB.CRW
2,7M    ./libs/asio/doc/reference.qbk
2,7M    ./libs/algorithm/test/search_test_data/0001.corpus
2,7M    ./bin.v2/libs/math/build/gcc-13.2.1/release/link-static/threading-multi/visibility-hidden/libboost_math_tr1l.a
Copyright (c) 2015-2021 The ISC Authors
