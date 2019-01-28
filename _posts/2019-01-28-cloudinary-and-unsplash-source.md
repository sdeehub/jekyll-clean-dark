---
layout: post
title: "แนะนำผู้ช่วยงานด้านรูปภาพ Cloudinary และ Unsplash Source (1/2)"
date: 2019-01-28 14:38:38 +0700
description: วันนี้เราจะมาแนะนำ Cloudinary และ Unsplash Source ให้พวกเราได้รู้จักกันไว้นะครับ
tags: Tool
comments: true
---
ตอนที่ 1 - เริ่มจาก Cloudinary หรือ [https://cloudinary.com](https://cloudinary.com) คือ บริการให้จัดเก็บรูปภาพและวีดีโอพร้อมด้วยตัวจัดการที่ให้บริการในแบบ Cloud (SaaS) สำหรับข้อมูลอ้างอิงเพิ่มเติมจากใน wiki ดูได้ที่นี่: [https://en.wikipedia.org/wiki/Cloudinary](https://en.wikipedia.org/wiki/Cloudinary)

สำหรับการใช้งานสามารถ Sign up ได้ฟรี ซึ่งสำหรับ Free Plan จะกำหนดไว้ให้แค่ 1 Account ต่อ 1 User และสามารถใช้งานได้ตามข้อกำหนดนี้:

| 20,000 + 6,750 Extra | จำนวนครั้งที่รับ-ส่งได้ในแต่ละเดือน
| 300,000 + 250,000 Extra | จำนวนรูปภาพและวีดีโอที่เก็บได้ทั้งหมด
| 10 GB + 2.5 GB Extra | เนื้อที่จัดเก็บทั้งหมด
| 20 GB + 5 GB Extra | Bandwidth ที่ให้ได้สำหรับการดูในแต่ละเดือน
| 10 MB | ขนาดสูงสุดของไฟล์รูป
| 100 MB | ขนาดสูงสุดของไฟล์วีดีโอ

การใช้งานที่พวกเราใช้กันมากสุดก็คือเก็บรูปภาพ แล้วเรียกมาแสดงในเว็บ โดย:
- ปรับขนาดใหม่
- ใส่ Filter
- เปลี่ยนขนาดไฟล์
- เปลี่ยน Format หลักๆ ก็จะใช้งานประมาณนี้ครับ

ดูตัวอย่าง จากรูปจริงขนาด 2048 x 1536  - จากการอ้าง URL ข้างล่างนี้ให้ดูตรง `c_scale,w_800` คือกำหนดขนาดเป็นกว้าง 800 และจัดการรักษาสัดส่วนให้โดยอัตโนมัติ

`https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_800/v1548237664/dayne-topkin-67327-unsplash.jpg`

![Sample 800](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_800/v1548237664/dayne-topkin-67327-unsplash.jpg)

สำหรับอันนี้ `c_scale,w_400` ก็จะปรับขนาดเป็นกว้าง 400 และจัดการรักษาสัดส่วนให้โดยอัตโนมัติ

`https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_400/v1548237664/dayne-topkin-67327-unsplash.jpg`

![Sample 400](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_400/v1548237664/dayne-topkin-67327-unsplash.jpg)

ส่วนอันนี้เป็น `c_fill,g_auto,h_200,w_200` แสดงขนาด 200 x 200 พร้อมกับหาเนื้อหลักในภาพอัตโนมัติ

`https://res.cloudinary.com/sdees-reallife/image/upload/c_fill,g_auto,h_200,w_200/v1548237664/dayne-topkin-67327-unsplash.jpg`

![Sample 200](https://res.cloudinary.com/sdees-reallife/image/upload/c_fill,g_auto,h_200,w_200/v1548237664/dayne-topkin-67327-unsplash.jpg)

ถัดมาอันนี้ `c_fill,g_auto,h_200,w_200,r_max` ทุกอย่าง 200 x 200 เพิ่มเติมคือตัดมุมรัศมีเป็นวงกลมด้วย `r_max`

สรุปแค่การใช้งานตามตัวอย่างนี้ประโยชน์ที่พวกเราได้มากๆ จาก Cloudinary ก็คือ:
- เราได้พื้นที่เก็บรูป
- เรียกใช้ในแบบ Cloud
- จัดการรูปได้เลยในตอนเรียกใช้

ซึ่งนอกจากปรับขนาดเวลาจะแสดงรูปตามที่พวกเราใช้งานกันบ่อยๆ ที่บอกแล้ว ก็ยังปรับขนาดไฟล์ได้, แปลง Fomat, ใส่ Filter พวกนี้สามารถทำได้หมด และถ้ามีเวลาอีกนิดก็คลิกไปดูตัวอย่างทั้งหมดได้เลยที่นี่: [Cloudinary Demo](https://demo.cloudinary.com/) - ครั้งหน้าเรามาต่อกันที่ Unsplash Source นะครับ
