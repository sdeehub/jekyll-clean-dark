---
layout: post
title: วิธีเปลี่ยน Font ที่ใช้บน Ubuntu
date: 2021-07-10 T15:04:31+07:00
description: วิธีเปลี่ยน Font บน Ubuntu ง่าย ๆ (หรือบน elementary OS ก็ใช้วิธีนี้ได้) ด้วย GNOME Tweaks
tags:
- elementary OS
- Ubuntu
comments: true
---
มาดูการเปลี่ยน Font บน Ubuntu หรือบน elementary OS ก็ใช้วิธีนี้ได้ ด้วย GNOME Tweaks

ขั้นแรกสำหรับ Ubuntu ก็คือติดตั้ง GNOME Tweaks ด้วยคำสั่ง

`sudo apt install gnome-tweaks`

ส่วน elementary OS จะมีการติดตั้ง Tweaks มาให้เรียบร้อยแล้ว อยู่ในส่วนของ `Applications` ‣ `System Settings`

![System Settings](https://res.cloudinary.com/sdees-reallife/image/upload/v1625908768/Screenshot_from_2021-07-10_15.12.12.png)

ทั้ง Ubuntu และ elementary OS พอมาที่ `Tweaks` แล้วก็เข้าไปที่ `Fonts`

![Fonts](https://res.cloudinary.com/sdees-reallife/image/upload/v1625908761/Screenshot_from_2021-07-10_15.12.52.png)

มาถึงหน้าจอตรงนี้ก็คือจัดการเปลี่ยน Font กันได้เลย - ด้านล่างมีให้ Reset ค่า ถ้าเปลี่ยนไป เปลี่ยนมาแล้วไม่ถูกใจอยากกลับไปเริ่มใหม่กับใครคนเดิม หรือจะ Reset ด้วยมือก็ได้ เปิด `Terminal` ขึ้นมาแล้วว่าไปตามนี้ได้เลย

```bash
gsettings reset org.gnome.desktop.interface font-name            
gsettings reset org.gnome.desktop.interface document-font-name
gsettings reset org.gnome.desktop.interface monospace-font-name
gsettings reset org.gnome.desktop.wm.preferences titlebar-font
gsettings reset org.gnome.nautilus.desktop font
gsettings reset org.gnome.desktop.interface text-scaling-factor
```
