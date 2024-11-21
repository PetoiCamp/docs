# Introduction (For NyBoard)

The Nyboard V1 used by robot uses the Atmel ATMEGA328P controller, which only supports only one serial port. We separate the serial port of Nyboard to support more modules. The pins of the serial port are compatible with the 6-pin Arduino Pro Mini. Pin definitions are shown in the table below:

| Pin No. | Name | Usage                                                           |
| ------- | ---- | --------------------------------------------------------------- |
| 1       | DTR  | Modem signal DTR, reset NyBoard after serial download finished. |
| 2       | RX   | ATMEGA328P RX (receive)                                         |
| 3       | TX   | ATMEGA328P TX (send)                                            |
| 4       | 5V   | 5V power for MCU and chips                                      |
| 5       | GND  | Ground                                                          |
| 6       | GND  | Ground                                                          |

The default serial baud rate is **115200bps**.

There're 3 communication modules for the NyBoard V1:

* [USB uploader](https://docs.petoi.com/communication-modules/usb-downloader-ch340c)
* [Bluetooth](https://docs.petoi.com/communication-modules/dual-mode-bluetooth) dual mode（EDR & BLE）JDY-23
* [WiFi module](https://docs.petoi.com/communication-modules/wifi-esp8266) ESP8266
