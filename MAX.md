### Лабораторная работа1 :изучение утилит для разработки проектов

### Туториал

Данная лабораторная работа посвещена изучению утилит для разработки проектов

(Вводные данные "-"
 Выходные данные "--"
 Вводные данные в cat ">")

```
-export GITHUB_USERNAME=MAX-shadow
-export GIST_TOKEN=***(тк токен надо держать в секрете)
-alias edit=nano
-mkdir -p ${GITHUB_USERNAME}/workspace
-cd ${GITHUB_USERNAME}/workspace
-pwd
--/home/max/MAX-shadow/workspace
-cd ..
-/home/max/MAX-shadow
-mkdir -p workspace/tasks/
-mkdir -p workspace/projects/
-mkdir -p workspace/reports/
-cd workspace
```

```
-wget https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz
----2026-05-12 16:54:39--  https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz
Распознаётся nodejs.org (nodejs.org)… 104.16.212.131, 104.16.213.131, 2606:4700::6810:d483, ...
Подключение к nodejs.org (nodejs.org)|104.16.212.131|:443... соединение установлено.
HTTP-запрос отправлен. Ожидание ответа… 200 OK
Длина: 9356460 (8,9M) [application/x-xz]
Сохранение в: «node-v6.11.5-linux-x64.tar.xz»

node-v6.11.5-linux- 100%[===================>]   8,92M  2,54MB/s    за 3,7s    


2026-05-12 16:54:44 (2,44 MB/s) - «node-v6.11.5-linux-x64.tar.xz» сохранён [9356460/9356460]
```
```
-tar -xf node-v6.11.5-linux-x64.tar.xz
-rm -rf node-v6.11.5-linux-x64.tar.xz
-mv node-v6.11.5-linux-x64 node
-ls node/bin
--node  npm
-echo ${PATH}
--/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
-export PATH=${PATH}:`pwd`/node/bin
-echo ${PATH}
--/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games:/home/max/MAX-shadow/workspace/node/bin
-mkdir scripts
```
```
-cat > scripts/activate<<EOF
>export PATH=\${PATH}:`pwd`/node/bin
>EOF

-source scripts/activate
-gem install gist
--Fetching gist-6.0.0.gem
Defaulting to user installation because default installation directory (/var/lib/gems/3.3.0) is not writable.
WARNING:  You don't have /home/max/.local/share/gem/ruby/3.3.0/bin in your PATH,
	  gem executables (gist) will not run.
Successfully installed gist-6.0.0
Parsing documentation for gist-6.0.0
Installing ri documentation for gist-6.0.0
Done installing documentation for gist after 0 seconds
1 gem installed
-(umask 0077 && echo ${GIST_TOKEN} > ~/.gist)
-export LAB_NUMBER=01
-git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
--Клонирование в «tasks/lab01»...
remote: Enumerating objects: 74, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 74 (delta 0), reused 1 (delta 0), pack-reused 71 (from 1)
Получение объектов: 100% (74/74), 945.07 КиБ | 1.05 МиБ/с, готово.
Определение изменений: 100% (20/20), готово.
-mkdir reports/lab${LAB_NUMBER}
-cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
-cd reports/lab${LAB_NUMBER}
-edit REPORT.md
-gist REPORT.md
--https://gist.github.com/MAX-shadow/a89eba2edfa80f2b5e9e1e92f3736a
```
### Домашнее задание

```
- find . -maxdepth 1 -type f | wc -l
-- 12
```
```
- find . -type f | wc -l
-- 61191
```
```
- find . -type f -name "*.h" -o -name "*.hpp" | wc -l
-- 15208
```
```
- find . -type f -name "*.cpp" | wc -l
-- 13774
```
```
- find . -type f ! -name "*.h" -a ! -name "*.hpp" -a ! -name "*.cpp" | wc -l
-- 32209
```
```
- find / -name "any.hpp" 2>/dev/null | xargs realpath
-- /home/max/boost_1_69_0/boost/hana/any.hpp
-- /home/max/boost_1_69_0/boost/hana/fwd/any.hpp
-- /home/max/boost_1_69_0/boost/xpressive/detail/utility/any.hpp
-- /home/max/boost_1_69_0/boost/fusion/algorithm/query/detail/any.hpp
-- /home/max/boost_1_69_0/boost/fussion/algorithm/query/any.hpp
-- /home/max/boost_1_69_0/boost/fusion/include/any.hpp
-- /home/max/boost_1_69_0/boost/spirit/home/support/algorithm/any.hpp
-- /home/max/boost_1_69_0/boost/proto/detail/any.hpp
-- /home/max/boost_1_69_0/boost/type_erasure/any.hpp
```
```
- grep -rl "boost::asio" .

- ./bootstrap.sh --prefix=/usr/local --with-libraries=all
-- Building Boost.Build engine with toolset gcc... tools/build/src/engine/bin.linuxx86_64/b2
-- Unicode/ICU support for Boost.Regex?... not found.
-- Generating Boost.Build configuration in project-config.jam...
-- 
-- Bootstraping is done. To build, run:
-- 
-- ./b2
-- 
-- To adjust configuration, edit 'project-config.jam'.
-- Further information:
-- 
-- - Command line help:
--   ./b2 --help
-- 
-- - Getting started guide:
--   http://www.boost.org/more/getting_started/unix-variants.html
-- 
-- - Boost.Build documentation:
--   http://www.boost.org/build/doc/html/index.html

-- 888
-- 
-- BOOSTITERATORCONVERTIBLE(Derived2,Derived1)
-- 
-- 889
-- 
-- usr/include/c++/14/bits/stl vector.h:1673:21:
-- required from'void std::vector<Tp,Alloc>::M range initialize(InputIterator,InputIterator,std::input iterator tag)[with InputIterator = boost::iterators::transform iterator<boost::algorithm::detail::copy_iterator_rangeF<std::cxxll::basic_string<char>,gnu cxx::normal_iterator<char*,std::cxxll::basic_string<char>>>,boost::algorithm::split_iterator<gnucxx::normal_iterator<char*>,std::cxxll::basic_string<char>>>,boost::iterators::use_default,boost::iterators::use_default>; =std::cxx11::basic_string<char>;Alloc=std::allocator<std::cxx11::basic string<char> >]'
-- 1673
-- for（；first！=last;++first）
-- usr/include/c++/14/bits/stl vector.h:711:23:
-- required from'std::vector<Tp,Alloc>::vector(InputIterator,InputIterator,const allocator_type&)[with InputIterator = boost::iterators::transform iterator<boost::algorithm::detail::copyiterator_rangeF<std::cxxll::basic_string<char>,gnucxx::normal_iterator<char*,std::cxxll::basic_string<char>>>,boost::algorithm::split_iterator<gnucxx::normal_iterator<char*>,std::cxxll::basic_string<char>>>,boost
```
```
- nano test.cpp
- g++ test.cpp -o test
- cat test.cpp
-- #include <boost/version.hpp>
-- #include <iostream>
-- 
-- int main() {
--     std::cout << "Boost version: " << BOOST_VERSION << std::endl;
--     std::cout << "Boost lib version: " << BOOST_LIB_VERSION << std::endl;
--     return 0;
-- }
```
```
- ./test
-- Boost version: 106900
-- Boost lib version: 1_69
```
```

- mkdir -p ~/boost-libs
- cd boost_1_69_0
- sudo mv /usr/local/lib/libboost_*.a ~/boost-libs
-- [sudo] наполь для raspul:
- cd boost-libs
-- bash: cd: boost-libs: Нет такого файла или каталога
- cd
- ls
-- libboost_atomic.a    libboost_random.a
-- libboost_chrono.a    libboost_regex.a
-- libboost_container.a  libboost_serialization.a
-- libboost_context.a   libboost_stacktrace_addr2line.a
-- libboost_contract.a   libboost_stacktrace_backtrace.a
-- libboost_date_time.a libboost_stacktrace_basic.a
-- libboost_exception.a libboost_stacktrace_noop.a
-- libboost_fiber.a    libboost_system.a
-- libboost_filesystem.a libboost_test_exec_monitor.a
-- libboost_graph.a    libboost_timer.a
-- libboost_istreams.a  libboost_unit_test_framework.a
-- libboost_locate.a   libboost_wave.a
-- libboost_prg_exec_monitor.a libboost_wserialization.a
-- libboost_program_options.a
```
```
- find ~/boost-libs -type f -exec ls -lh {} \; | awk
'{print $5 "|" $9}'
-- 319K    /home/max/boost-libs/libboost_contract.a
-- 206K    /home/max/boost-libs/libboost_prg_exec_monitor.a
-- 229K    /home/max/boost-libs/libboost_chrono.a
-- 2,4K    /home/max/boost-libs/libboost_atomic.a
-- 19K    /home/max/boost-libs/libboost_stacktrace_backtrace.a
-- 824K    /home/max/boost-libs/libboost_graph.a
-- 773K    /home/max/boost-libs/libboost_wserialization.a
-- 2,2M    /home/max/boost-libs/libboost_unit_test_framework.a
-- 400K    /home/max/boost-libs/libboost_filesystem.a
-- 229K    /home/max/boost-libs/libboost_fiber.a
-- 2,7M    /home/max/boost-libs/libboost_regex.a
-- 4,5M    /home/max/boost-libs/libboost_wave.a
-- 2,0M    /home/max/boost-libs/libboost_locale.a
-- 20K    /home/max/boost-libs/libboost_context.a
-- 35K    /home/max/boost-libs/libboost_stacktrace_addr2line.a
-- 1,3K    /home/max/boost-libs/libboost_system.a

- find ~/boost-libs -type f -exec ls -lh {} \; | awk '{print $5 "|" $9}' | sort -hr | head -10
-- 4,5M    /home/max/boost-libs/libboost_wave.a
-- 2,7M    /home/max/boost-libs/libboost_regex.a
-- 2,2M    /home/max/boost-libs/libboost_unit_test_framework.a
-- 2,2M    /home/max/boost-libs/libboost_test_exec_monitor.a
-- 2,0M    /home/max/boost-libs/libboost_locate.a
-- 1,5M    /home/max/boost-libs/libboost_program_options.a
-- 1,2M    /home/max/boost-libs/libboost_serialization.a
-- 824K    /home/max/boost-libs/libboost_graph.a
-- 773K    /home/max/boost-libs/libboost_wserialization.a
-- 400K    /home/max/boost-libs/libboost_filesystem.a
```
