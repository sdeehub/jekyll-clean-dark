---
layout: post
title: certutil -hashfile c:\Temp\myfile.exe SHA512
date: 2020-07-25 T14:36:17+07:00
description: หาค่า hashfile ยังไง? เวลาใช้ Windows 10
tags:
- DOS
- Windows
comments: true
---
Syntax:  
`certutil -hashfile c:\Temp\myfile.exe SHA512`

เหมือน Q&A ยังไงยังงั้น ถามมา-ตอบไป แล้ว post นี้จะเขียนอะไรเพิ่มเติม? ส่งงานแบบนี้ลูกพี่เล่นงานผมแน่ ๆ แต่คำสั่งนี้ใช้ได้จริง ๆ นะครับ

ถ้าจะดูเป็น SHA256 ก็ใช้:

`certutil -hashfile c:\Temp\myfile.exe SHA512`

หรือถ้าจะดูค่า hash อื่น ๆ ผมแนะนำให้ใช้:

`certutil -hashfile -?`

![certutil hashfile](https://res.cloudinary.com/sdees-reallife/image/upload/v1595664728/certutil-hashfile.png)

ง่าย ๆ แค่นี้เองครับ แต่การหาค่า hash file บน Windows ยังมีวิธี (คำสั่ง) อื่นด้วยนะครับเช่น
- ใช้ fciv ก็ได้ - ตามที่พวกเราเคยเขียนไปแล้วใน post: [เช็คค่า MD5, SHA-1 ด้วย FCIV](https://sdeehub.github.io/cpe/2020/05/checksum-with-fciv)
- ใช้ PowerShell:

`PS C:\>Get-FileHash -Path c:\Temp\myfile.exe -Algorithm SHA512`

หรือถ้าจะหาพวก 3rd Party Tools มาใช้ก็ได้นะครับ แต่วันนี้ผมมาในรูปแบบของ Q&A จริง ๆ แถมยังไม่ต้องอ่านมาถึงตรงนี้ก็ได้เพราะดูชื่อ post ก็นึกออก เอาไปใช้งานได้แล้วนะครับ :)
