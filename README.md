### Luck_fox_pro_max_cv
Я пишу эту иструкцию, чтобы, как миниимум, не забыть самому, что и как я делал для курсача по АСВТ
## Установка образа с сайта 
## ADB shell
## Кросс-компилятор
Так как для выполнения работы нужна камера - необходимо использовать ОС buildroot, а не ubuntu, поэтому, используется кросс-компиллятор uclibc
https://files.luckfox.com/wiki/Luckfox-Pico/Software/arm-rockchip830-linux-uclibcgnueabihf.tar.gz - ссылка на скачивание
После установки:
```
tar zxvf arm-rockchip830-linux-uclibcgnueabihf.tar.gz -C ~/
```
теперь можно компиллировать программы на языке с/с++ на своем компьютере и загружать исполняемый файл на luckfox.
например, можно сделать простой файл на с++ helllo.cpp
```
#include <iostream>
#include <string>

int main() {
    std::string msg = "Hello from C++ on Luckfox Pico Max!";
    std::cout << msg << std::endl;
    return 0;
}
```
После, можно сделать исполняемый файл при помощи кросс-компиятора
```
arm-rockchip830-linux-uclibcgnueabihf-gcc hello.cpp -o hello
```
Полученный исполняемый файл можно отправить на плату 
```
adb push hello /root
```
Подсоединившись к плате через ADB можно запустить полученый исполняемый файл, который будет находиться по расположеню /root
```
./hello
```
