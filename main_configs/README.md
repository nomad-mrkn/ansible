## Infra

Основная репа, где хранятся хосты, основные переменные, конфиги, плейбуки и ссылки на роли

Чтобы выкачать роль\роли из git: `ansible-galaxy install -r roles/requirements.yml --force`

Запуск плейбуков происходит из данной репы, например: `/ansible/main_configs$ ansible-playbook playbooks/ssh_settings.yml -l < host_name >`

Есть роли\плейбуки, где используются зашифрованные переменные при помощи ansible vault


### `fast_start.yml`
Плейбук содержит в себе `linux_setup`, `ssh_settings`, `docker_install` и `linux_exporters(node_exporter)`
#### Особое внимание на переменные `exporter_use_container` и `exporter_rootfull` в блоке с переменными для запуска `linux_exporters`
Если на сервере планируется установить Docker и экспортер будет запущен в контейнере - `exporter_use_container: true`. Если экспротрер будет устанавливаться в качестве systemd демона - `exporter_use_container: false`.
`exporter_rootfull` выставляется `true` или `false` в зависимости от режима запуска, привелигированный `true` или ограниченный `false`. Переменная `exporter_install` всегда должна находиться в `true`
Запуск всего плейбука - `ansible-playbook playbooks/fast_start.yml -l <inventory_hostname> --tags docker_rootfull,node_exporter`. Для запуска конкретной части плейбука, используй теги. Часть, содержащая `linux_setup` и `ssh_settings` отрабатывает всегда `tags: always`