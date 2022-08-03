## Part 1. Установка ОС
1. Начало установки Ubuntu 20.04
![./Screenshots/1.png](./Screenshots/1.png)


2. Продолжение установки Ubuntu 20.04
![./Screenshots/2.png](./Screenshots/2.png)


3. Определение версии установленной ОС
![./Screenshots/3.png](./Screenshots/3.png)

## Part 2. Создание пользователя

1. Создание нового пользователя и добавление его в группу adm
   - G - Список дополнительных групп, в которых числится пользователь. Перечисление групп осуществляется 
   через запятую, без промежуточных пробелов. На указанные группы действуют те же ограничения, что и для группы указанной 
   в параметре -g. По умолчанию пользователь входит только в начальную группу.
   - m - Если домашнего каталога пользователя не существует, то он будет создан.
   - s - Имя регистрационной оболочки пользователя. Если задать пустое значение, то будет использована регистрационная оболочка по умолчанию.
   
![./Screenshots/4.png](./Screenshots/4.png)

2. Вывод команды cat /etc/passwd с подтверждением создания нового пользователя
![./Screenshots/5.png](./Screenshots/5.png)

3. Вывод команды vi /etc/group с подтверждением внесения пользователя в группу adm
![./Screenshots/6.png](./Screenshots/6.png)

## Part 3. Настройка сети ОС

1. Вызов команды sudo nano /etc/hostname для смены названия машины
![./Screenshots/7.png](./Screenshots/7.png)

2. Замена старого названия                  
![./Screenshots/8.png](./Screenshots/8.png)

3. На новое                                 
![./Screenshots/9.png](./Screenshots/9.png)

4. Проверка название машины после перезагрузки
![./Screenshots/10.png](./Screenshots/10.png)

5. Установка временной зоны при помощи команды dpkg-reconfigure tzdata.
![./Screenshots/11.png](./Screenshots/11.png) 
##### Вывести названия сетевых интерфейсов с помощью консольной команды.
6. Вывод названий сетевых интерфейсов при помощи команды ip addr show    
lo (local loopback) используется для того, чтобы компьютер мог обращаться к самому себе и имеет по умолчанию ip-адрес 127.0.0.1 на всех компьютерах.
![./Screenshots/12.png](./Screenshots/12.png)
 
7. Получение ip-адреса устройства от DHCP сервера   
   DHCP - Dynamic Host Configuration Protocol - протокол, использующийся для автоматического выставления различной конфигурации, в том числе IP-адресов.
![./Screenshots/13.png](./Screenshots/13.png)

8. Внешний ip-адрес шлюза
![./Screenshots/14.png](./Screenshots/14.png)

9. Установка статичных настроек ip, gw, dns
![./Screenshots/15.png](./Screenshots/15.png)

10. После перезагрузки виртуальной машины, настройки не изменились. 
Пингование удаленных хостов 1.1.1.1 и ya.ru прошло успешно.
![./Screenshots/16.png](./Screenshots/16.png)
![./Screenshots/17.png](./Screenshots/17.png)

## Part 4. Обновление ОС

Команда apt update обновляет индекс пакетов в системе Linux или списки пакетов.   
Команда apt upgrade обновляет пакеты программного обеспечения до последних версий
1. Обновление индексов при помощи команды sudo apt update
![./Screenshots/18.png](./Screenshots/18.png)

2. После обновления системных пакетов при помощи команды sudo apt upgrade, проводим проверку на необходимость обновления
![./Screenshots/19.png](./Screenshots/19.png)
![./Screenshots/20.png](./Screenshots/20.png)

## Part 5. Использование команды **sudo**

Команда sudo ( substitute user and do, подменить пользователя и выполнить ) позволяет строго определенным пользователям выполнять указанные программы с административными привилегиями без ввода пароля суперпользователя root.
1. Смена hostname от имени пользователя, созданного в пункте Part2.        
![./Screenshots/21.png](./Screenshots/21.png)

## Part 6. Установка и настройка службы времени

1. Вывод команды timedatectl show, показывающая время часового пояса.
![./Screenshots/22.png](./Screenshots/22.png)

## Part 7. Установка и использование текстовых редакторов 

1. VIM
- :wq - выход из VIM с сохранением
![./Screenshots/23.png](./Screenshots/23.png)
- :q! - выход из VIM без сохранения
![./Screenshots/24.png](./Screenshots/24.png)
- /School - поиск слова
![./Screenshots/25.png](./Screenshots/25.png)
- :s/School/biba and boba - замена слова на другое
![./Screenshots/26.png](./Screenshots/26.png)

2. NANO
- Control + X -> Y -> Enter - последовательность для выхода с сохранением
![./Screenshots/27.png](./Screenshots/27.png)
- Control + X -> N - последовательность для выхода без сохранения
![./Screenshots/28.png](./Screenshots/28.png)
- Control + W - поиск слова
![./Screenshots/29.png](./Screenshots/29.png)
- Control + \ -> ввод слова для поиска -> Enter -> ввода слова для замены -> Enter -> Y -> Enter
![./Screenshots/30.png](./Screenshots/30.png)

3. JOE
sudo apt install joe
- Control + K -> Q -> Y - последовательность для выхода с сохранением
![./Screenshots/31.png](./Screenshots/31.png)
- Control + K -> Q -> N - последовательность для выхода без сохранения
![./Screenshots/32.png](./Screenshots/32.png)
- Control + K -> F + r -> new -> Y - последовательность для выхода без сохранения
![./Screenshots/33.png](./Screenshots/33.png)
## Part 8. Установка и базовая настройка сервиса **SSHD**
1. Установка службы SShd при помощи команды sudo apt-get install ssh
![./Screenshots/34.png](./Screenshots/34.png)
2. Включение автостарта службы при загрузке системы при помощи команды sudo systemctl enable ssh
![./Screenshots/35.png](./Screenshots/35.png)
3. sudo vim /etc/ssh/sshd_config - замена порта 22 на 2022
![./Screenshots/36.png](./Screenshots/36.png)
4. ps - выводит список текущих процессов на сервере.
    Флаги:                
   -A, -e, (a) - выбрать все процессы;      
   -a - выбрать все процессы, кроме фоновых;   
   -d, (g) - выбрать все процессы, даже фоновые, кроме процессов сессий;   
   -N - выбрать все процессы кроме указанных;         
   -С - выбирать процессы по имени команды;        
   -G - выбрать процессы по ID группы;        
   -p, (p) - выбрать процессы PID;         
   --ppid - выбрать процессы по PID родительского процесса;       
   -s - выбрать процессы по ID сессии;          
   -t, (t) - выбрать процессы по tty;       
   -u, (U) - выбрать процессы пользователя.       

Наличие процесса sshd.
![./Screenshots/36.png](./Screenshots/37.png)

5. Вызов команды netstat -tan
![./Screenshots/38.png](./Screenshots/38.png)
   -a - Отображение всех подключений и ожидающих портов      
   -n - Отображение адресов и номеров портов в числовом формате       
   -t - Отображение текущего подключения в состоянии переноса нагрузки с процессора на сетевой адаптер при передаче данных ( "offload" )  
   0.0.0.0 означает, что подключение может быть выполнено с/на любой адрес   
   LISTEN - готовность к установке соединения

## Part 9. Установка и использование утилит **top**, **htop**

1. Вызов команды top
![./Screenshots/39.png](./Screenshots/39.png)
Сортировка по %MEM
![./Screenshots/40.png](./Screenshots/40.png)
Сортировка по %CPU
![./Screenshots/41.png](./Screenshots/41.png)
   - uptime = 8 min
   - user - 1
   - общая загрузка системы - 0, 0, 0
   - общее количество процессов - 109
   - загрузка cpu - 0
   - загрузка памяти - 169.8
   - pid память - 1378
   - pid cpu - 1563

2. Вызов команды htop
 - Сортировка по PID
![./Screenshots/42.png](./Screenshots/42.png)
 - Сортировка по PERCENT_CPU
![./Screenshots/43.png](./Screenshots/43.png)
 - Сортировка по PERCENT_MEM
![./Screenshots/44.png](./Screenshots/44.png)
 - Сортировка по TIME
![./Screenshots/45.png](./Screenshots/45.png)
 - Фильтр по процессу sshd
![./Screenshots/46.png](./Screenshots/46.png)
 - Процесс syslog
![./Screenshots/47.png](./Screenshots/47.png)
 - hostname, clock, uptaime
![./Screenshots/48.png](./Screenshots/48.png)

## Part 10. Использование утилиты **fdisk**
1. Запуск команды fdisk -l
   - Название жесткого диска - /dev/sda
   - Размер жесткого диска - 20 GiB
   - Количество секторов - 41943040
![./Screenshots/49.png](./Screenshots/49.png)
2. Размер swap
![./Screenshots/50.png](./Screenshots/50.png)

## Part 11. Использование утилиты **df** 
1. Запуск команды df
    - Размер раздела - 10218772
    - Размер занятого пространства - 4600004
    - Размер свободного пространства - 5078096
    - Процент использования - 48%
    - Единица измерения - Кб
![./Screenshots/51.png](./Screenshots/51.png)

2. Запуск команды df -Th
   - Размер раздела - 9.8 Гб
   - Размер занятого пространства - 4.4 Гб
   - Размер свободного пространства - 4.9 Гб
   - Процент использования - 48%
   - Единица измерения - Гб
![./Screenshots/52.png](./Screenshots/52.png)

## Part 12. Использование утилиты **du**

1. Вывод команды du       
![./Screenshots/53.png](./Screenshots/53.png)

2. Вывод размера папок /home, /var, /var/log
![./Screenshots/54.png](./Screenshots/54.png)

3. Вывод размеров всего содержимого в /var/log
![./Screenshots/55.png](./Screenshots/55.png)

## Part 13. Установка и использование утилиты **ncdu**

Установка ncdu при помощи команды sudo apt install ncdu
1. Вызов команды ncdu
![./Screenshots/56.png](./Screenshots/56.png)
2. Размер папки /home
![./Screenshots/57.png](./Screenshots/57.png)
3. Размер папки /var
![./Screenshots/58.png](./Screenshots/58.png)
4. Размер папки /var/log
![./Screenshots/59.png](./Screenshots/59.png)

## Part 14. Работа с системными журналами

1. Просмотр /var/log/dmesg
![./Screenshots/60.png](./Screenshots/60.png)
2. Просмотр /var/log/syslog
![./Screenshots/61.png](./Screenshots/61.png)
3. Просмотр /var/log/auth.log
![./Screenshots/62.png](./Screenshots/62.png)
4. Время последней успешной авторизации, имя пользователя и метод входа в систему.
![./Screenshots/63.png](./Screenshots/63.png)
5. Перезапуск системы SSHd
![./Screenshots/64.png](./Screenshots/64.png)

## Part 15. Использование планировщика заданий **CRON**

1. Установка задачи uptime
![./Screenshots/65.png](./Screenshots/65.png)
