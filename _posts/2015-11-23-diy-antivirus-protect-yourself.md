---
layout: post
title: "วิธีการตรวจสอบว่าเครื่อง Windows ติดไวรัสหรือไม่ โดยใช้ DOS Command Line"
date: 2015-11-23 17:17:47 +0700
tags:
  - Antivirus
  - DOS
description: สแกนไวรัสไม่ได้จำเป็น ถ้าคุณรู้เรื่อง IT มากพอ?
comments: true
---
ด้วย Comand Line ของ DOS ต่อไปนี้จะช่วยให้เราสามารถตรวจสอบความเคลื่อนไหวการใช้งาน network ของเครื่องเราได้ว่ามีอะไรที่ไม่ปกติหรือไม่

### 1) List Startup Items

`wmic startup list full` ใช้คำสั่ง: wmic startup list full - ดูว่า Startup Item เมื่อเราเปิดเครื่องว่ามี Services หรือ Process อะไรที่ดูพิกล ๆ ชื่อไม่คุ้น แต่…เอ้ย…จริง ๆ คุ้นไม่คุ้นนี่ก็ต้องรู้มาระดับหนึ่งเหมือนกันนะเห้ย ขืนไปลบสุ่มสี่สุ่มห้า ได้ลง Windows ใหม่ อย่ามาโทษกันนะเอ่อ…

ปล. จริง ๆ สามารถ กด `Ctrl`{: .key}+`Alt`{: .key}+`Del`{: .key} ได้ เหมือนกันนะ แต่ง่าย ๆ เดี่ยวมันไม่เทย์ดิ

### 2) DNS Cache

`displaydns` ใช้คำสั่ง: displaydns - เช็คดูว่า มีเว็บไซต์ไหนที่เคยทำการ resolve บ้าง
การ resolve dns cache นั้นก็คือ การเข้าถึงเว็บ ซึ่งชื่อมันจะแตกต่างกัน แบบว่า นี่ชื่อเว็บไรหว่ะ กุไม่เคยเข้า แล้ว dns มัน req เข้าไปได้ไง กุไม่เคยเข้าจีจีนะ

เอาล่ะ…นั้นแหละ คือผิดปกติแล้ว…ล่ะ หรือ เมิงแอบเข้าเว็บโป๊แล้วไปเผลอคลิกมั่ว อันนี้ก็ไม่รู้น้าาา

![DNS Cache]({{ "/assets/images/authors/romeoow/2015-11-23/blog1.png" | relative_url }}){: .center-image }*รูปหน้าจอ: DNS Cache*
### 3) ตรวจสอบ Network

คราวนี้มาส่อง network บ้างว่ามัน ไปคุยกับใครบ้าง คุยกันทางไหน? คุยกันกี่เรื่อง? รายละเอียดเยอะไหม? และมันจะทำอะไร? นี่เหมือนเราเสือกนะ แต่เราเสือกในเครื่องของเรา แสดงว่าเราไม่ผิดนะ  เอ่อ…

`netstat -naob` ใช้คำสั่ง: netstat -naob
* -n   address, port ที่ใช้ในรูปแบบตัวเลข ‣ คุยกันทางไหน?
* -a   connection ทั้งหมด และ listening port ‣ คุยกันกี่เรื่อง?
* -o   process id ของแต่ละ connection ‣ รายละเอียดเยอะไหม?
* -b   คำสั่ง connection นั้น ๆ ‣ มันจะทำอะไรของมัน?

![Netstat]({{ "/assets/images/authors/romeoow/2015-11-23/blog2.png" | relative_url }}){: .center-image }*รูปหน้าจอ: คำสั่ง netstat -naob*
