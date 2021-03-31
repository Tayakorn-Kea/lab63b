##  การทดลองที่ 7 การใช้Microcontrollerสร้าง Wifi และ Web Server จากนั้นควบคุมการเปิด-ปิดไฟLEDด้วยปุ่ม Yes-No ใน Web server <br>
<br>
```
#include <ESP8266WiFi.h>

const char* ssid = "ESP_8266";
const char* password = "123456789";

WiFiServer server(80);

String header;

const int output5 = 5;
const int output4 = 4;
String output5State = "off";
String output4State = "off";

void setup() {
pinMode(output5, OUTPUT);
pinMode(output4, OUTPUT);

digitalWrite(output5, LOW);
digitalWrite(output4, LOW);
WiFi.mode(WIFI_AP); 
WiFi.softAP("ESP_8266"); 
server.begin();
}
```
