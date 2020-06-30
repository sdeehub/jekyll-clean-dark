---
layout: post
title: "sc - อมตะ command ที่พวกเราใช้กันบน Windows"
date: 2020-06-30 T11:37:45+07:00
description: sc เป็นคำสั่งที่เราใช้กันบ่อย ๆ เอาไว้เพื่อจัดการกับ service บน Windows
tags:
- DOS
- Windows
comments: true
---
Syntax:  
`sc [\\server] [command] [service_name] [options]`

[SC หรือ Service Control](https://ss64.com/nt/sc.html) - และนี่คือ link เดียวที่ครบทุกอย่างเกี่ยวกับ sc ถ้าคุณคลิกไปอ่าน link ที่เราให้ไว้แล้วก็คงจะรู้แล้วว่า sc มีไว้ใช้ทำอะไร และ ใช้ยังไง แต่ถ้าคุณยังอ่านต่อมาถึงตรงนี้ เริ่มแรกคุณต้องรู้ก่อนว่าจะหา service_name มาได้จากที่ไหน?

service_name - มาจากการเปิดตัว Services บน Windows แล้วคลิกขวาที่ service เลือก Properties

![service-1](https://res.cloudinary.com/sdees-reallife/image/upload/v1593495792/service_name-1.png)

![service-2](https://res.cloudinary.com/sdees-reallife/image/upload/v1593495791/service_name-2.png)

และต่อไปนี้คือ sc ที่พวกเราใช้กันอยู่บ่อย ๆ และน่าจะเป็นประโยชน์สำหรับทุก ๆ คน

*สมมุติเอาว่าเราจะสั่งไปที่เครื่อง 192.168.0.35 ใน network ของเรานะ*
list ทุก service ที่ active บนเครื่อง 192.168.0.35:  
`sc \\192.168.0.35 query state=`

list ทุก service ที่ inactive บนเครื่อง 192.168.0.35:  
`sc \\192.168.0.35 query state= inactive`

list ทุก service บนเครื่อง 192.168.0.35:  
`sc \\192.168.0.35 query state= all`

*สมมุติเอาว่าเราจะจัดการ service: DHCP Client นะ*
start service ที่ชื่อ Dhcp บนเครื่อง 192.168.0.35:  
`sc \\192.168.0.35 start "Dhcp"`

stop service ที่ชื่อ Dhcp บนเครื่อง 192.168.0.35:  
`sc \\192.168.0.35 stop "Dhcp"`

เรียกดูสถานะของ service ที่ชื่อ Dhcp บนเครื่อง 192.168.0.35:  
`sc \\192.168.0.35 query "Dhcp"`

เรียกดู config ของ service ที่ชื่อ Dhcp บนเครื่อง 192.168.0.35:  
`sc \\192.168.0.35 qc "Dhcp"`

ตั้งค่าให้ service ที่ชื่อ Dhcp บนเครื่อง 192.168.0.35 start แบบ AUTO:  
`sc \\192.168.0.35 config "Dhcp" start= auto`

ตั้งค่าให้ service ที่ชื่อ Dhcp บนเครื่อง 192.168.0.35 start แบบ MANUAL:  
`sc \\192.168.0.35 config "Dhcp" start=`

สุดท้ายนี่เวลาใช้ต้องเอา `DOMAIN\User` กับ `password` มาใส่เอาไว้เปลี่ยน logon account ของ service:   
`sc \\192.168.0.35 config "Dhcp" obj= "DOMAIN\User" password= "password"`
