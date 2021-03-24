# การทดลองที่ 3 เรื่อง การเขียนโปรแกรมเอ้าพุทสัญญาณดิจิทัล
## วัตถุประสงค์
1.ศึกษาการเขียนโปรแกรมลง microcontroller <br>
2.ศึกษาและนำ microcontroller ไปใช้ <br>
3.เพื่อศึกษาเกี่ยวกับการ run microcontroller
## อุปกรณ์ที่ใช้
1.computer <br>
2.microcontroller (ESP01) <br>
3.อุปกรณ์ต่อ USB-Serial <br>
4.อแดปเตอร์ที่ต่อสายพอร์ท 0 กับ 1 <br>
5.รีเรย์ <br>
6.ตัวโปรแกรมเอ้าพุตสัญญาณ <br>
7.ขั้วชาร์ต
### ศึกษาข้อมูลเบื้องต้น
run relay https://www.youtube.com/watch?v=6JnhaUILGuw <br>
รีเรย์ http://www.psptech.co.th/ <br>
03_Output-Port https://github.com/choompol-boonmee/lab63b/blob/master/examples/03_Output-Port/src/main.cpp <br>
## วิธีทำ
1.เชื่อมต่อ อแดปเตอร์ เข้ากับคอมพิวเตอร์ด้วยการต่อ USB ไปยัง Serial <br>
2.นำ microcontroller เชื่อมต่อกับพอร์ท <br>
3.เปิด cmd ใช้คำสั่ง cd pattani <br>
4.ใช้คำสั่ง cd 03_Output-Port ตามด้วยคำสั่ง 1s และคำสั่ง pwd <br>
5.ใช้คำสั่ง vi src/main.cpp จะขึ้นโค้ดดังนี้ <br>