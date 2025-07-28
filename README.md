# Переключатель соединения OpenVPN

Небольшой набор скриптов для переключения соединения OpenVPN как через CLI, так и через ярлык

# Зависимости для запуска

- Ubuntu 22.04 и выше или Debian 11 и выше

- Совместимое с `libnotify-bin` рабочее окружение

# Зависимости для сборки

- `build-essential`

- `debhelper`

- `devscripts`

```bash
sudo apt install build-essential debhelper devscripts
```

# Сборка

```bash
dpkg-buildpackage -us -uc
```

# Установка

```bash
chmod +x scripts/open-vpn-prepare; \
sudo scripts/open-vpn-prepare;     \
sudo apt install ../openvpntoggler*
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
chmod +x scripts/open-vpn-clear; \
sudo scripts/open-vpn-clear
```

# Устранение неполадок

Все возникающие во время работы скриптов ошибки будут записываться в `.log` файл. Путь до `.log` файла будет выведен в терминал при возникновении ошибки

# TODO

- Найти способ моментального обновления иконки ярлыка в DE

- Сделать уведомления блочными

- Добавить таймаут уведомлений
