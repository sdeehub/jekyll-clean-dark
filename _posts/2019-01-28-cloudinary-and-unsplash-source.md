---
layout: post
title: "แนะนำผู้ช่วยงานด้านรูปภาพ Cloudinary และ Unsplash Source (1/2)"
date: 2019-01-28 14:38:38 +0700
description: วันนี้เราจะมาแนะนำ Cloudinary และ Unsplash Source ให้พวกเราได้รู้จักกันไว้นะครับ
tags: Tool
comments: true
---
*ตอนที่ 1* - เริ่มจาก Cloudinary หรือ [https://cloudinary.com](https://cloudinary.com) คือ บริการให้จัดเก็บรูปภาพและวีดีโอพร้อมด้วยตัวจัดการที่ให้บริการในแบบ Cloud (SaaS) สำหรับข้อมูลอ้างอิงเพิ่มเติมจากใน wiki ดูได้ที่นี่: [https://en.wikipedia.org/wiki/Cloudinary](https://en.wikipedia.org/wiki/Cloudinary)

สำหรับการใช้งานสามารถ Sign up ได้ฟรี ซึ่งสำหรับ Free Plan จะกำหนดไว้ให้แค่ 1 Account ต่อ 1 User และสามารถใช้งานได้ตามข้อกำหนดนี้:

| 20,000 + 6,750 Extra | จำนวนครั้งที่รับ-ส่งได้ในแต่ละเดือน
| 300,000 + 250,000 Extra | จำนวนรูปภาพและวีดีโอที่เก็บได้ทั้งหมด
| 10 GB + 2.5 GB Extra | เนื้อที่จัดเก็บทั้งหมด
| 20 GB + 5 GB Extra | Bandwidth ที่ให้ได้สำหรับการดูในแต่ละเดือน
| 10 MB | ขนาดสูงสุดของ 1 ไฟล์รูป
| 100 MB | ขนาดสูงสุดของ 1 ไฟล์วีดีโอ

การใช้งานที่พวกเราใช้กันมากสุดก็คือเก็บรูปภาพ แล้วเรียกมาแสดงในเว็บ โดย:
- ปรับขนาดรูปที่แสดงใหม่
- ใส่ Filter
- เปลี่ยนขนาดไฟล์ให้เล็กลง
- เปลี่ยนไฟล์ Format - หลักๆ ก็จะใช้งานอยู่ประมาณนี้ครับ

ดูตัวอย่าง: จากรูปจริงที่มีขนาด 3888 x 2592  - แต่เราจะเอามาแสดงที่ขนาดกว้าง 600 จากการอ้าง URL ข้างล่างนี้ ดูตรง `c_scale,w_600` คือกำหนดขนาดเป็นกว้าง (width) 600 และจัดการรักษาสัดส่วนให้โดยอัตโนมัติ

`https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_600/v1548237664/dayne-topkin-67327-unsplash.jpg`

![Sample 600](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_600/v1548237664/dayne-topkin-67327-unsplash.jpg)
*Photo by [Dayne Topkin](https://unsplash.com/@dtopkin1) on [Unsplash](https://unsplash.com/)*
{:.figure}

สำหรับอันนี้ `c_scale,w_300` ก็จะปรับขนาดเป็นกว้าง 300 และจัดการรักษาสัดส่วนให้โดยอัตโนมัติ

`https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_300/v1548237664/dayne-topkin-67327-unsplash.jpg`

![Sample 300](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_300/v1548237664/dayne-topkin-67327-unsplash.jpg)

ส่วนอันนี้เป็น `c_fill,g_auto,h_150,w_150` แสดงขนาด 150 x 150 พร้อมกับหาเนื้อหลักในภาพอัตโนมัติ

`https://res.cloudinary.com/sdees-reallife/image/upload/c_fill,g_auto,h_150,w_150/v1548237664/dayne-topkin-67327-unsplash.jpg`

![Sample 150](https://res.cloudinary.com/sdees-reallife/image/upload/c_fill,g_auto,h_150,w_150/v1548237664/dayne-topkin-67327-unsplash.jpg)

ถัดมาอันนี้ `c_fill,g_auto,h_150,w_150,r_max` ทุกอย่าง 150 x 150 เพิ่มเติมคือตัดมุมรัศมีเป็นวงกลมด้วย `r_max`

`https://res.cloudinary.com/sdees-reallife/image/upload/c_fill,g_auto,h_150,w_150,r_max/v1548237664/dayne-topkin-67327-unsplash.jpg`

![Sample r_max](https://res.cloudinary.com/sdees-reallife/image/upload/c_fill,g_auto,h_150,w_150,r_max/v1548237664/dayne-topkin-67327-unsplash.jpg)

เอาตัวอย่างพอให้เห็นภาพกันสักเท่านี้ก่อนนะครับ สำหรับประโยชน์ที่ได้และต้องขอบคุณ Cloudinary ไว้เป็นอย่างมากก็คือการที่:
- เราได้พื้นที่เก็บรูป
- เรียกใช้รูปได้บน Cloud
- จัดการรูปได้เลยในตอนเรียกใช้
- และถ้าใช้แบบที่ไม่ใช่ Free Plan ก็สามารถมี User หลายๆ คนและกำหนดผู้ดูแลได้ด้วย - [ตามเนื้อหานี้ครับ](https://support.cloudinary.com/hc/en-us/articles/202521652-Can-I-have-multiple-users-roles-for-my-account-)

ถ้าสนใจจะดูตัวอย่างทั้งหมดของ Cloudinary ก็คลิกที่นี่เลยครับ: [Cloudinary Demo](https://demo.cloudinary.com/) - ครั้งหน้าเรามาต่อกันที่ Unsplash Source นะครับ
