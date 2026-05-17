### Лабораторная работа1 :изучение утилит для разработки проектов

### Tutorial
### 1.Настройка переменных окружения

```bash
export GITHUB_USERNAME=qNetayS
export GIST_TOKEN=<сохраненный_токен>
alias edit=nano
```
### 2.Настройка переменных окружения
```
mkdir -p ${GITHUB_USERNAME}/workspace
cd ${GITHUB_USERNAME}/workspace
pwd
cd ..
pwd

mkdir -p workspace/tasks/
mkdir -p workspace/projects/
mkdir -p workspace/reports/
cd workspace
```
Результат:
созданы струкуры:
qNetayS/workspace/tasks/
qNetayS/workspace/projects/
qNetayS/workspace/reports/

### 3.Установка Node.js
```
wget https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz
tar -xf node-v6.11.5-linux-x64.tar.xz
rm -rf node-v6.11.5-linux-x64.tar.xz
mv node-v6.11.5-linux-x64 node
```
### 4.Добавление Node.js в PATH
```
ls node/bin
echo ${PATH}
export PATH=${PATH}:`pwd`/node/bin
echo ${PATH}
```
### 5.Создание скрипта активации окружения
```
mkdir scripts
cat > scripts/activate<<EOF
export PATH=\${PATH}:`pwd`/node/bin
EOF
source scripts/activate
```
### 6.Установка утилиты gist
```
gem install gist
```
### 7.Сохраниение токена для gist
```
(umask 0077 && echo ${GIST_TOKEN} > ~/.gist)
```
Результат: токен сохранен с правами 600
### 1. Скачивание библиотек boost c помощью wget

```shell
wget hhtps://sourceforge.net/projects/boost/1.69.0/boost_1_69_0.tar.gz
```
Результат: файл успешно скачан в директорию ~/Timp

### 2. Разархивированиие в директорию ~/boost_1_69_0
Выполнение команды:
```shell
tar -xzf boost_1_69_0.tar.gz -C ~/Timp/
```
Результат:создана директория ~/Timp/boost_1_69_0 с нужным содержимым

### 3.Подсчет количества файлов(без учета вложенных директорий)
```shell 
find ~/Timp/boost_1_69_0 -maxdepth 1 -type f | wc -l
```
Результат: 12
В корневой директории boost находится 12 файлов (README,LICENSE,index.html и другие)

### 4.Подсчет количества файлов(с учетом вложенных директорий)
```shell
find ~/Timp/boost_1_69_0 -type f|wc -l
```
Результат: 8285

### 5.Подсчет .hpp .cpp и остальных файлов 
заводим переменные которые хранят количества файлов типов 
```shell
hpp_count=$(find ~/Timp/boost_1_69_0 -type f -name "*.hpp" |wc -l
cpp_count=$(find ~/Timp/boost_1_69_0 -type f -name "*.hpp" |wc -l
total_files=$(find ~/Timp/boost_1_69_0 -type f|wc -l)
other_count=$((total_files - hpp_count - spp_count))
```

а после выводим их в качестве ответа на данный пункт 
```shell
echo "HPP $hpp_count"
echo "CPP $cpp_count"
echo "Other $other_count"
```
Результат:
HPP: 14912
CPP: 13774
Other: 32505

### 6.Поиск пустого файла any.hpp
как я понял имеется ввиду найти любой файл с весом ноль,тогда
```shell
find ~/Timp/boost_1_69_0 -name "*.hpp" -size 0
```
Результат:путь файла
/home/vboxuser/boost_1_69_0/tools/build/src/tools/doxygen/windows-paths-check.hpp

### 7.Поиск файлова с упоминанием boost::asio

```shell 
grep -r "boost::asio" ~/Timp/boost_1_69_0 -- incluse-"*.hpp" --include="*.cpp" -l
```
файлов получилось слишком много,тогда подсчитаем их количество
```shell
grep -r "boost::asio" ~/Timp/boost_1_69_0 -- incluse-"*.hpp" --include="*.cpp"--include="*.h" | wc -l
```
Результат:11550

### 8.Компиляция Boost
Для более быстрйо компиляции используем команды 
```shell
cd ~/TImp/boost_1_69_0
./bootstrap.sh
./b2 -j$(nproc) stage
```
Результат:
создана директория stage/lib/
скомпилированы статистические библиотеки(*.a)

### 9.Перенос статистических библиотек в ~/boost-libs

```shell
mkdir -p ~/boost/libs
cp ~/Timp?boost_1_69_0/stage/lib/*.a ~/boost-libs/
```
проверка:
```shell
ls ~/Timp/boost_1_69_0/stage/lib/*.a
```
Результат:вывод всех статистических библиотек формата .a

### 10.Подстчет дискового пространства каждого файла

```shell
ls -lh ~/Timp/boost-libs/
```
Результат:вывод множества пространств, в общем 20М

### 11.Ввод топ 10 тяжелых библиотек
```shell
ls -ls ~/Timp/boost-libs/ |head -11
```
Результат:
libbost_atomic.a
libbost_ahrono.a
libbost_container.a
libbost_context.a
и другие 
Итого 20060
