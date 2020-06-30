---
layout: post
title: "เช็คค่า MD5, SHA-1 ด้วย FCIV"
date: 2020-05-11 T10:06:51+07:00
description: มาใช้งาน fciv กัน
tags:
- Tool
- Windows
comments: true
---
*fciv คืออะไร?*  
fciv เป็น utility ของ Windows เอาไว้ใช้เช็คค่า MD5, SHA-1 หรือที่เรียกว่า File Checksum Integrity

*fciv อยู่ที่ไหน?*  
เราสามารถดาวน์โหลด fciv ได้จากที่นี่ [Microsoft File Checksum Integrity Verifier](https://www.microsoft.com/en-us/download/details.aspx?id=11533)

*ติดตั้งยังไง?*  
ง่ายมาก คลิก-คลิก ที่ Windows-KB841290-x86-ENU.exe

![fciv-1](https://res.cloudinary.com/sdees-reallife/image/upload/v1589173815/fciv-1.png)

![fciv-2](https://res.cloudinary.com/sdees-reallife/image/upload/v1589173815/fciv-2.png)

กด Yes เพื่อตอบรับข้อตกลงการใช้

![fciv-3](https://res.cloudinary.com/sdees-reallife/image/upload/v1589173814/fciv-3.png)

เลือกโฟลเดอร์ที่จะติดตั้ง

*แล้วใช้ยังไง?*  
ง่ายสุดๆ - ติดตั้ง (หรือไฟล์ fciv.exe) อยู่ที่ไหนก็เรียกที่นั่น แล้วตามด้วยไฟล์ที่เราจะให้หา Checksum แล้วก็กด Enter

![fciv-4](https://res.cloudinary.com/sdees-reallife/image/upload/v1589173815/fciv-4.png)

ค่าปกติจะเป็น MD5 แต่ถ้าเราจะหา SHA-1 ก็ให้เราใส่ `-sha1` เพิ่มในคำสั่ง แค่นี้ก็เรียบร้อย
