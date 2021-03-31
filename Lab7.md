# การทดลองที่ 7 การใช้Microcontrollerสร้าง Wifi และ Web Server จากนั้นควบคุมการเปิด-ปิดไฟLEDด้วยปุ่ม Yes-No ใน Web server <br>
## วัตถุประสงค์
1.เพื่อเข้าใจ code ที่ใช้เขียนลง microcontroller <br>
2.เพื่อเข้าใจ code ที่ใช้เขียนใน web server แบบคร่าวๆ <br>
3.สามารถนำ code จากกาทดลอง1-6 ไปต่อยอดได้ 
## อุปกร์ที่ใช้ทดลอง
1.computer <br>
2.microcontroller ESP_01 <br>
3.หลอดไฟ LED <br>
4.USB ไว้เชื่อมต่อกับ Serial
## ศึกษาข้อมูลเพิ่มเติม
* https://github.com/choompol-boonmee/lab63b/tree/master/examples
## วิธีการทำการทดลอง
1.เชื่อมต่อ Microcontroller กับ computer <br>
2.เปิด commandprompt <br>
3.นำ Code การสร้าง wifi และ Web server ด้านล่างใส่ลง microcontroller <br>

```javascript
#include <ESP8266WiFi.h>

const char* ssid = "lab7lab7lab7";
const char* password = "00000000";

IPAddress local_ip(172, 20, 10, 14);
IPAddress gateway(172, 20, 10, 1);
IPAddress subnet(255, 255, 255, 244);

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
WiFi.softAP("lab7lab7lab7"); 
server.begin();
}

void loop(){
WiFiClient client = server.available(); 

if (client) { 
String currentLine = ""; 
while (client.connected()) { 
if (client.available()) { 
char c = client.read(); 
header += c;
if (c == '\n') { 
if (currentLine.length() == 0) {
client.println("HTTP/1.1 200 OK");
client.println("Content-type:text/html");
client.println("Connection: close");
client.println();

if (header.indexOf("GET /5/on") >= 0) {
output5State = "on";
digitalWrite(output5, HIGH);
} else if (header.indexOf("GET /5/off") >= 0) {
output5State = "off";
digitalWrite(output5, LOW);
} else if (header.indexOf("GET /4/on") >= 0) {
output4State = "on";
digitalWrite(output4, HIGH);
} else if (header.indexOf("GET /4/off") >= 0) {
output4State = "off";
digitalWrite(output4, LOW);
}

client.println("<!DOCTYPE html><html>");
client.println("<head><meta charset='utf-8' name=\"viewport\" content=\"width=device-width, initial-scale=1\">");
client.println("<link rel=\"icon\" href=\"data:,\">");
client.println("<style>html { font-family: Helvetica; display: inline-block; margin: 0px auto; text-align: center;}");
client.println(".button { background-color: #195B6A; border: none; color: white; padding: 16px 40px;");
client.println("text-decoration: none; font-size: 30px; margin: 2px; cursor: pointer;}");
client.println(".button2 {background-color: #77878A;}</style></head>");

client.println("<body><h1>เว็บเซิร์ฟเวอร์ ใช้งานได้เด้อ</h1>");

client.println("<p>GPIO 5 - State " + output5State + "</p>"); 
if (output5State=="off") {
client.println("<p><a href=\"/5/on\"><button class=\"button\">ON</button></a></p>");
} else {
client.println("<p><a href=\"/5/off\"><button class=\"button button2\">OFF</button></a></p>");
} 

client.println("<p>GPIO 4 - State " + output4State + "</p>");
if (output4State=="off") {
client.println("<p><a href=\"/4/on\"><button class=\"button\">ON</button></a></p>");
} else {
client.println("<p><a href=\"/4/off\"><button class=\"button button2\">OFF</button></a></p>");
}
client.println("</body></html>");

client.println();
break;
} else { 
currentLine = "";
}
} else if (c != '\r') { 
currentLine += c; 
}
}
}
header = "";
client.stop();
}
}
```
4.พิมพ์ pio run -t upload เพื่อนำโปรแกรมลง Microcontroller
* กดปุ่มสีดำ เพื่อทำให้เกิดการ load 
* กดปุ่มสีแดง เพื่อให้เกิดการ reset
5.พิมพ์ pio device monitor เพื่อให้โปรแกรมทดสอบการทำงาน
6.ใช้โทรศัพท์มือถือหรือคอมพิวเตอร์ค้นหา wifi ที่สร้างจากตัว microcontroller แล้วทำการเชื่อมต่อ
* ชื่อ wifi คือ lab7lab7lab7
* รหัส wifi คือ 00000000
7.เมื่อเชื่อมต่อ wifi สำเร็จให้เข้า Web
* ใส่ IP ของ ESP นั้นคือ 172.20.10.14
8.เมื่อเข้าไปแล้วให้ลองกดปุ่ม Yes-No เพื่อตรวจสอบว่าไฟLEDติดและสว่างหรือไม่
* ถ้า Yes สว่าง
* ถ้า No ดับ

## บันทึกผลการทดลอง
จากการทดลองทำให้สามารถนำ code จากเดิมมาประยุกต์ได้เยอะแยะมากมายเปลี่ยนรูปแบบจากเดิมไปมากหรือน้อยขึ้นอยู่กับความถนัดของแต่ละคนและอุปกรณ์ที่ใช้หรือที่มีอยู่ ในขั้นตอนตรวจสอบ IP สามารถทำได้โดยพิมพ์ ifconfig ก็ได้ ในการทดลองที่ 7 นี้เราได้ทำความรู้การสร้าง wifi ด้วยตัว microcontroller จากการทดลองที่
