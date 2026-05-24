# Установка Podkop
Пакет работает на всех архитектурах.
Будет точно работать только на OpenWrt 24.10.5.

Нужен dnsmasq-full. В автоматическом режиме ставится сам. Вручную надо поставить [самостоятельно](https://github.com/itdoginfo/podkop/blob/952dd6215a2a83d65937cf9e33534c42809091ed/install.sh#L20).

## Автоматическая
```
sh <(wget -O - https://raw.githubusercontent.com/slywater/podkop-v0.2.5/refs/heads/main/install.sh)
```

Скрипт также предложит выбрать, какой туннель будет использоваться. Для выбранного туннеля будут установлены нужные пакеты, а для Wireguard и AmneziaWG также будет предложена автоматическая настройка - прямо в консоли скрипт запросит данные конфига. Для AmneziaWG можно также выбрать вариант с использованием конфига обычного Wireguard и автоматической обфускацией до AmneziaWG.

Для AmneziaWG скрипт устанавливает пакеты из стороннего репозитория [awg-openwrt v24.10.5](https://github.com/Slava-Shchipunov/awg-openwrt/releases/tag/v24.10.5), так как в официальном репозитории OpenWRT они отсутствуют. Устанавливаются `kmod-amneziawg`, `amneziawg-tools`, `luci-proto-amneziawg` и `luci-i18n-amneziawg-ru`. Версия OpenWrt на роутере должна быть `24.10.5`; при другой версии скрипт остановится, чтобы не поставить несовместимый kmod-пакет.

# Обновление
Скрипт обнаружит уже установленный podkop и предложит обновиться. Подтягивается актуальная версия из репозитория [itdoginfo](https://github.com/itdoginfo/podkop)
```
sh <(wget -O - https://raw.githubusercontent.com/itdoginfo/podkop/refs/heads/main/install.sh)
```

# Удаление
```
opkg remove luci-app-podkop podkop
```

Если был установлен русский язык
```
opkg remove luci-i18n-podkop-ru
```
