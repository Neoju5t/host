# Домашнее задание к занятию "`Система мониторинга Zabbix`" - `Динейко Алексей`


---

### Задание 1

`Установка Zabbix Server с веб-интерфейсом`


```
sudo -s
apt install postgresql
sudo systemctl start postgresql
sudo systemctl enable postgresql
wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest+ubuntu22.04_all.deb
dpkg -i zabbix-release_latest+ubuntu22.04_all.deb
apt update
apt install zabbix-server-pgsql zabbix-frontend-php php8.1-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
sudo -u postgres createuser --pwprompt zabbix

```


1. ![Скриншот-1](https://github.com/Neoju5t/zabbix_1/blob/be9541c6e9d17e73429d895e4f29171053b623be/img/LOGIN%20ZABBIX.JPG)
2. ![Скриншот-2](https://github.com/Neoju5t/zabbix_1/blob/be9541c6e9d17e73429d895e4f29171053b623be/img/ZABBIX.JPG)


---

### Задание 2

`Установка Zabbix Agent на два хоста`

```
sudo -s
wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest+ubuntu22.04_all.deb
dpkg -i zabbix-release_latest+ubuntu22.04_all.deb
apt update
apt install zabbix-agent
systemctl restart zabbix-agent
systemctl enable zabbix-agent

```

![Скриншот-3](https://github.com/Neoju5t/zabbix_1/blob/be9541c6e9d17e73429d895e4f29171053b623be/img/Test2.JPG)
![Скриншот-4](https://github.com/Neoju5t/zabbix_1/blob/be9541c6e9d17e73429d895e4f29171053b623be/img/log.JPG)
![Скриншот-5](https://github.com/Neoju5t/zabbix_1/blob/be9541c6e9d17e73429d895e4f29171053b623be/img/connect%20server.JPG)


---
