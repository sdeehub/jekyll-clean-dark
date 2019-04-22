---
layout: post
title: "เมื่อต้องใช้งาน .NET Core บน Arch Linux"
date: 2019-04-22 14:34:32 +0700
description: มาดูการติดตั้งและใช้งาน .NET Core บน Arch Linux กันครับ
tags:
  - .NET Core
comments: true
---
เริ่มจากการติดตั้งก่อนเลย

`$ sudo pacman -S dotnet-sdk`

วิธีตรวจดูว่าการติดตั้งเรียบร้อย

`$ dotnet --version`

หรือลองด้วย console application - ย้ายไปใน folder ใหม่ก่อน

`$ dotnet new console`

แล้วใช้คำสั่ง

`$ dotnet run`

ก็จะได้ `Hello World!` ขึ้นมาทันที

พอเราติดตั้ง .NET Core SDK เรียบร้อยแล้ว ถัดมาก็ทำการติดตั้ง [Code หรือ Visual Studio Code](https://wiki.archlinux.org/index.php/Visual_Studio_Code) - แล้วแต่ว่าเราจะเลือกใช้ตัวที่เป็น Open-Source หรือของ Microsoft

`$sudo pacman -S code`

การเรียกใช้ก็คือเรียก `code` ได้เลย - แค่นี้เราก็พร้อมที่จะใช้ .NET Core บนเครื่อง Arch Linux ของเราแล้วล่ะ
