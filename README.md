# rabota_diploms

1. Образ Ubuntu - так как много софта, много пакетов, легко устанавливать.
-----
2. графический редактор  
```
GIMP - apt install gimp
inkscape - apt install inkscape
Вместо КОМПАС-3D берем, freecad, так как он более лучше и мощней, плюс менее прожорлив к ресурсам. -  apt install freecad
Вместо 3D-Paint берем blender, лучше, гибче и больше возможностей, менее прожорлив -  apt install blender
NanoCAD нет смысла устанавливать, так как все те же функции выполняет и freecad
```
-----
3. пакет программ
```
libreoffice ставим - apt install libreoffice 
```
включает в себя уже полный набор программ
Writer (аналог Word)
Calc (аналог Excel)
Impress (аналог PowerPoint)
Draw (векторная графика)
Base (базы данных)
Math (редактор формул)
-----
4. архиватор
Ставим стандартный zip и 7-zip
```
apt install zip
apt install 7zip
```
-----
5. утилита
Ставим для администратора и клиента htop, позволяет мониторить нагрузку на ядра, cpu, ram и тд.
CPU-Z аналог ставим более верткий с возможностью выгрузки в html формат информации об устройстве + есть UI, программа hardinfo - apt install hardinfo
GPU-Z аналог ставим, apt install psensor

------
6. антивирус
Все из перечисленных в задание не соответствуют требования: есть платные версии, есть без обновляемых версий, нам подходит clamav clamav-daemon clamtk
Плюсы: обновляемые базы, автозапуск сканирования, не сильно нагружает систему по сравнению с Касперским.
```
apt install clamav clamav-daemon clamtk
```
имеет UI , через clamtk

------
7. среда разработки 
выбираем Visual Studio code, так у него ряд преимуществ перез другими:
понятный интерфейс
из коробки доступны интеграции с git
Поддержка мультиязыков
Легковесный, не грузит систему.
```
apt install software-properties-common apt-transport-https wget
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
apt update
apt install code
```

Для андроида ставим 
```
apt install snapd
snap install android-studio --classic
```

8. СУБД
Выбираем PostgreSQL
Преимущества:
масштабируемый, есть настройка репликаций
более верткий по сравнению с конкурентами.
```
apt install postgresql
```
-----

Установка виртуального принтера:
```
apt install cups-pdf
```
Для проверки работы можно открыть LibreOfice и тыкнуть распечатать.
Файл pdf сохраниться в /home/ваш_пользователь/PDF

-----

Настройка удаленного стола:
```
apt install xrdp
```
nano /etc/xrdp/startwm.sh
вставить туда
```
export DESKTOP_SESSION=ubuntu
export GNOME_SHELL_SESSION_MODE=ubuntu
export XDG_CURRENT_DESKTOP=ubuntu:GNOME
```

systemctl status xrdp-sesman (проверка оболочки графики)
systemctl status xrdp (статус работы сервера xrdp)

-----
Настройка журнала логов
nano /etc/systemd/journald.conf
```
SystemMaxUse=500M    # Максимальный размер логов
MaxRetentionSec=1month  # Хранить логи 1 месяц
```
-----

Создаем пользователя
```
adduser username1
```

Создание группы
```
groupadd officeusers
```

Добавление пользователя в группу
```
usermod -aG officeusers username1
```

Проверим что пользователь добавлен в группу
```
groups username1
```


Находим путь к LibreOffice
```
which libreoffice
```

Даём группе право на исполнение:
```
sudo chown :officeusers /usr/bin/libreoffice
sudo chmod 750 /usr/bin/libreoffice
```



