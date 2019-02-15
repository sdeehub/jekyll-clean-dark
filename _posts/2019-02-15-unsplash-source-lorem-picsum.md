---
layout: post
title: "แนะนำผู้ช่วยงานด้านรูปภาพ Cloudinary และ Unsplash Source (2/2)"
date: 2019-02-15 17:30:43 +0700
description: วันนี้ถึงเวลาที่เราจะมาแนะนำ Unsplash Source และมีแถม Lorem Picsum ให้พวกเราได้รู้จักกันต่อจากตอนที่แล้วครับ
tags: Tool
comments: true
---
*ตอนที่ 2* - วันนี้เรามาดูการใช้งาน Unsplash Source กันดีกว่า - เริ่มจากที่นี่ [https://source.unsplash.com](https://source.unsplash.com) สิ่งที่เราสามารถจะใช้ได้ก็คือการเรียกรูปจาก Unsplash มาแสดง

- แบบแรกคือสุ่มเอารูปภาพมาแสดงในขนาดที่กำหนด - `https://source.unsplash.com/random/600x400` ในคำสั่งนี้คือแสดงด้วยขนาด 600x400

![Random Unsplash](https://source.unsplash.com/random/600x400)

- ถัดมาเป็นการสุ่มรูปภาพจาก User ที่เราต้องการ - `https://source.unsplash.com/user/mzmlatief/600x400` ในคำสั่งนี้คือเราเลือกเอาการสุ่มรูปภาพของ [Mizan M Latief](https://unsplash.com/@mzmlatief)

![Random from User](https://source.unsplash.com/user/mzmlatief/600x400)

- ต่อมาเป็นการเพิ่มให้สุ่มเอารูปภาพจากการ Like ของ User คนที่เราต้องการ - `https://source.unsplash.com/user/mzmlatief/likes/600x400`

![Random User Likes](https://source.unsplash.com/user/mzmlatief/likes/600x400)

- คราวนี้มาสุ่มรูปภาพจาก Collection กันบ้างครับ - `https://source.unsplash.com/collection/4285281/600x400` ในตัวอย่างนี้เราใช้ `Collection ID: 4285281`

![Random from Collection](https://source.unsplash.com/collection/4285281/600x400)

- เลือกแบบสุ่ม ตรงนี้คือทุกครั้งที่มีการเรียก URL ไปใหม่รูปภาพก็จะเปลี่ยนไป แต่ถ้าต้องการให้ใช้รูปภาพนั้นไป ทั้งวัน หรือ ทั้งสัปดาห์ ก็ง่ายๆ แค่เติม `/daily` หรือ `/weekly` ต่อท้ายเข้าไปแบบนี้

`https://source.unsplash.com/collection/4285281/600x400/daily`

![Random Daily](https://source.unsplash.com/collection/4285281/600x400/daily)

`https://source.unsplash.com/collection/4285281/600x400/weekly`

![Random Weekly](https://source.unsplash.com/collection/4285281/600x400/weekly)

เรียบร้อยกันไปแล้วครับสำหรับ Unsplash Source - แต่ถ้าหากเรายังต้องการอะไรที่มากไปกว่านี้จาก Unsplash ให้ดูจาก [Unsplash API](https://unsplash.com/developers) เพิ่มได้ครับ เพราะอย่างหลังนี่มีเอาไว้สำหรับงาน Dev. โดยเฉพาะครับ

*ของแถม:* ก่อนจบมาแถมท้ายกันด้วย Lorem Picsum สักนิดนะครับ - `https://picsum.photos/`

- เริ่มจากง่ายๆ เลย สุ่มรูปภาพมาด้วย - `https://picsum.photos/600/400?random` นี่คือให้แสดงรูปภาพที่ขนาด 600x400 นะครับ แต่ถ้าใส่ค่าเดียวก็จะเป็น Square ไป

![Picsum](https://picsum.photos/600/400)

![Picsum Square](https://picsum.photos/600)

- ถัดมาใส่ Grayscale คือเพิ่ม `/g/` เข้าไป - `https://picsum.photos/g/600/400?random`

![Picsum Grayscale](https://picsum.photos/g/600/400?random)

- หรือจะใส่เบลอก็เพิ่ม `?blur` ต่อท้ายเข้าไป - `https://picsum.photos/600/400?blur`

![Picsum Blur](https://picsum.photos/600/400?blur)
