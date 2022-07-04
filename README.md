# Micropython_example

MicroPython pyboard — это компактная электронная плата, которая запускает MicroPython на «голом железе», предоставляя вам низкоуровневую операционную систему Python, которую можно использовать для управления всеми видами электронных проектов.

MicroPython содержит множество расширенных функций, таких как интерактивная подсказка, целые числа произвольной точности, замыкания, понимание списков, генераторы, обработка исключений и многое другое. Тем не менее, он достаточно компактен, чтобы поместиться и работать всего на 256 КБ пространства кода и 16 КБ ОЗУ.

MicroPython стремится быть максимально совместимым с обычным Python, чтобы вы могли легко переносить код с рабочего стола на микроконтроллер или встроенную систему.

* [Прошивка для ESP8266](https://micropython.org/download/esp8266-1m/)
* [micropython документация](http://docs.micropython.org/en/latest/library/index.html)

# Micropython - Перепрошивка платы
sudo chmod a+rw /dev/ttyUSB0
pip install esptool
esptool.py --port /dev/ttyUSB0 erase_flash
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
