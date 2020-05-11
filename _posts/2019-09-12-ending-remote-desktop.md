---
layout: post
title: "ปิด Remote Desktop แบบไหน? - Sign Out หรือใช้ Disconnect"
date: 2019-09-12 22:22:10 +0700
description: เวลาที่เราจะจบการใช้งาน Remote Desktop เราจะเลือกใช้แบบไหน แล้วผลที่ได้จะเป็นยังไงบ้างเหรอครับ?
tags:
- Windows
comments: true
---
![Remote Desktop](https://res.cloudinary.com/sdees-reallife/image/upload/v1568281371/remote-desktop.png)

Remote Desktop หรือที่เรียกว่า RDP (Remote Desktop Protocol) หรือ RDS (Remote Desktop Services) เวลาเข้าใช้งานก็แค่ Login ไปที่เครื่องที่จะ Remote ให้ถูกเครื่อง - ส่วนเวลาจะจบการใช้งานล่ะ?

มีด้วยกัน 2 แบบนะ นั่นคือ:
- Disconnect - อันนี้จะจบการทำ Remote แต่ว่าเรื่องของ Session จะยังค้างอยู่ งานอะไรที่สั่งค้างไว้ที่ Server หรืออย่างดาวน์โหลดอะไรยังไม่เสร็จ แบบนี้จะยังทำต่อไป แล้วพอเรา RDP กลับเข้ามาใหม่ทุกอย่างก็จะต่อเนื่องจากตอนที่เราจากไปทันที
- Sign Out - อันนี้จะเป็นการจบ Remote แบบจบคือจบ Session จะถูกตัดจบ ไม่มีอะไรค้างคาที่เกิดจากการใช้งานของเรา แล้วพอ Login กลับเข้ามาใหม่ก็เหมือนมาเริ่มกันใหม่แบบคลีนๆ เกลี้ยงๆ แบบนั้นนั่นเอง

รู้กันแบบนี้แล้วก็เลือกใช้ให้ตรงกับที่พวกเราจะต้องการล่ะกันนะครับ
