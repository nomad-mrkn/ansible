# Роль certbot-route53

Роль устанавливает certbot и плагин для route53, настраивает подключение к aws, выпускает сертификаты (опционально).

Для работы роли обязательно требуется указать данные для aws:

```
aws_access_key_id: 'AKIAIOSFODNN7EXAMPLE'
aws_secret_access_key: 'wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY'
```

```
А также домены:

```
certbot_route53_domains: [ 'example.com', '*.example.com' ]
```
Не пугаемся, что нет в роли добавление строчки в кронтаб - в пакете certbot есть таймер, который периодически вызывает renew. Каждый сервис должен сам класть хуки для деплоя/передергивания себя, если он пользует сертификаты.

Назначить хук можно при помощи параметра
```
certbot_route53_deploy_hook: /usr/sbin/nginx -s reload
```
