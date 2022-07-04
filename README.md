# Micropython_example


![alt text](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4e/Micropython-logo.svg/1200px-Micropython-logo.svg.png)

MicroPython — это компактная и эффективная реализация языка программирования Python 3, включающая небольшое подмножество стандартной библиотеки Python и оптимизированная для работы на микроконтроллерах и в ограниченных средах.

MicroPython содержит множество расширенных функций, таких как интерактивная подсказка, целые числа произвольной точности, замыкания, понимание списков, генераторы, обработка исключений и многое другое. Тем не менее, он достаточно компактен, чтобы поместиться и работать всего на 256 КБ пространства кода и 16 КБ ОЗУ.

MicroPython стремится быть максимально совместимым с обычным Python, чтобы вы могли легко переносить код с рабочего стола на микроконтроллер или встроенную систему.

* [micropython документация](http://docs.micropython.org/en/latest/library/index.html)

# Micropython - Перепрошивка платы

Нам надо скачать прошивку для нашей платы, я буду показывать на примере платы esp8266, но данная схема будет работать со всеми платами с поддержкой микропайтон. Открываем браузер и переходим на сайт micropython.org/download тут ищем прошивку для нужной платы. Заметьте что тут есть три версии для esp8266, отличаются они в флэш памяти. Выбираем актуальную версию и скачиваем.

* [Прошивка для ESP8266](https://micropython.org/download/esp8266-1m/)

Для установки прошивки нам нужна специальная утилита, скачиваем ее командой 
```sh
pip install esptool 
```

Далее вводим команду для очистки памяти платы
```sh
esptool.py --port /dev/ttyUSB0 erase_flash
```

Но если у вас появляется ошибка, тогда введите следующую команду.
```sh
sudo chmod a+rw /dev/ttyUSB0
```

Вводим команду для перепрошивки платы. Проверьте порт, скорость порта должна быть 460800 если будут ошибки, тогда понизьте скорость до 115200. И обязательно укажите путь к файлу прошивки. Отправляем команду и плата перепрошита.
```sh
esptool.py --port /dev/ttyUSB0 --baud 460800 write_flash --flash_size=detect 0 /home/stanislav/Загрузки/esp8266-1m-20220618-v1.19.1.bin
```


Как я говорил ранее, микропайтон поддерживает функцию интерактивная подсказка, это значит что мы можем вводить код и плата сразу же будет его выполнять. Для этого мы можем использовать программу teraterm для виндовс, screen для Mac и picocom или minicom для Линукс. Установим picocom на линукс. У меня есть список команд для его установки на арч Линукс, дебиан, убунту и федора Линукс.

Выполняем нужные вам команды и идём тестировать.

Arch Linux
```sh
sudo pacman -Sy
sudo pacman -S picocom
```

Debian Linux
```sh
sudo apt-get update
sudo apt-get install picocom
```

```sh
sudo apt update
sudo apt -y install picocom
```

Fedora Linux
```sh
sudo dnf makecache --refresh
sudo dnf -y install picocom
```

picocom /dev/ttyUSB0 -b115200

https://randomnerdtutorials.com/esp32-esp8266-micropython-web-server/

Install Thonny
https://www.tecmint.com/thonny-python-ide/
bash <(curl -s https://thonny.org/installer-for-linux)

change from python to micropython
