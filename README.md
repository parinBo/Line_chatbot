# Line_chatbot With DialogFlow

## Line

* create line account
```
https://developers.line.biz/en/
```
* go to products > Messaging API (จะอยู่ด้านซ้าย) > Start now
 <img src="https://github.com/parinBo/Line_chatbot/blob/main/chatbot1.png" width="350" alt="accessibility text">
 
* จากนั้นตั้งชื่อ project,channel icon,channe name(ชื่อApp),channel description, Category, Subcategory, Email address
* เมื่อเสร็จแล้ว ที่ Basic setting คัดลอก channel Id และ เลื่อนลงมาด้าล่าง คัดลอก Channel secret  จากนั้นไปที่ Messaging API เลื่อนลงมาด้านล่างสุด คัดลอก Channel access token

## DialogFlow
* create agent 
แนะนำรายละเอียดคร่าวๆ
**intent** เป็นการกำหนดส่วนพูดคุยของchat bot โดยตอนแรกจะมี 
* Default Fallback Intent
* Default Welcome Intent <br>
ซึ่ง2 อันนี้ เป็นค่าเริ่มต้นของคำพูดทักทายกับคำพูดที่ chatbot ไม่เข้าใจ
สามารถสร้างได้เองได้โดยกดที่ create intent ที่ด้านบน เมื่อกดแล้ว ตั้งชื่อ intent โดยส่วนหลักๆ จะมี <br>
-> Contexts จะมี input และ output ซึ่งสามารถเพิ่มอย่างใดอย่างหนึ่ง ทั้งสองอย่าง หรือไม่ก็ได้ โดยcontext นี้คือ intent<br>
-> Training phrases คือคำที่ user จะพิมพ์เข้ามา
-> Respose คือ จะตอบกลับว่าอะไร
 <img src="https://github.com/parinBo/Line_chatbot/blob/main/chatbot3.png" width="350" alt="accessibility text">
 
**Fulfillment** => ส่วนของการเพิ่มเต็มให้บอทเราสามารถส่งค่าไปประมวลผลหรือดึงค่าบางอย่างมาแสดงจาก backend ได้ สามารถใส่ได้ 2 แบบ คือ ใส่ webhook ลงไป กับ พิมพ์ลงไปใน Inline Editor ซึ่ง มันเชื่อมกันกับ Cloud Function for Firebase<br>
**Integrations** => เป็นส่วนที่จะconnectเข้ากับ app platform ต่างๆ<br>
**Training** => เป็นส่วนที่บอกว่าเจอคำกี่ครั้ง <br>
**history** => ประวัติ

## connect line
* ไปที่ Integrations เลือกหาไลน์ เพิ่ม channel Id,Secret,Access token กด save
* จากนั้น นำ webhook dialogflow ไปใส่ที่ line develop
---
## ทำinput กับ line chatbot
* สร้างintent หลักก่อน จากนั้น ทำการสร้าง follow up intent โดยนำเมาส์ไปชี้ที่ intent หลัก และเลือก Add follow-up intent<br>
::ข้ามมาที่ Action and parameters ก่อน::<br>
<mark>ข้ามมาที่ Action and parameters ก่อน</mark><br>
**REQUIRED** = เลือกเมื่อจต้องการ parameter
**PARAMETER NAME** = ตั้งชื่อ parameter
**ENTITY** = typr parameter
**VALUE** = variable start with $ (ex. $name)
**PROMPTS** = มันจะแสดงผลกรณีที่ Dialogflow ไม่สามารถเก็บค่านั้นมาได้ ในที่นี้ก็คือค่าน้ำหนัก โดยเราสามารถมีได้หลายประโยคผ่านการเว้นบรรทัด<br>
เมื่อเสร็จสิ้นแล้วกลับขึ้นไปด้านบน ไปที่ Training phrases ให้ทำการทดลองใส่ข้อความลงไป โดยเมื่อใส่ไปแล้วทำการจับคู่กับ parameter ที่สร้างไว้ให้ถูกต้อง
 <img src="https://github.com/parinBo/Line_chatbot/blob/main/chatbot5.png" width="350" alt="accessibility text">



