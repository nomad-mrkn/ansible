### Роль для установки контейнеров nginx и модуля ldap

Запуск роли: `ansible-playbook playbooks/nginx_ldap.yml -l имя_хоста`

Переменные `{{ fullchain }}` и `{{ privkey }}` хранятся в зашифрованном виде в /main_configs/environments/all/group_vars/all.yml. [Документация модуля](https://github.com/nginxinc/nginx-ldap-auth/tree/master), используемого в роли

Так как на каждом хосте свои настройки, `nginx.conf` хранится в `/main_configs/environments/all/host_vars/имя_хоста.yml`
