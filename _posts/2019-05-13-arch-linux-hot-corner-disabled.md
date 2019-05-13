---
layout: post
title: "ปิดการใช้งาน Left Hot Corner บน Arch Linux"
date: 2019-05-13 17:30:42 +0700
description: วันนี้จะมาดูการปิดเจ้า Left Hot Corner (คือตรงมุมซ้ายบนของหน้าจอเวลาที่เราเลื่อนเมาส์เข้าไป) บน Arch Linux กันครับ
tags:
- Arch Linux
comments: true
---
การใช้งาน Left Hot Corner โดยปกติก็คือเวลาที่เราเคลื่อนเมาส์เข้าไปที่มุมซ้ายบนของหน้าจอ ก็จะเกิดเหตุการณ์แบบนี้

![Left Hot Corner](https://res.cloudinary.com/sdees-reallife/image/upload/v1557743817/Screenshot_from_2019-05-13_16-35-51.png)

คราวนี้เมื่อเราจะปิดการทำงานนี้ - มาเริ่มจากอ่านคำแนะนำตรงนี้ก่อนเลย: [Arch Linux - GNOME - Disable top left hot corner](https://wiki.archlinux.org/index.php/GNOME#Disable_top_left_hot_corner)

จากคำแนะนำเราสามารถติดตั้ง Extension ที่ชื่อว่า 'No Topleft Hot Corner' จากหน้า Browser ได้เลย ด้วยการคลิกไปที่ [https://extensions.gnome.org/](https://extensions.gnome.org/)

พอคลิกเข้าไปแล้ว และถ้าบน Browser เกิดมีข้อความเตือนแบบนี้ก็ไม่ต้องตกใจ

![Needed chrome-gnome-shell](https://res.cloudinary.com/sdees-reallife/image/upload/v1557745360/Screenshot_from_2019-05-13_17-53-18.png)

ให้ติดตั้ง `chrome-gnome-shell` ด้วยคำสั่ง `sudo pacman -S chrome-gnome-shell` แบบนี้ซะก่อน

```console
$ sudo pacman -S chrome-gnome-shell
resolving dependencies...
looking for conflicting packages...

Packages (1) chrome-gnome-shell-10.1-2

Total Installed Size:  0.03 MiB

:: Proceed with installation? [Y/n] y
(1/1) checking keys in keyring                     [###################] 100%
(1/1) checking package integrity                   [###################] 100%
(1/1) loading package files                        [###################] 100%
(1/1) checking for file conflicts                  [###################] 100%
(1/1) checking available disk space                [###################] 100%
:: Processing package changes...
(1/1) installing chrome-gnome-shell                [###################] 100%
:: Running post-transaction hooks...
(1/3) Updating icon theme caches...
(2/3) Arming ConditionNeedsUpdate...
(3/3) Updating the desktop file MIME type cache...
$
```

คราวนี้บน Browser ก็สามารถติดตั้ง Extension ที่ต้องการได้ล่ะ

![gnome-extension](https://res.cloudinary.com/sdees-reallife/image/upload/v1557745400/Screenshot_from_2019-05-13_17-46-03.png)

![enable extension](https://res.cloudinary.com/sdees-reallife/image/upload/v1557745446/Screenshot_from_2019-05-13_17-46-37.png)

ถ้าจะตรวจสอบว่ามีการใช้งาน gnome-extension อะไรอยู่บ้างในตอนนี้ก็สามารถใช้คำสั่งนี้ได้เลย `gsettings get org.gnome.shell enabled-extensions`

```console
$ gsettings get org.gnome.shell enabled-extensions
['hidetopbar@mathieu.bidon.ca', 'hide-top-panel@dimka665.gmail.com', 'nohotcorner@azuri.free.fr']
$
```

คราวนี้เมื่อติดตั้ง Extension ไปเรียบร้อยแล้ว สุดท้ายถ้าจะเปิด-ปิด Extension จากใน Tweaks ก็สามารถทำได้เช่นกัน: `Tweaks` ‣ `Extensions`

![Tweaks Extensions](https://res.cloudinary.com/sdees-reallife/image/upload/v1557745471/Screenshot_from_2019-05-13_17-47-12.png)
