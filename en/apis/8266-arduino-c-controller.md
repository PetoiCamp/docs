# 🦎 8266 Arduino C Controller

Since the ESP8266 can be used as a regular Arduino board, we can write a simple Arduino code to open the serial port and send the serial commands to control the robot. It's like a stand-alone serial commander written in C and can go with the robot. You may write hundreds of pre-defined tasks without worrying about the memory limits on the main controller.&#x20;

You can find a short [test8266Master](https://github.com/PetoiCamp/OpenCat/tree/main/ModuleTests/test8266Master) in OpenCat/ModuleTest:

```clike
void setup() {
  // put your setup code here, to run once:
  Serial.begin(115200);
  Serial.setTimeout(5);
  bool connected = false;
  while (!connected) {
    Serial.print("b 20 8 22 8 24 8");
    for (byte t = 0; t < 100; t++) {
      if (Serial.available())
        if (Serial.read() == 'b') {
          connected = true;
          while (Serial.available() && Serial.read())
            ;
          break;
        }
      delay(10);
    }
    delay(1000);
  }
}

void sendCMD(const char cmd[], int wait = 0) {
  Serial.print(cmd);
  while (true) {
    if (Serial.available() && toLowerCase(Serial.read()) == cmd[0]) {
      delay(10);
      while (Serial.available() && Serial.read())
        ;
      break;
    }
    delay(2);
  }
  delay(wait);
}

void loop() {
  sendCMD("d", 500);                    //rest and wait 0.5 seconds 趴下并等待0.5秒
  sendCMD("khi");                       //greetings 打招呼
  sendCMD("kpu");                       //pushups 俯卧撑
  sendCMD("kvtF", 1000);                //stepping 原地踏步
  sendCMD("G");                         //Turn off the gyro 关闭陀螺仪
  sendCMD("kwkF", 1500);                //walk 行走
  sendCMD("kck");                       //check 观察
  sendCMD("kpu1");                      //push ups with on hand 单手俯卧撑
  sendCMD("kvtR", 2000);                //spin 旋转
  sendCMD("G", 100);                    //turn on the gyro 打开陀螺仪
  sendCMD("ktrF", 1500);                //trot 跑步
  sendCMD("kjy", 0);                    //joy 加油
  sendCMD("i 0 45 8 -90 9 -90", 1000);  //rotate the head and arm joints 伸手转头
  sendCMD("ksit", 1000);                //sit 坐下
}
```
