---
layout: post
title: "Hyper-V + Ubuntu + xRDP"
date: 2020-04-04 T09:38:52+07:00
description: วันนี้มาลองใช้ Hyper-V ของ Windows ทำ VM (แทนการใช้ VirtualBox) แล้วลง Ubuntu - ทุกอย่างเรียบร้อยแต่ทำไมหน้าจอมาไม่เต็ม?
tags:
- Linux
- Microsoft
- Ubuntu
comments: true
---
เริ่มกันที่จะใช้งาน Hyper-V ต้องทำยังไง? : อ่านนี่ก่อนเลย [Install Hyper-V on Windows 10](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)

หรือให้สรุปสั้นๆ ง่ายๆ - คลิกไป `Start` (หรือเท่ากับการ Search นั่นเอง) - ใส่ไปว่า `Turn Windows features on or off` แล้วคลิกไปที่ Hyper-V เป็นอันเรียบร้อย

![Windows Features](https://res.cloudinary.com/sdees-reallife/image/upload/v1585882683/Windows-Features.png)

คือเครื่องพร้อม, Hyper-V พร้อมแต่ถ้าเรายังไม่พร้อม : อ่านนี่ต่อเลย [How to Install Ubuntu on Windows 10 using Hyper-V?](https://geekflare.com/ubuntu-on-windows/)

หรือให้สรุปสั้นๆ ง่ายๆ - ซึ่งก็ไม่มี แต่ว่าก็ไม่ยาก ลองดูนะ!

เพราะสิ่งที่พวกเราเจอนั่นก็คือ ได้ Hyper-V แล้ว - ลง Ubuntu แล้ว แต่จะทำยังไงให้เต็มจอ! หากันตั้งนาน หรือให้สรุปสั้นๆ ก็คือ : อ่านนี่เลยที่เดียวจบ [Sneak Peek: Taking a Spin with Enhanced Linux VMs](https://techcommunity.microsoft.com/t5/virtualization/sneak-peek-taking-a-spin-with-enhanced-linux-vms/ba-p/382415#)

หรือให้สรุปสั้นๆ ง่ายๆ ก็คือ - บน VM ลง git ก่อนนะแล้วก็ตามนี้ได้เลย

`$ git clone https://github.com/Microsoft/linux-vm-tools.git ~/linux-vm-tools`
`$ cd ~/linux-vm-tools/ubuntu/18.04/`
`$ sudo chmod +x install.sh`
`$ sudo ./install.sh`

รันเสร็จแล้วครั้งแรกตำราบอกให้รีบูท พอกลับเข้ามา Ubuntu แล้วก็รันอีกครั้ง (ตกลงรัน `$ sudo ./install.sh` 2 ครั้งนะ) - เสร็จแล้วตอนนี้ให้ Shut down ตัว VM ของเราไปก่อน

มาที่ Windows - คลิกไป `Start` (หรือเท่ากับการ Search นั่นเอง) - ใส่ไป `Power` เจอแล้ว `Windows PowerShell` ตรงนี้ให้รันเป็น Administrator ด้วยนะ

![Windows PowerShell](https://res.cloudinary.com/sdees-reallife/image/upload/v1585884305/Windows-PowerShell.png)

แล้วใส่คำสั่งนี้:

`Set-VM -VMName <your_vm_name>  -EnhancedSessionTransportType HvSocket`

*ตรง <your_vm_name> ก็คือชื่อ VM ของเรานั่นเอง*

คราวนี้พอบู๊ท VM กลับมาอีกครั้งก็จะมีหน้าจอ `Display configuration` : เลือกกันให้ตรงตามที่ควรจะเป็น แล้วตรง `Show Options` ก็คลิกนั่นล่ะ - จากนั้น รู้แล้วนะว่าคุณจะต้องคลิกตรงไหน ยังไงต่อ :)

ไม่ลองก็ไม่รู้ใช่มั๊ย - วันนี้เอาแค่นี้ล่ะ ทุกอย่างเป็น VM ไม่น่าจะมีอะไรเสียหายลองดูได้นะ ขอให้มีความสุขกับการใช้ Ubuntu และ Windows ไปพร้อมๆ กัน
