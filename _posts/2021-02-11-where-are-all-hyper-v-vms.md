---
layout: post
title: ช่วยด้วย! เปิด Hyper-V มาทำไม VM มันหาย?
date: 2021-02-11 11:06:20
description: วันนี้วันดีตรุษจีนรับปีวัวทั้งที เรียก Hyper-V ขึ้นมา กะจะเปิดเข้า VM ... แต่ว่า -ว่างเปล่า!-
tags:
- Hyper-V
- Windows
comments: true
---
ปกติบน Windows เราก็ใช้ VM ผ่านตัว Hyper-V Manager ([ถ้าต้องการรู้จักกับการใช้งาน Hyper-V - อ่าน post นี้นะ](https://sdeehub.github.io/cpe/2020/04/hyper-v-ubuntu-xrdp)) แต่คราวนี้พอเปิด Hyper-V Manager ขึ้นมากลับว่างเปล่า VM ที่ทำไว้หายเกลี้ยง

ถ้าเป็นแบบนี้ วิธีแก้ที่เราเจอก็คือ link นี้ ของ [shauncassells](https://shauncassells.wordpress.com/2018/05/24/fix-hyper-v-encountered-an-error-trying-to-access-an-object-on-computer-localhost-because-the-object-was-not-found-the-object-might-have-been-deleted-verify-that-the-virtual-machine-managemen/)

นั่นก็คือเปิด `Windows PowerShell (Admin)` (Shortcut key: `Winkey`{: .key}+`X`{: .key}+`A`{: .key})

แล้วใช้คำสั่งนี้:

`MOFCOMP %SYSTEMROOT%\System32\WindowsVirtualization.V2.mof`

![mofcomp](https://res.cloudinary.com/sdees-reallife/image/upload/v1613015493/Screenshot_2021-02-11_100555.png)

ปิด Hyper-V Manager แล้วเปิดขึ้นมาใหม่ ... เย้! เรียบร้อย ซินเจิ้งหรูอี้ ซินเหนียนฟาไฉ - ขอให้ปีใหม่นี้สมหวังทุกประการ ร่ำรวยมั่งคั่ง สุขภาพแข็งแรงทั่วกันทุก ๆ คน
