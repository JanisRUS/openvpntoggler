# # Переключатель соединения OpenVPN

Небольшой набор скриптов для переключения соединения OpenVPN 3 client как через CLI, так и через ярлык

# Зависимости для запуска

- Ubuntu 22.04 и выше или Debian 12 и выше

- Использующее `gdbus` рабочее окружение

# Зависимости для сборки

- `build-essential`

- `debhelper`

- `devscripts`

Опциональные зависимости

- `docker`

```bash
sudo apt install build-essential debhelper devscripts
```

# Сборка

Нативная сборка:

```bash
scripts/build-native
```

Автоматическая сборка в Docker-контейнере:

```bash
scripts/build-docker <IMAGE>
```

> IMAGE- название базового Docker образа. По умолчанию: ubuntu:24.04

Сборка Docker-образа для ручной сборки:

```bash
docker build -t open-vpn-builder --build-arg BASE_IMAGE=<IMAGE> --build-arg UID=$(id -u) --build-arg GID=$(id -g) -f Dockerfile.manual .
```

> IMAGE- название базового Docker образа. По умолчанию: ubuntu:24.04
> 
> UID- ID пользователя. По умолчанию: 1000
> 
> GID- ID группы. По умолчанию: 1000

Собранный пакет будет находиться в директории `output`

# Установка

```bash
sudo apt install ./output/open-vpn-toggler-prepare*.deb && \
sudo apt update                                         && \
sudo apt install ./output/open-vpn-toggler_*.deb
```

# Использование

Укажите свой `.ovpn` файл:

```bash
open-vpn-set-config <FILE>
```

Запуск через CLI:

```bash
open-vpn-toggler
```

Запуск через ярлык:

```
Нажмите на ярлык 
```

Статус подключения индицируется цветом иконки ярлыка и увеломлениями.

# Удаление

```bash
sudo apt remove open-vpn-toggler*
```

# Устранение неполадок

Все возникающие во время работы скриптов ошибки будут записываться в `.log` файл. Путь до `.log` файла будет выведен в терминал при возникновении ошибки

# TODO

- 
