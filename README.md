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
