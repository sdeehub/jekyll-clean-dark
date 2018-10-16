---
layout: post
title: "อัพ iOS 11.3 แล้ว Wi-Fi เข้าไม่ได้!"
date: 2018-01-28 12:44:00 +0700
description: เรื่องมีอยู่ว่าที่ผ่านมาทุกครั้งหลังการอัพ iOS ทุกอย่างจะผ่านไปด้วยความเรียบร้อย แต่ล่าสุดหลังจากที่มีการอัพ iPad เป็น iOS 11.3 เกิดการใช้งานในส่วนของ Wi-Fi ไม่ได้ คือ ใส่ password ยังไงเครื่องก็ยังไม่ยอมเข้าให้ (ทั้งๆ ที่ใส่ password ไม่ผิดแน่ๆ) แล้วเราจะแก้ไขอะไรได้บ้าง?
tags: Mac
comments: true
---
เอาตอนจบ กับ [คำเตือน](#caution) มาบอกไว้ก่อนในตอนนี้ว่า สุดท้ายแล้วใช้วิธี Factory Reset ทุกอย่างใหม่ คือ ไปที่ `Settings` ‣ `General` ‣ `Reset` ‣ `Erase All Content and Settings` และแล้วทุกอย่างก็ `หายเกลี้ยงไป` รวมถึงอาการใช้งาน Wi-Fi ไม่ได้ก็หายกลับมาใช้งานได้เป็นปกติด้วย แต่ก่อนที่จะไปถึงขั้นตอนสุดท้ายแบบที่เราต้องยอมให้ทุกอย่างหายไปเพื่อที่เราจะได้เธอกลับมาใหม่ มาดูกันว่ามีอะไรที่ช่วยเราได้บ้างในระหว่างทาง

ทวนสถานการณ์ที่เกิดขึ้นอีกครั้งนะครับ คือ หลังจากอัพ iOS บน iPad ซึ่งปกติก็ทำอย่างต่อเนื่องมาทุกๆ ครั้งที่มีอัพเดทออกมาใหม่ แต่ล่าสุดครั้งสุดท้ายเมื่อคืนวานที่เป็นการอัพ iOS ไปที่ 11.3 หลังจากเครื่องบูทกลับมาปรากฎว่าเข้า Wi-Fi ไม่ได้ ใส่ password ยังไงก็ไม่ผ่าน เราลองมาดูการแก้ไขไปตามขั้นตอนนี้นะครับ ทำไล่ไปทีละข้อ ถ้าพอเข้าใช้งาน Wi-Fi ได้ที่ข้อไหน ให้หยุดและพอได้ทันที ‣ เริ่มนะครับ

1. ให้เป็นข้อแรกก่อนทุกๆ ข้อ สำหรับเรื่อง Wi-Fi ก่อนที่จะทำอะไร ขอให้ตรวจสอบก่อนว่า Router ใช้งานได้ปกติดี ไม่มีอะไรขัดข้อง เช่น สามารถดูได้ง่ายๆ จากอุปกรณ์อื่นๆ ที่ใช้งานร่วมอยู่ด้วย ว่ายังใช้งานเชื่อมต่อออกเนท-เข้าใช้ Wi-Fi ได้เป็นปกติดีอยู่หรือไม่ และถ้าเอะใจว่าออกเนทไม่ได้อาจจะมาจากการรวนของ Router แนะนำให้เปิด-ปิดตัว Router ใหม่ พร้อมกับถ้าสามารถถอดปลั๊กไฟออกไว้สัก 10 วิ. ได้ด้วยก็จะดี ‣ หลังจากนี้ให้กดเลือกเพื่อเข้า Wi-Fi ใหม่อีกครั้ง ถ้ายังไม่ได้ให้ไปที่ข้อต่อไป

2. บน iPad ให้จัดการ `Forget This Network` โดยไปที่ `Settings` ‣ `Wi-Fi` ‣ ดูไปที่ชื่อ Wi-Fi (SSID) ตรงรายชื่อใน `CHOOSE A NETWORK...` ที่เป็นชื่อของเรา แล้วให้คลิกที่ ตัวไอในวงกลม (ด้านขวามือ) แล้วเลือกที่ `Forget This Network` - การทำตรงนี้จะเป็นการสั่งให้เครื่องลืมค่า Wi-Fi ของเราที่เคยตั้งไว้ ‣ หลังจากนี้ให้กดเลือกเพื่อเข้า Wi-Fi ใหม่อีกครั้ง ถ้ายังไม่ได้ให้ไปที่ข้อต่อไป
![Wi-Fi Setting](/assets/img/authors/reallife/2018-01-28/wifi-setting-ios-11.jpg)
![Forget This Network Setting](/assets/img/authors/reallife/2018-01-28/forget-this-network.jpg)

3. ที่ iPad ไปที่ `Settings` ‣ `General` ‣ `Reset` ‣ `Reset Network Settings` - ตรงนี้จะเป็นการรีเซทเพื่อคืนค่าที่เกี่ยวข้องกับเรื่องของ network ทั้งหมด ‣ หลังจากนี้ให้กดเลือกเพื่อเข้า Wi-Fi ใหม่อีกครั้ง ถ้ายังไม่ได้ให้ไปที่ข้อต่อไป

4. ที่ iPad ไปที่ `Settings` ‣ `General` ‣ `Reset` ‣ `Reset All Settings` - ตรงนี้จะเป็นการรีเซทเพื่อคืนค่าทุกอย่างของ iOS โดยที่ยังจะเก็บข้อมูลทุกอย่างที่อยู่บนเครื่องไว้ ‣ หลังจากนี้ให้กดเลือกเพื่อเข้า Wi-Fi ใหม่อีกครั้ง ถ้ายังไม่ได้ให้ไปที่ข้อต่อไป

ถ้าคุณมาถึงตรงนี้ เหมือนเราที่มาถึงที่ข้อสุดท้ายก่อนที่ข้อมูลทั้งหมดและอาการผิดปกติจะหายไป

<a id="caution"></a>*คำเตือน:* มาถึงตรงนี้ขอให้เข้าใจว่า *(1)* Follow this advice at your own risk - ทำต่อไปด้วยความระมัดระวังและรับผิดชอบการกระทำด้วยตัวคุณเอง และ *(2)* ให้ทำการ `Backup` [ข้อมูลไว้ก่อนจะด้วย iTunes หรือบน iCloud ก็ได้](https://support.apple.com/th-th/HT203977) แต่ขอให้ทำ `Backup` ให้เรียบร้อย - ถ้ามีคำถามว่าต่อเนทไม่ได้แล้วจะเข้า iCloud ยังไง? ‣ อย่างของเราจะเข้าเนทด้วยการ Share Hotspot หรือ Wi-Fi แบบที่ไม่ต้องใส่ password (ถึงจะไม่ค่อย secure เท่าไหร่แต่ก็ OK สำหรับใช้ชั่วคราว)

*ข้อ 5. ทางแก้สุดท้าย:* ที่ iPad ไปที่ `Settings` ‣ `General` ‣ `Reset` ‣ `Erase All Content and Settings` แล้วคลิก `Erase Now`
![Erase All Content and Settings](/assets/img/authors/reallife/2018-01-28/erase-all-content-and-settings.jpg)
![Confirm to Erase Now](/assets/img/authors/reallife/2018-01-28/confirm-to-erase.jpg)

ตรงนี้คือจะเป็นการทำ Factory Reset ทุกอย่างบนเครื่องจะหายเกลี้ยงทั้ง: ข้อมูล, แอพ, เพลง และการตั้งค่าต่างๆ ทุกอย่างรวมถึงอาการผิดปกติที่เราเจอด้วย หลังจากเครื่องรีบูทกลับมา เราสามารถใช้งาน Wi-Fi ได้เป็นปกติ และข้อมูลที่สำรองไว้ก็เอากลับมาเข้าเครื่องได้ตามขั้นตอน [การ Restore ข้อมูล](https://support.apple.com/th-th/HT204184)


ท้ายนี้เราหวังว่าทุกอย่างจะเป็นไปด้วยความเรียบร้อย และคุณจะได้ iPad กลับมาใช้งานได้เป็นปกติเหมือนเราเช่นกัน