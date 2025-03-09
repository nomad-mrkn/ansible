### Роль для установки экспортеров

Запуск роли: `ansible-playbook playbooks/linux_exporters.yml -D -l <inventory_hostname> --tags <tag>`

Теги для установки: `node_exporter`, `container_exporter`

Переменные обозначаются в /main_configs/playbooks/linux_exporters.yml. Для каждого экспортера свой набор переменных, который формируем в блоке экспортера

### Особое внимание на переменные `exporter_use_container`, `exporter_rootfull` и `exporter_install`
Если на сервере установлен Docker и экспортер будет запущен в контейнере - `exporter_use_container: true`. Если экспротрер устанавливается в качестве systemd демона - `exporter_use_container: false`. Если необходимо установить экспортер, то `exporter_install: true`. Для обновления какого-либо параметра/конфига для уже установленного экспортера - `exporter_install: false`

`exporter_rootfull` выставляется `true` или `false` в зависимости от режима запуска, привелигированный `true` или ограниченный `false`.

Переменные `exporter_use_container` и `exporter_rootfull` должны всегда определяться, так как на них завязана вся логика работы роли и порядок выполнения заданий плейбука