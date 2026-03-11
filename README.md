# Домашнее задание к занятию "`Система мониторинга Zabbix`" - `Юртаева Софья`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1

![Скриншот 1](https://github.com/YurtaevaSofia/hw-02/blob/main/img/img1.png) 
```
1. Установка PostgreSQL
sudo apt updat
sudo apt install postgresql -y

2. Подключение репозитория zabbix 
wget https://repo.zabbix.com/zabbix/7.2/release/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.2+ubuntu24.04_all.deb
sudo dpkg -i zabbix-release_latest_7.2+ubuntu24.04_all.deb
sudo apt update

3. Установка Zabbix сервера, веб-интерфейса и агента
sudo apt install -y zabbix-server-pgsql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts zabbix-agent

4. Создание БД и юзера
sudo -u postgres psql

5. Импорт схемы данных
zcat /usr/share/zabbix/sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix

6. Настройка пароля в конфиге Zabbix сервера
sudo nano /etc/zabbix/zabbix_server.conf

7. Запуск сервисов и добавление в автозагрузку
sudo systemctl restart zabbix-server zabbix-agent apache2
sudo systemctl enable zabbix-server zabbix-agent apache2
```
---

### Задание 2

![Скриншот 2](https://github.com/YurtaevaSofia/hw-02/blob/main/img/img2.png) 
![Скриншот 3](https://github.com/YurtaevaSofia/hw-02/blob/main/img/img3.png) 
![Скриншот 4](https://github.com/YurtaevaSofia/hw-02/blob/main/img/img4.png) 

```
*** Использованные команды ***
sudo systemctl restart zabbix-server
sudo systemctl status zabbix-server
sudo tail -30 /var/log/zabbix/zabbix_server.log
sudo systemctl restart zabbix-agent
sudo systemctl status zabbix-agent
sudo tail -30 /var/log/zabbix/zabbix_agentd.log
sudo systemctl restart zabbix-agent2
sudo systemctl status zabbix-agent2
sudo tail -30 /var/log/zabbix/zabbix_agentd2.log
sudo ss -tulpn | grep 1005
ps aux | grep zabbix_agentd
zabbix_get -s 127.0.0.1 -p 10050 -k agent.ping
zabbix_get -s 127.0.0.1 -p 10052 -k agent.ping
```

---

