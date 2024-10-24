# INT-4_Task_1
Для первого задания INT-4(Ansible)

Всем машимам стоит установить статический ip адрес. 

## Окружение

1. **Две виртуальные машины с Debian**
2. **Запуск playbook Ansible происходит с Kali Linux**


## Необходимые команды для запуска Ansible:


Установим python3

```
sudo apt-get install python3
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 2
```

Установка pip3 и ansible

```
sudo apt install python3-pip
pip3 install ansible
```

Укажем в переменной PATH путь до ansible
```
export PATH=$PATH:/home/user/.local/bin
```


## Команда для запуска playbook:

```bash
ansible-playbook playbook.yml
```

## Необходимые настройки Debian машин для запуска Ansible:

1. Добавить нового пользователя "ansible". (Имя пользователя можно поменять, главное указать его затем в inventory)
2. Добавить строку в /etc/sudoers:

```
ansible ALL=(ALL:ALL) NOPASSWD:ALL
```
3. Установить сервер и клиент OpenSSH и запустить:

```
sudo apt update
sudo apt install openssh-server openssh-client
sudo systemctl enable ssh
sudo systemctl start ssh
```

# Реализуемый функционал playbook:

1. Установка и настройка Fail2Ban для первичной защиты.
2. Установка Webmin для мониторинга хоста.
3. Установка Postgresql-16.
4. Настройка репликации и запуск.
5. Настройка логирования БД.
6. Создание тестовой БД.

# Описание файлов конфигурации и их предназначение:

1. Файл "ansible.cfg" предназачен для:
   1.1 Определяет путь к файлу инвентаря, который содержит список хостов для управления. В данном случае это файл inventory, который находится в той же директории, где расположен конфигурационный файл.
   1.2 Отключает проверку ключей SSH для хостов. Это полезно при частом подключении к новым или измененным серверам, чтобы избежать необходимости подтверждения ключей.
2. Файл "init.sql":
   2.1 Создание тестовых таблиц в тестовой БД.
3. Файл "inventory":
   3.1 Содержит список хостов управления и уч. записи для подключения Ansible
4. Файл "vars.yml":
   4.1 Файлы переменных окружения, аналог .env
5. Файл "playbook_db.yml":
   5.1 Запускаемый playbook.
