# ПЗ 2 Работа с Windows IW-DM и Client
 2. Работа с Windows IW-DM и Client
1.	На IW-DM установить гугл и postgreSQL10 (там всё по дефолту выбирать, stack builder устанавливать не надо)
2.	Настроить IP-адреса для новых ВМ IW-DM, Client следующим образом:
На IW-DM и Client шлюзом и DNS-сервером задать IP-адрес IW-DEMO-AD
![image](https://user-images.githubusercontent.com/83372679/211776812-ee2c2558-46d7-458c-b211-01077573e59b.png)
Пример данных  на IW-DM или Client
![image](https://user-images.githubusercontent.com/83372679/211776845-cb017984-7a03-48d7-9a70-89788bc4ed52.png)
Пример данных на IW-DEMO-AD
3.	Задать домен с сервера IW-DEMO-AD (demo.lab) на IW-DM и Client, ввести логпасс и перезагрузить
![image](https://user-images.githubusercontent.com/83372679/211776990-28034f2e-bffc-415c-a13f-d20d4e9ab23b.png)
Где найти название домена
![image](https://user-images.githubusercontent.com/83372679/211777036-4ff9ec89-5518-4620-967c-74b3dbb4014a.png)
Где ввести домен
4.	Для удобства можно задать имя компьютера, по которому потом можно будет обращаться вместо IP
5.	Перезагрузить ВМ
6.	Проверить успешное подключение, зайдя через созданных пользователей на своих узлах из списка центра администрирвоания на созданных Win-ВМ
3. Добавление пользователей и синхронизация на IW-DEMO-AD
1.	Перейти в центр администрирования Active Directory
![image](https://user-images.githubusercontent.com/83372679/211777150-22a73ed3-1ec0-490e-b850-99a6314bb01e.png)
2.	Создать сначала подразделение, а потом пользователей для WS1 и WS2 в этом подразделении
![image](https://user-images.githubusercontent.com/83372679/211777188-187d0735-945c-4e69-8699-458e825ccd1c.png)
3.	Создать подразделение demooffice, в нем создать два подразделения computers и users.
4.	Перенести компьютеры из паки demo/Computers в demooffice/computers (они там появятся после введения новых ВМ в домен)
![image](https://user-images.githubusercontent.com/83372679/211777220-2a2b8f62-dcc5-4e4b-8a7f-71d5d04f9d3a.png)
5.	Создать пользователей администратора и клиента в active directory и задать им членство
![image](https://user-images.githubusercontent.com/83372679/211777277-a0022327-1eb4-4b21-90b8-c728ec433a73.png)
6.	Для того чтобы задать членство надо вписать в поле domain -> проверить имена и выбрать соответствующее членство админа или пользователя
![image](https://user-images.githubusercontent.com/83372679/211777307-23ccb0a5-746b-4bc2-bb31-f5a9650ff6c4.png)
![image](https://user-images.githubusercontent.com/83372679/211777326-e8a00be8-4b1d-43f4-8aa6-2a1ece626b6e.png)
![image](https://user-images.githubusercontent.com/83372679/211777339-c971dc96-a9b1-4276-a7ac-cf104901f54f.png)
/обратить внимание и сохранить красное выделение, потом понадобится
