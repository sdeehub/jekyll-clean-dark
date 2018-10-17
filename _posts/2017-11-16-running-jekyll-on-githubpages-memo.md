---
layout: post
title: "บันทึกช่วยจำในการใช้ Jekyll ร่วมกับ GitHub Pages"
date: 2017-11-16 17:17:47 +0700
tags: Jekyll
description: เนื้อหาในตอนนี้เราจะไม่ได้พูดถึงการติดตั้ง Jekyll ใดๆ เลย หรือแม้แต่ที่มาที่ไปของการใช้งาน GitHub ถ้านั่นคือสิ่งที่คุณคิดว่าต้องทำความเข้าใจเพิ่มละก็ ขอให้ลองหาอ่านเรื่อง การติดตั้ง Jekyll, การใช้งาน GitHub และ GitHub Pages ซะก่อน นั่นน่าจะเป็นเรื่องที่ดีมาก :)
comments: true
---
เอาล่ะและนี่คือ memo หรือบันทึกช่วยจำถ้าคุณจะต้องทำให้ Jekyll กับ GitHub Pages มาอยู่ด้วยกัน - แบบไหนนะเหรอ? นั่นคือสิ่งที่เราหมายถึงว่า website ถูกสร้างขึ้นมาด้วย Jekyll แล้วก็เอาไป host ไว้บน GitHub Pages

และจากย่อหน้านี้ก็คือการเริ่มกันซะที - หลังจากที่ได้ทำการติดตั้ง Jekyll ลงบนเครื่องของเราเป็นที่เรียบร้อยแล้ว

### ขั้นตอนที่ 1 (PC Ubuntu): สร้าง Jekyll local site
```bash
# สร้าง Jekyll site: ./sdeesreallife.github.io (ชื่อองค์กรตามด้วย.github.io)
$ jekyll new sdeesreallife.github.io

# เปลี่ยน path ไปที่: sdeesreallife.github.io
$ cd sdeesreallife.github.io

# สั่งให้ Jekyll ทำการ build site บน local server
$ bundle exec jekyll server

# เปิด browser ไปที่: http://localhost:4000
```
### ขั้นตอนที่ 2: สร้าง Repository บน GitHub
Login เข้าใช้งาน GitHub

คลิกที่รูป Profile ของเรา แล้วเลือก Your Profile

สร้าง Repository ขึ้นมาใหม่ในชื่อเดียวกับชื่อองค์กรตามด้วย.github.io
`https://github.com/sdeesreallife/sdeesreallife.github.io`
#### ขั้นตอนที่ 3: Commit local site ไปที่ GitHub (PC Ubuntu)
```bash
$ cd sdeesreallife.github.io
$ git init
$ git remote add origin https://github.com/sdeesreallife/sdeesreallife.github.io
$ git add .
$ git commit -m "initial commit of the Jekyll's site template."
$ git push -u origin master

# เปิด browser ไปที่:https://sdeesreallife.github.io
```
### Tips and Tricks
เพื่อให้การใช้งาน Jekyll บน loacl site สะดวกขึ้นอีกนิด เราจะใช้ Plugin Jekyll::Livereload ร่วมด้วย

ขั้นตอนการติดตั้ง: เพิ่มบรรทัด `gem 'jekyll-livereload'` ในไฟล์ Gemfile และสั่ง bundle
```bash
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.6"
  gem "jekyll-livereload" # เพิ่มบรรทัดนี้ลงไป
end

$ bundle
```

ขั้นตอนการรัน: ใช้คำสั่ง `jekyll serve --livereload` หรืออีกแบบที่เพิ่มการแสดง posts ที่เป็น drafts ให้ด้วย `bundle exec jekyll serve --drafts --livereload` - ผลลัพธ์ที่ได้คือทุกครั้งที่เราแก้ไข local site ต่อไปนี้ Jekyll จะทำการ auto regenerated และเพิ่มการ reload หน้าเว็บให้ด้วยเลย :)
