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
esptool.py --port /dev/ttyUSB0 --baud 460800 write_flash --flash_size=detect 0 /home/stanislav/Загрузки/esp8266-1m-20220618-v1.19.1.bin

# if error, change 460800 to 115200

To access the prompt over USB-serial you need to use a terminal emulator program. On Windows TeraTerm is a good choice, on Mac you can use the built-in screen program, and Linux has picocom and minicom

sudo pacman -Sy
sudo pacman -S picocom
picocom /dev/ttyUSB0 -b115200

https://randomnerdtutorials.com/esp32-esp8266-micropython-web-server/

Install Thonny
https://www.tecmint.com/thonny-python-ide/
bash <(curl -s https://thonny.org/installer-for-linux)

change from python to micropython
