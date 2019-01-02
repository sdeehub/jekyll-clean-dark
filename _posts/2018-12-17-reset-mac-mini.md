---
layout: post
title: "ลง macOS ใหม่แบบที่ทำ Factory Reset ยังไง?"
date: 2018-12-17 15:46:07 +0700
description: ถ้าหากเรามีความจำเป็นที่จะต้องลง macOS ใหม่เพื่อล้างทุกอย่างบนเครื่องหรือทำ Factory Reset จะต้องทำยังไง?
tags: Apple
comments: true
---
ขั้นแรกก่อนที่จะลงมือเราจะต้องทำการ Backup ข้อมูลที่จำเป็นเก็บเอาไว้ก่อน จะด้วย Time Machine หรือเก็บไว้ที่ iCloud หรือเก็บไว้บน External HD ก็แล้วแต่ **แต่ต้องทำการ Backup ข้อมูลที่ต้องใช้เก็บไว้ให้เรียบร้อยก่อนเป็นอย่างแรก**

ถัดมาเมื่อเราจะต้องทำการล้างเครื่อง ลง macOS ใหม่ ซึ่งเป็นการล้างทุกอย่างออกแล้วเริ่มใหม่ (ไม่ใช่ลงซ้ำหรือ reinstall) ซึ่งหลายคนอาจจะสงสัยว่าทำไมต้องทำ - คำตอบสำหรับคำถามนี้ก็เช่น ต้องการขายเครื่อง ให้เป็นเครื่องเปล่า หรือ ได้เครื่องเก่าของเค้า มาเป็นเครื่องใหม่ของเรา อยากเริ่มกันใหม่ ลืมอดีตของเธอไปให้หมด อะไรประมาณนี้

และเมื่อพอจะเข้าใจที่มาที่ไป และเมื่อพร้อมที่จะเริ่มใหม่ก็ไปกันเลย!

- เริ่มจาก Shutdown เสร็จแล้วตอนเปิดเครื่องขึ้นมาใหม่ให้กด `Command`{: .key}+`R`{: .key} ค้างไว้ เพื่อบูทเข้าไปที่ Recovery Mode เมื่อเข้าได้จะเจอกับ macOS Utilities

- เลือกที่ `Disk Utility` แล้วคลิก `Continue`

  ![Disk Utility](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_600/v1546423925/IMG_20190102_170612732.jpg)

- ด้านซ้ายใต้ส่วนของ `Internal` คลิกที่ `Macintosh HD` คือเลือกฮาร์ดดิสก์ในเครื่องของเรา แล้วคลิกที่ `Erase` - ในส่วนของช่อง `Format` ถ้าเป็น `APFS` อยู่แล้วก็ตามนั้น แต่ถ้าไม่ใช่ให้เลือก `Mac OS Extended (Journaled)` แล้วในขั้นตอนการติดตั้ง macOS จะทำการแปลง format ตรงนี้ให้เราเอง

  ![Erase Disk](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_600/v1546423914/IMG_20190102_170639974.jpg)

- คลิก `Erase` เพื่อทำการลบ เมื่อเครื่องทำงานเสร็จแล้วให้คลิก `Done`

- จากนั้นหน้าจอจะกลับมาที่ macOS Utilities อีกครั้ง ถึงตรงนี้ให้เลือก `Reinstall macOS`

  ![Reinstall macOS](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_600/v1546423900/IMG_20190102_170704268.jpg)

- แล้วจากนั้นก็เข้าสู่กระบวนการคลิก `Continue` ไปจนจบขั้นตอน

  ![macOS Mojave](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_600/v1546423887/IMG_20190102_170727363.jpg)
