# avr cross compile

This cross compiles and flashes to a arudino nano. It is a simple LED blink program.

The reason I made this is to get more familar with cross compiling in general.

If working in wsl2, do [this](https://github.com/dorssel/usbipd-win/wiki/WSL-support) and [this](https://docs.microsoft.com/en-us/windows/wsl/connect-usb) to access the serial port on the windows 10 host.

```bash
# compiler, libraries, programmer, arduino libraries
apt-get install gcc-avr avr-libc avrdude arduino-core

# obtained this upload line from viewing the verbose logging output in the arduino ide
avrdude -v -patmega328p -carduino -P/dev/ttyUSB0 -b115200 -D -Uflash:w:avr_cross_compile-atmega328p.hex:i
```