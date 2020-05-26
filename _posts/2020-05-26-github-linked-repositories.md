---
layout: post
title: "การตั้งค่า Linked repositories ใน Github Project"
date: 2020-05-26 T22:34:45+07:00
description: ถ้าจะให้ดีใช้งาน Github Project แล้วก็ใช้ Linked repositories ซะด้วยเลย
tags:
- Github
comments: true
---
มาดูกันเลยว่าเราจะต้องคลิกอะไรตรงไหนบ้าง เพื่อที่จะจัดการ link ให้ [Github Project](https://help.github.com/en/github/managing-your-work-on-github/managing-project-boards) รู้จักกับ Repository ที่เรา Push code กันอยู่ทุกวัน

เริ่มที่ Repository ของเราก่อน - ไปที่ `Settings`

![repo. setting](https://res.cloudinary.com/sdees-reallife/image/upload/v1590508967/Screenshot_from_2020-05-26_22.48.20.png)

ไปตรง Features - คลิกเลือกที่ `Issues`

![select issues](https://res.cloudinary.com/sdees-reallife/image/upload/v1590508967/Screenshot_from_2020-05-26_22.49.02.png)

ที่ Repository ทำแค่นี้ก็เรียบร้อยแล้ว ถัดมาก็ไปที่ Project กัน

สำหรับ Project ของเรา - คลิกที่ `...`

![dot dot dot](https://res.cloudinary.com/sdees-reallife/image/upload/v1590508967/Screenshot_from_2020-05-26_22.51.00.png)

ด้านซ้ายมุม - คลิกที่ `Linked repositories`

![linked repo.](https://res.cloudinary.com/sdees-reallife/image/upload/v1590508967/Screenshot_from_2020-05-26_22.51.45.png)

ตรงนี้ก็ใส่ชื่อ Repository ของเราลงไป - *1 Proejct เราสามารถ linked ได้ 25 repo. นะ*

![cacti.cacti.cacti](https://res.cloudinary.com/sdees-reallife/image/upload/v1590508967/Screenshot_from_2020-05-26_23.01.13.png)

หลังจากนี้ก็เป็นอันเสร็จพิธี ถัดจากนี้ไปมีอะไรก็ดูแลจัดการกันไปด้วย Project นี่ล่ะ ส่วนการ์ดงานไหนที่มี issue เกี่ยวข้องกับ Repository ไหนก็อ้างกันให้ตรง

![note to issue](https://res.cloudinary.com/sdees-reallife/image/upload/v1590510408/Screenshot_from_2020-05-26_23.26.23.png)

พอเมื่อไหร่ที่ Push code ก็ใส่ comment ให้ close #issue_no นั้นไว้ด้วย ตัว [Manage automation](https://help.github.com/en/github/managing-your-work-on-github/about-automation-for-project-boards) ของ Project ก็จะย้ายการ์ดไปให้ตามที่ตั้งไว้ได้เองเลย
