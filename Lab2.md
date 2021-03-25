# การทดลองที่ 2 เรื่อง การเขียนโปรแกรมค้นหาไวไฟ
## วัตถุประสงค์
ใช้ microcontroller สามารถหา wifi รอบๆได้
## อุปกรณ์ที่ใช้
1.microcontroller (ESP01) <br>
2.อุปกรณ์ต่อ USB-Serial <br> 
3.เสาปล่อยสัญญาณไวไฟ <br>
4.computer
### ศึกษาข้อมูลเบื้องต้น
run example 2 https://youtu.be/yBjab0UNuB8 <br>
code 02_scan-wifi https://github.com/choompol-boonmee/lab63b/blob/master/examples/02_Scan-Wifi/platformio.ini
## วิธีทำ
1.เชื่อมต่อ microcontroller เข้ากับคอมพิวเตอร์ด้วยการต่อ USB ไปยัง Serial <br>
2.เปิด cmd ใช้คำสั่ง cd pattani <br> 
3.พิมพ์คำสั่ง cd 02_scan-wifi <br> 
4.พิมพ์คำสั่ง 1s ตามด้วยค่ำสั่ง vi src/main.cpp เพื่อเตรียมอัพโหลดโปรแกรมใน microcontroller <br>
<br>
![image](https://user-images.githubusercontent.com/80882373/112294512-7ee03180-8cc5-11eb-8413-8eb2730b2374.png) <br>
5.พิมพ์คำสั่ง pio run -t upload เพื่ออัพโหลดโปรแกรมเข้า microcontroller <br>
![image](https://media.discordapp.net/attachments/663373978848591875/824536281425510430/unknown.png?width=765&height=430) <br>
6.พิมพ์คำสั่ง pio device monitor เพื่อสแกนหา wifi <br>
<br>
![image](https://media.discordapp.net/attachments/663373978848591875/824227472353787924/112263855-8c37f480-8ca2-11eb-863b-71d68cf96fa7.png?width=682&height=430)
## การบันทึกผลการทดลอง
จากการใช้คำสั่ง pio device monitor จะเริ่มสแกนหา wifi เมื่อพบจะขึ้นชื่อของ wifi ที่ตรวจเจอ
## อภิปรายผลการทดลอง
จากการทดลองการเขียนโปรแกรมค้นหาไวไฟ จะเห็นว่าเมื่อเราอัพโหลดโปรแกรมลงในไมโครคอนโทรเลอร์
และใช้คำสั่ง pio device monitor เพื่อดูการทำงานของไมโครคอนโทรเลอร์และหน้าจอจะแสดงผลจำนวนและชื่อของwifiที่ตรวจพบ
## คำถาม
? ใช้คำสั่งใดหา wifi ที่อยู่รอบๆ <br>
Ans : pio device monitor
