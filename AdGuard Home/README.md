# Установить AdGuard Home


1. Обновим пакеты
```bash
opkg update
```

2. Установка
```bash
opkg install adguardhome-go
```

3. Отключаем системный DNS сервер
``` bash
ndmc -c opkg dns-override
# Opkg::Manager: DNS override enabled.
```

4. Применить настройки
``` bash
ndmc -c system configuration save
# Core::System::StartupConfig: Saving (cli).
```

5. Далее запускаем AdGuard Home идём по пути /opt/etc/init.d/
и находим скрипт S99adguardhome.sh 

```bash
"/opt/etc/init.d/S99adguardhome" start
# Starting AdGuardHome...              done.
```

6. Переходим в админку по адресу:
``` bash
https://адрес_вашего_роутера:3000
```

7. Отключаем логи в файле /opt/etc/AdGuardHome/adguardhome.conf
8. 
```bash
# Убираем $LOG из строки
 OPTIONS="$DIR $PID $UPD"
```

```bash
# Restart
"/opt/etc/init.d/S99adguardhome" restart
# Shutting down AdGuardHome...              done.
# Starting AdGuardHome...              done.
```

9. В настройках DNS в AdGuard Home
"Настройки DNS" добавьте:
```bash
tls://dns.adguard-dns.com
tls://dns.quad9.net
tls://dns.google
```
