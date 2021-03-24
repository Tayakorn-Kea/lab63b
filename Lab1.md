# การทดลองที่ 1 เรื่องการเขียนโปรแกรมเพื่อรันบนไมโครคอนโทรเลอร์
## วัตถุประสงค์
1.ศึกษาพื้นฐานของ microcontroller <br />
2.ศึกษาเกี่ยวกับการใช้คำสั่งทำงาน microcontroller <br />
3.ศึกษาการเชื่อมต่อเบื้องต้นของ microcontroller
## อุปกรณ์
1.microcontroller (ESP01) <br />
2.อุปกรณ์ต่อ USB-Serial <br />
3.computer
### ศึกษาข้อมูลเบื้องต้น
run example 1 https://youtu.be/NLIUsWLEpmg <br />
code 01_Serial-Monitor https://github.com/choompol-boonmee/lab63b/blob/master/examples/01_Serial-Monitor/src/main.cpp
## วิธีทำ
1.เชื่อมต่อ microcontroller เข้ากับคอมพิวเตอร์ด้วยการต่อ USB ไปยัง Seria <br />
2.เปิด cmd ใช้คำสั่ง cd pattani <br />
<br />
![alt text](https://media.discordapp.net/attachments/663373978848591875/824215655830126602/112263053-3b73cc00-8ca1-11eb-9208-d6c6f034ab40.png) <br />
3.พิมพ์คำสั่ง cd_Serial-Monitor ตามด้วย <br />
vi src/main.cpp   เพื่อการดูcodeโปรแกรมทดสอบ microcontroller <br />
<br />
![alt text](https://media.discordapp.net/attachments/663373978848591875/824218014760173578/unknown.png) <br />
4.พิมพ์คำสั่ง vi platformio.ini เพื่อให้ทราบข้อมูลเกี่ยวกับ microcontroller <br />
5.พิมพ์คำสั่ง pio run -t upload เพื่อทำการรัน microcontroller <br />
<br />
![alt text](https://media.discordapp.net/attachments/663373978848591875/824221674480074752/unknown.png?width=729&height=430) <br />
6.กดที่ปุ่มของ microcontroller เพื่อให้โปรแกรมรับคำสั่งใหม่เข้าไป <br /> 
<br />
![alt text](https://media.discordapp.net/attachments/663373978848591875/824218369196032010/112263157-6a8a3d80-8ca1-11eb-95f8-a52ef839065b.png?width=329&height=430) <br />
7.พิมพ์คำสั่ง pio device monitor เพื่อเช็คผลลัพธ์ <br />
<br />
![image](https://user-images.githubusercontent.com/80882373/112289782-30309880-8cc1-11eb-9df2-e2e8afb0e747.png) <br />
## บันทึกผลการทดลอง
จากการใช้คำสั่ง vi platformio.ini ทำให้รู้ได้ว่า <br>
1.เป็น platform ของ espressif8266 <br>
2.bord ชื่อ esp01_1m <br>
3.ใช้วิธีการเขียนโปรแกรม arduino
## อภิปรายผลการทดลอง
จากการใช้คำสั่ง vi src/main.cpp ทำให้เราทราบว่าโปรแกรม 01_Serial-Monitor มี 2 ส่วนดังนี้ <br />
1.ส่วน set up <br>
2.ส่วน loop ที่เพิ่มจะเพิ่มตัวแปร count และแสดงผลของตัวแปรโดยมีการหน่วงเวลา 1000 ms โดยการทดลองการเขียนโปรแกรมเพื่อรันบนไมโครคอนโทรเลอร์จะเห็นว่าเมื่อเราอัพโหลดโปรแกรม 01_Serial-Monitor ลงในตัวไมโครคอนโทรเลอร์ที่เรียบร้อยแล้ว และใช้คำสั่ง pio device monitor เพื่อดูการทำงานของไมโทรคอนโทรเลอร์ หน้าจอจะขึ้นว่ามีการเปลี่ยนแปรทุกๆ 1 วินาทีตามโปรแกรม
### คำถาม
? ใช้คำสั่งใดในการรัน microcontroller <br />
Ans : pio run -t upload
