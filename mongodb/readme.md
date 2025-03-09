# Роль для создания контейнера и кластера mongodb
```
cluster_group: "{{ name_group_vars | default('mongo_cluster') }}" - проверяет inventory и берёт оттуда нужную группу
```
```
cluster: "{{ is_cluster | default('false') }}" - переменная, которая отвечает за прокатку задания create_cluster. в случае необходимости развернуть кластер, в main.yml выставлено условие " when: cluster" 
```
```
certbot: "{{ is_certbot | default( false ) }}" - переменная, которая отвечает за запуск роли certbot-route53. используется в create_container.yml
```
```
certbot_route53_deploy_hook: "{{ mongo_path }}/recreate_ssl.sh" - вебхук, который необходим для задания Create LE challenge to get certs из роли certbot-route53
```