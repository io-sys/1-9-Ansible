# 09-1 Ansible

### Решение
1. [`Vagrantfile`](https://github.com/io-sys/1-9-Ansible/tree/master/Vagrant/09-1-ansible)  
2. [`Playbook`](https://github.com/io-sys/1-9-Ansible/tree/master/ansible-playbook)  
3. Роль с именем[`nginx_8080port`](https://github.com/io-sys/1-9-Ansible/tree/master/ansible-role/roles/nginx_8080port) создана по `Plabook`'у  


### Домашнее задание: Первые шаги с Ansible
Подготовить стенд на `Vagrant` как минимум с одним сервером. На этом сервере используя `Ansible` необходимо развернуть `nginx` со следующими условиями:  
✅- необходимо использовать модуль `yum/apt`  
✅- конфигурационные файлы должны быть взяты из шаблона `jinja2` с перемененными  
✅- после установки `nginx` должен быть в режиме `enabled` в `systemd`  
✅- должен быть использован `notify` для старта `nginx` после установки  
✅- сайт должен слушать на нестандартном порту - 8080, для этого использовать переменные в `Ansible`  
✅* Сделать все это с использованием `Ansible` роли  
  
Домашнее задание считается принятым, если:  
✅- предоставлен (`Vagrantfile`)[https://github.com/io-sys/1-9-Ansible/tree/master/Vagrant/09-1-ansible] и готовый playbook/роль ( инструкция по запуску стенда, если посчитаете необходимым )  
✅- после запуска стенда `nginx` доступен на порту 8080  
✅- при написании `playbook`/роли соблюдены перечисленные в задании условия  
Критерии оценки: Ставим 5 если создан `playbook`  
Ставим 6 если написана роль.  


### Cheat sheet
```php
ansible web -m ping
```

Скопировать с `web`-сервера файл `nginx.conf`
```php
scp -i /home/vagrant/.ssh/id_rsa vagrant@192.168.11.151:/etc/nginx/nginx.conf .
```

Проиграть одну таску по тегу
```php
ansible-playbook playbook.yml --tags "replace_nginx_conf"
```
Проиграть веcь `playbook`
```php
ansible-playbook playbook.yml
```

```php
ss -ltnp | grep nginx
```

Проверить синтаксис:
```php
ansible-playbook fail2ban.yml --syntax-check
```

Посмотреть список хостов на которых будет выполняться роль. При этом сами таски не выполняются.
```php
ansible-playbook fail2ban.yml --list-hosts
```

Посмотреть все таски, которые входят в роль:
```php
ansible-playbook fail2ban.yml --list-tasks
```

Посмотреть все теги в роли:
```php
ansible-playbook fail2ban.yml --list-tags
```
