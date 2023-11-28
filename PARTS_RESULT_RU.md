# Отчет по проекту "Операционные системы UNIX/Linux (Базовый)"

Установка и обновления системы Linux. Основы администрирования.

## Part 1. Установка ОС

- Установил Ubuntu - проверил версию используя команду: `cat /etc/issue`
![linux](assets/images/part_1.png)

## Part 2. Создание пользователя

- Создание нового пользователя в группе adm: `sudo useradd -g adm gylbertk` и выставляю новый пароль `sudo passwd gylbertk`

![linux](assets/images/part_2_1.png)


- Вывел пользователя: `cat /etc/passwd` - итого:

![linux](assets/images/part_2_2.png)


- Или просто его найдем: `grep -w '^gylbertk' /etc/passwd`

![linux](assets/images/part_2_3.png)


## Part 3. Настройка сети ОС

- Задал название машины вида gylbertk-1: `sudo hostnamectl set-hostname gylbertk-1`

![linux](assets/images/part_3_1.png)


- Установил временную зону, соответствующую моему текущему местоположению: `sudo timedatectl set-timezone Asia/Novosibirsk`

![linux](assets/images/part_3_2.png)

- Вывел название сетевых интерфейсов с помощью консольной команды: `ifconfig -a`

![linux](assets/images/part_3_3.png)

----
- Интерфейс lo - виртуальный инетерфейс по умолчанию есть в любой Linux системе и работает по адресу 127.0.0.1 и предназначен для доступа к своему же компьютеру!
----

![linux](assets/images/part_3_4.png)

- Получил список IP адрес устройства на котором работаем от сервера DHCP

----
- DHCP - это Dynamic Host Configuration Protocol - протокол динамической настройки узла!
----

- Определил и вывел на экран внешний ip-адрес шлюза (ip) и внутренний IP-адрес шлюза, он же ip-адрес по умолчанию (gw)

![linux](assets/images/part_3_5.png)


- Задал статичные настройки ip, gw, dns (использовал публичный DNS сервера, например 1.1.1.1 или 8.8.8.8) - использовал команду `sudo vim /etc/netplan/00-installer-config.yaml`

![linux](assets/images/part_3_6.png)


- Перезагрузил виртуальную машину `reboot`. Убедиться, что статичные сетевые настройки (ip, gw, dns) соответствуют заданным в предыдущем пункте.

![linux](assets/images/part_3_7.png)


- Успешно пропинговал удаленные хосты 1.1.1.1 и ya.ru

![linux](assets/images/part_3_8.png)

## Part 4. Обновление ОС

- Произвел попытку обновления системы командой: `sudo apt upgrade`

![linux](assets/images/part_4_1.png)

## Part 5. Использование команды **sudo**

----
- Команда sudo ( substitute user and do, подменить пользователя и выполнить ) позволяет строго определенным пользователям выполнять указанные программы с административными привилегиями без ввода пароля суперпользователя root. Если быть точнее, то команда sudo позволяет выполнять программы от имени любого пользователя, но, если идентификатор или имя этого пользователя не указаны, то предполагается выполнение от имени суперпользователя root. Таким образом, использование sudo позволяет выполнять привилегированные команды обычным пользователям без необходимости ввода пароля суперпользователя root . Список пользователей и перечень их прав по отношению к ресурсам системы может быть настроен оптимальным образом для обеспечения комфортной и безопасной работы. Например, команда sudo в Ubuntu Linux, используется в режиме, позволяющем выполнять любые задачи администрирования системы без интерактивного входа под учетной записью root.
----
- Поменял hostname ОС от имени пользователя, созданного в пункте Part 2 (используя sudo). `sudo usermod -aG sudo gylbertk` и после проверив это!

![linux](assets/images/part_5.png)

- так же проверяем права и меняем имя хоста переключившись на пользователя в пункте Part 2

![linux](assets/images/part_5_1.png)


## Part 6. Установка и настройка службы времени

- Текущее время:

![linux](assets/images/part_6_1.png)

- Вывел время, часового пояса, в котором я сейчас находился.

![linux](assets/images/part_6_2.png)


## Part 7. Установка и использование текстовых редакторов


- Установил текстовые редакторы **VIM**, **NANO**, **MCEDIT**, **JOE**. такими командами как: `sudo apt install vim` - `sudo apt install nano` - `sudo apt install joe` 

### Работа с VIM
- Создал файл test_vim.txt используя команду `vim test_vim.txt`. В файле указал свой ник сохранил и вышел. Для редактирования испольем клавишу `i` - включается режим `insert` для его отключения клавиша `esc` и сам выход из редактора  `shift` + `:` и прописываем `:wq` + `insert`

![linux](assets/images/part_7_1.png)

- снова его открыл и отредактировал:

![linux](assets/images/part_7_2.png)

- снова его открыл и нашел нужное мне слово командой `/`:

![linux](assets/images/part_7_3.png)

- снова его открыл и заменил одно слово на другое `:s/какое_слово_заменить/на_что_заменить`:

![linux](assets/images/part_7_4.png)

### Работа с NANO
- Создал файл test_vim.txt используя команду `nano test_nano.txt`. В файле указал свой ник сохранил и вышел нажав `control + O` (плюс подтвердил название файла нажав на `inter`) и что бы сохранить и выйти из редактора `control + X`

![linux](assets/images/part_7_5.png)

- снова его открыл и отредактировал и нажал `control + X` и выбрал опцию `N` для закрытия файла без сохранения изменений:

![linux](assets/images/part_7_6.png)

- результат:

![linux](assets/images/part_7_7.png)

- снова его открыл и нашел нужно мне слово `control + W` в результате на искомое слово перемещается курсор в начало слово:

![linux](assets/images/part_7_8.png)

- нужное мне слово заменить `control + \`:

![linux](assets/images/part_7_9.png)

### Работа с JOE
- Создал файл test_joe.txt используя команду `joe test_joe.txt`. В файле указал свой ник сохранил и вышел. Для save используем клавиши `control + К` и для выхода `control + x`

![linux](assets/images/part_7_10.png)

- снова его открыл и отредактировал и нажал `control + C` и выбрал опцию `Y` для закрытия файла без сохранения изменений:

![linux](assets/images/part_7_11.png)

- результат:

![linux](assets/images/part_7_12.png)

- снова его открыл и нужно найти какоето слово - для начала курсор в начала всего текста перемещаем ` control + k и сразу нажимаем неотпуская control кнопку F`: и найденно слово курсор перемещается в конец искомого слова

![linux](assets/images/part_7_13.png)

- далее нудно заменить одно слово на другое ` control + k и сразу нажимаем неотпуская control кнопку F ищем слово и сразу кнопка R` и для подтверждения нажимаем `Y`

![linux](assets/images/part_7_14.png)

- результат:

![linux](assets/images/part_7_15.png)







## Part 8. Установка и базовая настройка сервиса **SSHD**


- Установил службу SSHd командой `sudo apt install openssh-server`

![linux](assets/images/part_8_1.png)

- Добавил автостарт службы при загрузке системы командой `sudo systemctl enable ssh`

![linux](assets/images/part_8_2.png)

- И проверил что служба работает `sudo systemctl status ssh`

![linux](assets/images/part_8_3.png)

- Перенастроил службу SSHd на порт 2022. Предварительно открываем конфиг службы `/etc/ssh/sshd_config` и поменял на порт 2022

![linux](assets/images/part_8_4.png)

- Использовал команду ps, показал наличие процесса sshd `ps -e | grep sshd`

![linux](assets/images/part_8_5.png)

----
- `ps` - позволяет посмотреть процессы в текущей оболочке использовав флаг **-е**, чтобы выбрать все процессы и устилиту **grep** для поиск процесса
----

- затем перезапустил конфигурацию командой `sudo systemctl reload ssh` либо перезапуск всей службы `sudo systemctl restart ssh` и перезагрузил систему командой `reboot` и проверил открытые порты `netstat -tan`

![linux](assets/images/part_8_6.png)

----
### Значение ключей -tan:

- **-t** используется, чтобы показать tcp порты;
- **-a** показывает все порты;
- **-n** показывает ip адреса в числовом виде.

### Значение столбцов вывода:


- **Proto** — протокол (tcp, udp).
- **Recv-Q** — количество байтов, помещённых в буфер приёма TCP/IP, но не переданных приложению. Если это число высокое, то нужно проверить работоспособность приложения, которое работает с данным портом.
- **Send-Q** — количество байтов, помещённых в буфер отправки TCP/IP, но не отправленных, или отправленных, но не подтверждённых. Высокое значение может быть связано с перегрузкой сети сервера.
- **Local Address** — локальный адрес сервера.
- **Foreign Address** — адрес второй стороны.
- **State** — состояние подключения, или прослушивания. (LISTENING — сокет ожидает запроса на подключение, CONNECTED — сокет подключен, DISCONNECTING — сокет отключен)

### Значение 0.0.0.0:
- Это IP-адрес на локальной машине по умолчанию
----

## Part 9. Установка и использование утилит **top**, **htop**

- Установил утилиту `top` командой: `sudo apt install top`
- Установил утилиту `htop` командой: `sudo apt install htop`

### Работа с top

- Пример работы:
![linux](assets/images/part_9_1.png)

- **uptime**: 7 min;
- **количество авторизованных пользователей**: 1 user;
- **общая загрузка системы**: 0.00, 0.00, 0.00
- **общее количество процессов**: 112
- **загрузку cpu**: 0.0 us, 0.0 sy, 0.0 ni, 100 id, 0.0 wa, 0.0 hi, 0.0 si, 0.0 st
- **загрузку памяти**: 981.0 total, 169.3 free, 193.6 used, 618.1 buff/cache
- **pid процесса занимающего больше всего памяти**: 950
- **pid процесса, занимающего больше всего процессорного времени**: 950


### Работа с htop

- Пример работы:
![linux](assets/images/part_9_2.png)

----

- Вывод команды htop с сортировкой по **PID**:

![linux](assets/images/part_9_3.png)

- Вывод команды htop с сортировкой по **PERCENT_CPU**:

![linux](assets/images/part_9_4.png)

- Вывод команды htop с сортировкой по **PERCENT_MEM**:

![linux](assets/images/part_9_5.png)

- Вывод команды htop с сортировкой по **TIME**:

![linux](assets/images/part_9_6.png)

- Вывод команды htop с фильтрацией для процесса **sshd**:

![linux](assets/images/part_9_7.png)

- Поиск процесса **syslog**:

![linux](assets/images/part_9_8.png)

- Добавил вывод **hostname**, **clock** и **uptime**:

![linux](assets/images/part_9_9.png)

## Part 10. Использование утилиты **fdisk**

- Запустил команду fdisk -l. `sudo fdisk -l`

![linux](assets/images/part_10_1.png)

- **Название жесткого диска**: dev/sda2;
- **Размер жесткого диска**: 16 GiB;
- **Количество секторов**: 33548288;
- **Размер swap** (посмотрел с помощью команды `swapon --show`): 2.3 GiB.

![linux](assets/images/part_10_2.png)

## Part 11. Использование утилиты **df**

### Запустил `df`
- Запустил команду `df`:

![linux](assets/images/part_11_1.png)

- **размер раздела**: 16 445 308
- **размер занятого пространства**: 5 813 576
- **размер свободного пространства**: 97 776 644
- **процент использования**: 38%
- **единица измерения в выводе**: в килобайтах.
- 
### Запустил `df -Th`
- Запустил команду `df -Th`:
  - опция `-h`, чтобы выводить размеры в читаемом виде, в мегабайтах или гигабайтах;
  - опция `-T`, чтобы выводить информацию только про указанные файловые системы.

![linux](assets/images/part_11_2.png)

- **размер раздела**: 16G
- **размер занятого пространства**: 5.6G
- **размер свободного пространства**: 9.4G
- **процент использования**: 38%
- **тип файловой системы для раздела**: ext4.


## Part 12. Использование утилиты **du**


Использовал флаг `-s` для вывода только общего размера папки
- Размер папок /home, /var, /var/log в байтах: `sudo du -s /home /var /var/log`

![linux](assets/images/part_12_1.png)

- Размер папок /home, /var, /var/log в человекочитаемом виде: `sudo du -sh /home /var /var/log`

![linux](assets/images/part_12_2.png)

- Cодержимоe в /var/log (не общее, а каждого вложенного элемента): `sudo du -s /home /var /var/log`

![linux](assets/images/part_12_3.png)

## Part 13. Установка и использование утилиты **ncdu**

- Установил утилиту командой `sudo apt-get install ncdu`

![linux](assets/images/part_13_1.png)

- Вывел размеры папок /home, /var, /var/log:
  - /home

![linux](assets/images/part_13_2.png)

  - /var

![linux](assets/images/part_13_3.png)

  - /var/log

![linux](assets/images/part_13_4.png)


## Part 14. Работа с системными журналами

- Открыл для просмотра:
  - /var/log/dmesg

![linux](assets/images/part_14_1.png)

  - /var/log/syslog

![linux](assets/images/part_14_2.png)

  - /var/log/auth.log

![linux](assets/images/part_14_3.png)

Время последней успешной авторизации - 20:49:16, имя пользователя - student и метод входа в систему - by LOGIN (скрин ниже).

![linux](assets/images/part_14_4.png)

----
![linux](assets/images/part_14_5.png)

----

- Перезапустил службу SSHD командой `sudo systemctl restart ssh` и в /var/log/syslog нашел системную запись об этом:

![linux](assets/images/part_14_6.png)


## Part 15. Использование планировщика заданий **CRON**

Открыть планировщик заданий для редактирования: `crontab -e`
- Используя планировщик заданий, запускаю команду uptime через каждые 2 минуты:

![linux](assets/images/part_15_1.png)

![linux](assets/images/part_15_2.png)

- Вывожу на экран список текущих заданий для CRON командой `crontab -l`

![linux](assets/images/part_15_3.png)

- Удалил все существующие задачи командой `crontab -r` и проверил список текущих задач

![linux](assets/images/part_15_4.png)