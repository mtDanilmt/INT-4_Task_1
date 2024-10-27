# INT-4_Task_1
Для первого задания INT-4(Ansible)

Всем машинам стоит установить статический IP-адрес. 

## Окружение

1. **Две виртуальные машины с Debian**
2. **Запуск playbook Ansible происходит с Kali Linux**


## Необходимые команды для запуска Ansible:


Установим python3

```
sudo apt update
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

Ввести команду: 

```
sudo apt-get install sshpass
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

- **Файл ansible.cfg**:
  - Определяет путь к файлу inventory с списком хостов.
  - Отключает проверку SSH-ключей для хостов, что полезно при подключении к новым или изменённым серверам.

- **Файл init.sql**:
  - Содержит команды для создания тестовых таблиц в тестовой БД.

- **Файл inventory**:
  - Список управляемых хостов и учётные данные для Ansible.

- **Файл vars.yml**:
  - Переменные окружения, аналог .env (в репозиторий добавлено осознанно для видимости данных).

- **Файл playbook_db.yml**:
  - Основной playbook для выполнения задач.



## Траблшутинг:

Если у вас не устанавливается ansible нужно создать вирутальное окружение, для этого в корне нужно прописать: 

```
apt install python3-venv
python3 -m venv .venv
source .venv/bin/activate
```

Затем ввести ещё раз командку установки ansible:

```
pip3 install ansible 
```










