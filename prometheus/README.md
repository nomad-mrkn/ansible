### Роль для установки контейнеров prometheus, blackbox_exporter, alertmanager

Запуск роли: `ansible-playbook playbooks/prometheus.yml -D --tags <tag>`

Теги для установки: `prometheus_install`, `blackbox_install`, `alertmanager_install`

Теги для перезапуска контейнера: `prometheus_container`, `blackbox_container`, `alertmanager_container`

Все конфиги-переменные находятся в `/main_role/environments/all/host_vars/prometheus.yml`
