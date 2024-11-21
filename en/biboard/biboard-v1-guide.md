# BiBoard V1 Guide

## Introduction

Biboard V1 is a development board based on the high-performance ESP32 MINI 1 module. The module employs an Xtensa dual-core 32-bit LX6 processor featuring 4 MB of Flash memory, 2.4 GHz Wi-Fi, and Bluetooth Low Energy. With its powerful computing capabilities and diverse expansion interfaces, it can meet various projects' personalized needs and complex embedded development requirements. It is widely used in fields such as the Internet of Things, industrial automation, and education and research. Biboard V1 is the ideal choice for any embedded developer.

## Feature

* Real-time high-load power supply
* High-speed UART debugging IC
* Flight Controller-Grade Six-Axis Motion Sensor
* 12-channel PWM servo interface
* Universal extensible interface (Grove socket)
* Stand-alone intelligent voice recognition with bilingual multi-word support
* High-fidelity audio speaker
* Zero-latency, high-sensitivity capacitive touch
* Strong EMC anti-interference and anti-radiation performance

## Specifications

| Specification                  | 	Details                                                        |
| ------------------------------ | --------------------------------------------------------------- |
| Processor                      | ESP32-U4WDH                                                     |
| SRAM                           | 520KB                                                           |
| ROM                            | 448KB                                                           |
| Flash                          | 4MB                                                             |
| External EEPROM                | Customizable                                                    |
| Input Voltage                  | 7 - 9V                                                          |
| Operating voltage              | 5V                                                              |
| Operating current              | 0.1 - 0.2A                                                      |
| Baud rate                      | 115200                                                          |
| Bluetooth protocol             | 4.2 BR/EDR and low energy Bluetooth standard                    |
| Wi-Fi protocol                 | 802.11b/g/n                                                     |
| Onboard Grove expansion socket | UART2, I2C, 4x Analog input                                     |
| Raspberry Pi port              | Support Raspberry Pi 3A+, 4, 5 (need to install a 5-pin socket) |

## Modules and functions

<figure><img src="../.gitbook/assets/image (535).png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="110">Part No.</th><th>Module &#x26; Function</th></tr></thead><tbody><tr><td>1</td><td>Programmable LED [1]</td></tr><tr><td>2</td><td>DC-DC chip</td></tr><tr><td>3</td><td>12 x PWM servo socket</td></tr><tr><td>4</td><td>MPU6050 gyroscope</td></tr><tr><td>5</td><td>Voice command Module</td></tr><tr><td>6</td><td>External EEPROM [2]</td></tr><tr><td>7</td><td>Grove Sockets (G1: UART2; G2: I2C; G3: 2x Analog input; G4: 2x Analog input)</td></tr><tr><td>8</td><td>Speaker</td></tr><tr><td>9</td><td>2.54mm Battery Input</td></tr><tr><td>10</td><td>Raspberry Pi port</td></tr><tr><td>11</td><td>ESP32 Mini</td></tr><tr><td>12</td><td>CH343P serial chip</td></tr><tr><td>13</td><td>BOOT button [3]</td></tr><tr><td>14</td><td>Reset button</td></tr><tr><td>15</td><td>8.4V Power indicator (<mark style="color:orange;">Yellow</mark> LED)</td></tr><tr><td>16</td><td>5V power indicator (<mark style="color:blue;">Blue</mark> LED)</td></tr><tr><td>17</td><td>Touch pad socket</td></tr></tbody></table>

{% hint style="info" %}
\[1]. BiBoard V1 supports 12 PWM servos by default, but if you need to read the feedback angle of the 12th servo (Pin 27), please disconnect **JP1**. After that, LED27 cannot be used.

\[2]. The newest firmware has implemented the external EEPROM's functionality with the built-in flash. You can purchase it elsewhere and solder it to the mainboard if needed. Model: M24C64-FMC6TG.&#x20;

\[3]. If the firmware burning process is interrupted due to external factors, it may lead to a situation where the firmware cannot be burned again. In this case, you need to power off the mainboard, press and hold the BOOT button, and then power on the mainboard again to force the ESP32 into **Download mode**. After the burning process is complete, power on the mainboard again.
{% endhint %}
