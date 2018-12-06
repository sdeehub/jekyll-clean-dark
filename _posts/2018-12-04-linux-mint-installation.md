---
layout: post
title: "ติดตั้ง Linux Mint คู่กับ Ubuntu"
date: 2018-12-04 15:17:15 +0700
description: มาดูการติดตั้ง Linux Mint คู่กับเครื่องที่มี Ubuntu อยู่แล้วกันครับ (ง่ายมากๆ)
tags:
  - Linux Mint
  - Ubuntu
comments: true
---
การติดตั้ง Linux Mint 19 Tara บนเครื่องที่มี Ubuntu อยู่แล้ว (คือทำให้เป็น Dual Boot) มีขั้นตอนใกล้เคียงกับติดตั้งแบบธรรมดาที่มี OS เดียวมากครับ ซึ่งวิธีการติดตั้งมีดังนี้คือ

- เริ่มจาก Download Linux Mint ISO file จาก [https://linuxmint.com/download.php](https://linuxmint.com/download.php) - ในตัวอย่างนี้เราจะเลือกเป็น Cinnamon 64-bit

   สำหรับความแตกต่างของแต่ละ Edition คือ Cinnamon, MATE, Xfce หรือ Architecture ว่าจะเป็น 32-bit หรือ 64-bit ให้อ่านรายละเอียดเพิ่มเติมจากที่นี่ [https://linuxmint-installation-guide.readthedocs.io/en/latest/choose.html](https://linuxmint-installation-guide.readthedocs.io/en/latest/choose.html)

   ![Download Linux Mint](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_600/v1543912927/Screenshot_from_2018-12-04_15-41-34.png)

- ทำ Live Boot คือ Bootable USB ของ Linux Mint จาก ISO ไฟล์ที่ Download มา โดยใน Ubuntu เราจะใช้ `Startup Disk Creator`

   ![Startup Disk Creator](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_600/v1544085569/Screenshot_from_2018-12-06_15-38-55.png)

- เมื่อได้ Live Boot มาแล้วก็รีบูทเข้า Linux Mint แล้วคลิกที่ `Install Linux Mint`

   ![Install Linux Mint](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_600/v1543895762/Screenshot_from_2018-12-04_10-53-35.png)

   ![Keyboard Layout](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_600/v1543895811/Screenshot_from_2018-12-04_10-56-35.png)

   ![Preparing to install](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_400/v1543895902/Screenshot_from_2018-12-04_10-58-01.png)

- หน้าจอสำคัญคือตอนเลือกการติดตั้ง หรือ `Installation type` ให้เลือกเป็น
   * Install Linux Mint 19 alongside Ubuntu 18.04.1 LTS

   ![Installation type](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_400/v1543895988/Screenshot_from_2018-12-04_10-59-30.png)

   ถัดมาจะเป็นหน้าจอให้เลือกขนาด Partition - ตามตัวอย่างคือแบ่งเนื้อที่กันคนละครึ่งระหว่าง Ubuntu และ Linux Mint และทั้ง 2 OS นี้มีส่วนของพื้นที่ home แยกกัน

   ![Install alongside](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_400/v1543896036/Screenshot_from_2018-12-04_11-00-10.png)

   จากนั้นก็คลิก `Continue` ตามขั้นตอนการติดตั้งไปเรื่อยๆ

   ![Write previous changes](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_400/v1543896094/Screenshot_from_2018-12-04_11-01-17.png)

   ![Write the changes to disks](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_400/v1543896450/Screenshot_from_2018-12-04_11-07-17.png)

   ![Where are you?](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_400/v1543896518/Screenshot_from_2018-12-04_11-08-28.png)

   ![Who are you?](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_400/v1543896588/Screenshot_from_2018-12-04_11-09-05.png)

- แล้วเกือบสุดท้ายก็จะมาถึงการ `Copying files...` เพื่อทำการติดตั้ง

   ![Welcome to Linux Mint](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_400/v1543896642/Screenshot_from_2018-12-04_11-10-32.png)

- เมื่อการติดตั้งเรียบร้อยต้องทำการรีบูท 1 ครั้ง นั่นคือ `Restart Now` พอคลิกแล้วตรงนี้จะมีหน้าจอบอกให้เราเอา USB Live Boot ออกก่อนที่จะกด `Enter`{: .key}

   ![Installation Complete](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_400/v1543897572/Screenshot_from_2018-12-04_11-25-31.png)

และเมื่อรีบูทกลับขึ้นมาคราวนี้ก็จะมีเมนูให้เลือกเลยว่าจะบูทเข้า Linux Mint หรือ Ubuntu ก็ได้ สำหรับในส่วนของ Partition เราสามารถตรวจสอบด้วยคำสั่ง `sudo fdisk -l` ดูอีกที และจากในตัวอย่างของเราก็จะมี /dev/sdb2 และ /dev/sdb3 เป็น Linux filesystem อยู่ 2 ส่วนคู่กัน

```
Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 6B07C38F-2D73-4467-A13A-2FFC7ADA4511

Device         Start       End   Sectors   Size Type
/dev/sdb1       2048   1050623   1048576   512M EFI System
/dev/sdb2    1050624 499798270 498747647 237.8G Linux filesystem
/dev/sdb3  499800064 976771071 476971008 227.4G Linux filesystem
```

คราวนี้ไม่ว่าจะเพราะอะไรที่เราจะต้องลง OS ไปคู่กันนะครับ แต่ก็คือให้รู้ว่าเราสามารถทำได้สบายๆ แบบที่ว่ามานี้

สำหรับวันนี้จบล่ะครับ
