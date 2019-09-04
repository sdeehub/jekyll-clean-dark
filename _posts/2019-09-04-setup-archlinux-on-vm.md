---
layout: post
title: "ติดตั้ง Arch Linux บน VM (ง่ายกว่าที่คิด)"
date: 2019-09-04 16:21:26 +0700
description: มาดูสรุปขั้นตอนและคำสั่งสำหรับการติดตั้ง Arch Linux บน VM กันครับ
tags:
- Arch Linux
- VirtualBox
comments: true
---
เริ่มต้นด้วยการไปโหลดไฟล์ image ISO ของ Arch Linux กันก่อน จากที่นี่ : [https://www.archlinux.org/download/](https://www.archlinux.org/download/) เลือกโหลด Magnet file, Torrent file หรือจะเป็นแบบ https download ก็ได้ (เลื่อนไปหา link ใกล้ๆ บ้านเราจากด้านล่างของ Page)

ระหว่างรอ download เพื่อไม่ให้เสียเวลามาสร้าง VM ขึ้นมาไว้กันก่อนเลยครับ ครั้งนี้เราจะใช้ Oracle VM VirtualBox สำหรับขั้นตอนก็คือ คลิก New จากนั้นก็ไหลไปตามนี้เลย :

![VM Screen-1](https://res.cloudinary.com/sdees-reallife/image/upload/v1567590491/archvm-screen-01.png)

- New > ตั้งชื่อ VM นี้ว่า ArchVM ประมาณนี้ > คลิก Next
- RAM 1024MB (1GB) > คลิก Next
- Create a virtual hard disk now > คลิก Create
- VDI (VirtualBox Disk Image) > คลิก Next
- Dynamically allocated > คลิก Next
- กำหนดพื้นที่ไว้ 20GB > คลิก Create

พอได้ VM มาเรียบร้อย คาดว่า ISO ก็น่าจะโหลดมาเรียบร้อยแล้ว เอาล่ะงั้นก็มาทำการ Start สิ่งที่เป็น VM ของเรากันเลย - เลือก ISO ไฟล์จากตรงนี้

![VM Screen-2](https://res.cloudinary.com/sdees-reallife/image/upload/v1567609950/archvm-screen-03.png)

เมื่อ Boot ขึ้นมาได้เรียบร้อย หลังจากนี้ก็จะเป็นขั้นตอนของการติดตั้ง Arch Linux แล้วล่ะ - *มาถึงตรงนี้บอกเผื่อไว้สำหรับใครที่อาจจะหลุด แล้วต้องกลับมาบอกให้ VM ทำการ Boot ใหม่ ดูหน้าจอนี้นะครับ*

![VM Screen-3](https://res.cloudinary.com/sdees-reallife/image/upload/v1567609966/archvm-screen-05.png)

*วิธีตั้งค่าให้ VM ไปเอา ISO ไฟล์มา Boot ก็คือ Settings > Storage > Empty > คลิกที่รูป CD กลมๆ แล้วไปเลือกหาไฟล์ ISO สำหรับเอามาใช้ในการ Boot*

เอาล่ะ! - เมื่อ Boot ขึ้นมาได้เรียบร้อย หลังจากนี้ก็จะเป็นขั้นตอนของการติดตั้ง Arch Linux แล้วล่ะ มาดูกันนะเราพยายามจะร้อยเรียงคำสั่งที่ต้องใช้ให้ทำตามได้เลยไปทีละขั้นตอนตามนี้ :

![VM Screen-4](https://res.cloudinary.com/sdees-reallife/image/upload/v1567609973/archvm-screen-06.png)

1. เริ่มที่ `root@archiso ~ #``
2. `fdisk /dev/sda`
3. `n` ทำ partition 1 > `p` Primary / ขนาด 8GB (สำหรับ root)
3. `n` ทำ partition 2 > `p` Primary / ขนาด 4GB (สำหรับ swap)
4. `n` ทำ partition 3 > `p` Primary / ขนาด 8GB (ที่เหลือ สำหรับ home)
5. `w` write partition ตามที่เราทำไว้ ลงไปที่ disk
6. `mkfs.ext4 /dev/sda1` > `mkfs.ext4 /dev/sda3`
6. `mkswap /dev/sda2` > `swapon /dev/sda2`
7. `mount /dev/sda1 /mnt`
7. `mkdir /mnt/home` > `mount /dev/sda3 /mnt/home`
8. `pacstrap /mnt base base-devel`
9. `genfstab -U /mnt >> /mnt/etc/fstab`
9. `arch-chroot /mnt`
10. `ln -sf /usr/share/zoneinfo/Asia/Bangkok /etc/localtime`
10. `hwclock --systohc --utc`
11. `locale-gen` > `echo LANG=en_GB.UTF-8 > /etc/locale.conf` > `export LANG=en_GB.UTF-8`
12. `echo ArchVM > /etc/hostname` ตั้งชื่อเครื่องของเรา ในตัวอย่างนี้คือ `ArchVM`
13. `nano /etc/hosts` >
```bash
127.0.0.1	localhost
::1		localhost
127.0.1.1	ArchVM.localdomain	ArchVM
```
14. `ctrl-x` > `Yes` > `/etc/hosts`
15. `pacman -S grub`
16. `grub-install /dev/sda`
16. `grub-mkconfig -o /boot/grub/grub.cfg`
17. `passwd`

ถึงตรงนี้เราควรจะได้ ArchVM ของเราที่มี root password ตามที่เราเพิ่งจะตั้งไปเรียบร้อยแล้วล่ะ - reboot VM แล้วภาวนา หรือยิ้มรอได้เลย :)
