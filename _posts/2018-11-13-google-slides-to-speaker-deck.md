---
layout: post
title: "ทำ Slide บน Jekyll ยังไง?"
date: 2018-11-13 15:08:20 +0700
description: มาดูการแปะ Slide บน Jekyll ด้วย Google Slides และ Speaker Deck กันครับ
tags:
- Jekyll
- Tool
comments: true
---
เริ่มแรกอันนี้มาจาก Google Slides โดยตรง จากการคลิกที่ `File` ‣ `Publish to the web...` ‣ `Embed` ตั้งค่าต่างๆ ให้ตรงตามที่อยากได้ เอา code ตรง <iframe> มาเก็บไว้แล้วคลิก `Published`

![Google Slides Embed](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_600/v1542194195/Screenshot_from_2018-11-14_18-15-44.png)

พอเอา code ไปแปะที่ใน Jekyll ก็จะได้ผลลัพธ์ออกมาคล้ายๆ แบบนี้ (แต่ยังไม่ Responsive)

<style>
.responsive-wrap iframe{ max-width: 100%;}
</style>
<div class="responsive-wrap">
<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vQsaK6p2sI3jbV1LkC0AX190U7jmTK8muY4cs8fiBONsJKlj_IGHT2-Jhtlk06jwpBo02VoR517g1z8/embed?start=false&loop=false&delayms=3000" frameborder="0" width="960" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
</div><br />

จากไฟล์ตัวอย่างของเราจะได้ code มาแบบนี้

```html
<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vQsaK6p2sI3jbV1LkC0AX190U7jmTK8muY4cs8fiBONsJKlj_IGHT2-Jhtlk06jwpBo02VoR517g1z8/embed?start=false&loop=false&delayms=3000" frameborder="0" width="960" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
```
และเพื่อให้หน้าจอแสดง Responsive ด้วย เราก็จะใส่ CSS ตามเนื้อหาที่แนะนำไว้ใน [Dev Notes](https://dev-notes.eu/2016/09/embed-google-slides-in-jekyll/) คือเพิ่ม `<style>` กับ `<div>` ครอบไว้อีกที กลายเป็นแบบนี้

```html
<style>
.responsive-wrap iframe{ max-width: 100%;}
</style>
<div class="responsive-wrap">
<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vQsaK6p2sI3jbV1LkC0AX190U7jmTK8muY4cs8fiBONsJKlj_IGHT2-Jhtlk06jwpBo02VoR517g1z8/embed?start=false&loop=false&delayms=3000" frameborder="0" width="960" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
</div>
```

เท่านี้ก็เรียบร้อยแล้วสำหรับการเอา Slide มาจาก Google Slides

ส่วนอันนี้มาจาก Speaker Deck - ด้วยขั้นตอนง่ายๆ คือ `Upload a deck` (ซึ่งรับไฟล์ .pdf) แล้วก็เอา embed code ออกมาแปะที่ Jekyll ของเรา

![Speaker Deck Embed](https://res.cloudinary.com/sdees-reallife/image/upload/c_scale,w_600/v1542201180/Screenshot_from_2018-11-14_20-12-21.png)

ผลลัพธ์ออกมาแบบนี้ และก็จะจัดการตัวเองได้เรียบร้อยไม่ต้องใส่อะไรเพิ่ม

<script async class="speakerdeck-embed" data-id="27cb35e9f1d844dab0230dc3fc78cdd9" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script><br />

สำหรับ code ที่เราใช้ในตัวอย่างนี้ก็คือแบบนี้

```html
<script async class="speakerdeck-embed" data-id="27cb35e9f1d844dab0230dc3fc78cdd9" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>
```

ผลลัพธ์ก็ตามที่เห็นแล้วนะครับ คราวนี้ก็อยู่ที่ว่าพวกเราจะชอบแบบไหน สามารถเลือกใช้ตามที่ต้องการได้สบายๆ กันเลย

ขอบคุณที่ติดตามอ่านเรื่องของพวกเรานะครับ มีข้อแนะนำเพิ่มเติมสามารถบอกกันได้ใน comment เช่นเคยครับ แล้วพบกันใหม่ โชคดีมีชัย มีตังค์ใช้กันทั่วหน้า ไว้ค่อยมาเจอกันใหม่ สวัสดีนะครับ
