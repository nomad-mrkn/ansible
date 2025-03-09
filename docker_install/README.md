Роль по установке Docker
Запуск плейбука в зависимости от режима Docker.
Если необходим Docker rootfull:
ansible-playbook playbooks/docker_install.yml -l <inventory_hostname> --tags docker_rootfull
Устанавливаются:

docker-ce={{ docker_version }}
docker-ce-cli={{ docker_version }}
containerd.io
docker-buildx-plugin
docker-compose-plugin
python3-docker

Если необходим Docker rootless:
ansible-playbook playbooks/docker_install.yml -l <inventory_hostname> --tags docker_rootless
Устанавливаются:

uidmap
dbus-user-session
slirp4netns
fuse-overlayfs
docker_rootless
docker-compose-plugin
python3-docker

ВАЖНО
После установки docker_rootless все контейнеры будут запускаться от имени docker_user. Все директории, конфиги и иные файлы должны быть настроен с соответствующими правами
