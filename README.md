# TS-Conf для ReVerSE-U16 ревизий A и C

### Отличия от оригинальной сборки:

* Добавлен Makefile для автоматической сборки проекта
* Добавлен hdmi_av для вывода звука по hdmi


### Требования к хосту для сборки

* Linux
* установленный Altera Quartus Web Edition 13.0+, 
* директория qurtus/bin добавлена в PATH (чтобы был доступ к quartus_sh, quartus_pgm и т.п. консольным утилитам)
* установленный sjasmplus из [https://github.com/z00m128/sjasmplus](https://github.com/z00m128/sjasmplus) и доступный в PATH
* установленный php-cli не ниже 5.6
* наличие make 
* установленный python

### Порядок сборки 

* **cd syn**
* правим Makefile, если нужно (выбираем ревизию платы, камень, флешку и т.п.)
* **make** - сборка проекта, включая сборку загрузчика и подготовку файлов для конвертации в jic
* **make jic** - сборка jic 
* **make program** - заливка jic через usb blaster в плату
* profit :)

#### Если что-то пошло не так

* make clean
* goto 10

### Запуск проекта
1. Записать в корень на microSD (FAT32) карту файлы из softwares/sd/
2. Записать на microSD образы TRD, SCL, TAP, музыку, другие файлы, поддерживающиеся WC
3. Запрограммировать VNC2 с помощью FT_Prog утилиты образом из vnc2/build/release/ReverseU16_VNC2.rom
4. Влить с помощью Quartus Programmer в плату полученный jic (либо make program)

#### Boot
* При включении загружается Loader. Делаем нужные настройки, нажимаем Enter
* После чего попадаем в настройки TS-Conf. 
* По Shift+F12 попадаем в WC
* Монтируем образ, либо запускаем поддерживающиеся файлы прямо из WC
* F12 - сброс в TR-DOS
* Profit

