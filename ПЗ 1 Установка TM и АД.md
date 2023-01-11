# Traffic-Monitor
# ПЗ 1 Установка TM и АД
https://youtu.be/zmpi4cYk0g0
1. Установка CentOS и Traffic Monitor
1.	При создании ВМ с CentOS задать 8 ядер, 8 гб ОЗУ и 600 гб дискового пространства thin provision. При установке разметить диск в режиме Standard Partition:
Раздел "/" - 100 gib
Раздел "/boot" - 1 gib
Раздел "/opt" - 100 gib
Раздел "/tmp" - 50 gib
Раздел "/var" - 80 gib
Раздел "/u01" - 80 gib
Раздел "/u02" - 100 gib
Раздел "/u03" - 80 gib
Раздел "swap" - 8 gib
/Обязательно писать gib, иначе диск разметится неправильно.
![image](https://user-images.githubusercontent.com/83372679/211775857-615ec32a-ab41-4a9e-b531-bbba90e5dc35.png)
![image](https://user-images.githubusercontent.com/83372679/211775906-6d2734a1-c7c7-408f-8e73-b23534efe2ba.png)
2.	Также включить адаптер интернета, задать hostname (iwtm) и если известны IP, шлюз, DNS-сервер.
3.	Задать время, лучше оставить английский язык, после начала установи задать root пароль. После установки системы зайти под пользователем root.

Если IP, шлюз и DNS, hostname не были заданы при установке CentOS, то надо проделать следующие действия
4.	Через vi отредактировать файл   
![image](https://user-images.githubusercontent.com/83372679/211776002-c05dfe33-1e53-4ad8-8f8e-8bb46b73f5e5.png)
/ens192 – адаптер demo
![image](https://user-images.githubusercontent.com/83372679/211776030-856586f2-e2b3-4407-b086-ade06ce207dc.png)
В /etc/hostname задать название iwtm

Установка Traffic Monitor
Проверить чтобы /etc/hosts  выглядел так: свой ip – iwtm, ip IW-DEMO-AD – demolab (имя домена)
 ![image](https://user-images.githubusercontent.com/83372679/211776169-ba421d9c-c240-4d1f-a87d-52c91b204991.png)
/Управление редактором VI – INSERT (править текст), ESC (выйти из мода правки), ctrl+С (выход), :wq (w-сохранить, q-выйти) или же :q! (когда надо выйти без сохранения)
5.	После внесения изменений перезагрузить ВМ, чтобы настройки применились
6.	Установить редактор нано yum -y install nano (он удобнее)
7.	Подключить к IW-TM диск TM.iso
8.	Создать директорию через mkdir tm и подключить к ней диск командой mount /dev/cdrom tm
9.	Перейти в каталог cd tm/TM/RHEL и запустить установку ./itwm-in (tab)
 ![image](https://user-images.githubusercontent.com/83372679/211776204-9b05ad3c-0360-4618-af1e-85d48a2bf7d1.png)
//Если будут ошибки, надо проверить связь с 8.8.8.8 и ya.ru, если нет сети, проверить корректность настроек интернета, если всё также не воркает, переустанавливать в точном порядке, как описано.
10.	После распаковки в настройках выбрать SQL – PostgresSQL, версия All - in - One  Entreprise, Server NTP выбрать manual и ввести ntp1.stratum2.ru, дальше со всем соглашаться.
/Для выбора надо нажать пробел
 ![image](https://user-images.githubusercontent.com/83372679/211776243-1752f6ee-c802-4bdb-b6f4-d41b64744aea.png)
 ![image](https://user-images.githubusercontent.com/83372679/211776295-a9042787-69a0-469a-bee7-0226da13b289.png)
![image](https://user-images.githubusercontent.com/83372679/211776305-8728b98d-9287-488e-9f21-ab5b72684198.png)
![image](https://user-images.githubusercontent.com/83372679/211776317-3cf1fb7c-b999-4e2c-8fc6-6bd2f67f32d8.png)
![image](https://user-images.githubusercontent.com/83372679/211776329-6b6abb7c-c0ad-43fe-ab2f-9fc0e3173f2e.png)

Далее со всем соглашаться
11.	После установки зайти через IP второго интерфейса с хрома на основной машине, и проверить доступность сайта. 
 ![image](https://user-images.githubusercontent.com/83372679/211776355-fcd4025b-9d6a-4762-8996-639366b7b168.png)

/login: officer password: xxXX1234
 

Опциональная инфа для того чтобы поднять доступ к интернету через NAT (по идее должно быть настроено за тебя)
12.	На IW-DEMO-AD добавить роль сервера «удаленный доступ», далее «маршрутизация»
 ![image](https://user-images.githubusercontent.com/83372679/211776400-3de15ce9-99d4-4bcd-a440-f6fb71ccde38.png)

13.	Затем средства -> маршрутизация и удаленный доступ, запустить DEMOLAB (в первый раз не появится IP-адресов, отменить, во второй раз выбрать внешний IP, который глядит в интернет)
 ![image](https://user-images.githubusercontent.com/83372679/211776427-7d7f533e-f715-4e7d-a808-952df6701ece.png)

14.	Добавить интерфейс, глядящий в интернет в пункте «преобразование сетевых адресов»
 ![image](https://user-images.githubusercontent.com/83372679/211776448-df83e4b0-7508-42e6-aafa-d2013e478cee.png)
