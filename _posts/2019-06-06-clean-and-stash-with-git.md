---
layout: post
title: "git clean หรือ git stash - จะใช้อะไร? แล้ว เมื่อไหร่?"
date: 2019-06-06 17:29:49 +0700
description: เวลาที่งานเยอะๆ ทำแล้วยังไม่เสร็จดี หรือทำแล้วเหมือนจะไม่สะอาด แล้วจะเอาขึ้น git ก็ยังไม่ใช่ที่ - จะเอายังไงดี? มีคำแนะนำอยู่ที่นี่แล้วครับ
tags:
- Git
comments: true
---
ก่อนอื่นถ้าพอมีเวลา เข้ามาอ่าน 3 หน้านี้ก่อนเลย - ใช่! แล้วก็ไม่ต้องอ่านที่พวกเราเขียนนี่ต่อแล้วล่ะ

- [git stash](https://git-scm.com/docs/git-stash)
- [git clean](https://git-scm.com/docs/git-clean)
- [Git Tools - Stashing and Cleaning](https://git-scm.com/book/en/v2/Git-Tools-Stashing-and-Cleaning)

เอาล่ะ! คุณจะอ่านหรือไม่อ่าน แต่พวกเราก็ต้องเขียนเก็บไว้ เพราะก็อย่างที่เคยบอกไป ว่าว่างๆ หรือถ้าต้องใช้ได้กลับมาเปิดไว้อ้างอิงกัน - ถึงเวลามาเริ่มกันแล้ว:

*git clean* - เอาอันนี้ก่อน ส่วนใหญ่จะเอาไว้สำหรับลบไฟล์ที่ไม่ได้ถูก track ออกไป

สำหรับคำว่าไม่ได้ถูก track หรือ untracked นี่คือยังไง? - ตัวอย่างก็เช่นเพิ่มไฟล์เข้าไปใหม่ ยังไม่ทันได้ `git add .` ก็ประมาณนี้ล่ะ ลองดูตัวอย่างข้างล่าง

```console
$ git status
On branch gh-pages
Your branch is up to date with 'origin/gh-pages'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	_posts/2019-06-06-clean-and-stash-with-git.md
	tag/Git.md

nothing added to commit but untracked files present (use "git add" to track)
$
```

ชัดเจนว่ามีไฟล์ที่ untracked อยู่ 2 ไฟล์ ถ้า `git clean` ก็จะลบไฟล์นี้ออกไปเลย สำหรับคำสั่งที่จะใช้ก็คือ:

`git clean -f`

จะต้องมี `-f` ด้วยเพื่อ force การลบ เพราะว่านี่คือคำสั่งอันตราย แต่ถ้ายังไม่ลบ แค่อยากรู้ก่อนว่าถ้าสั่งแล้วจะมีอะไรถูกลบไปบ้างถ้าเราเกิดจะสั่ง `git clean` ขึ้นมาจริงๆ - ให้ใช้เราคำสั่งแบบนี้ก่อนคือ:

`git clean -n`

โดยที่ `-n` ก็คือ dry-run ยังไม่ได้ run กันจริงๆ แค่เอามาโชว์ให้ดูกันก่อน จากตัวอย่างก็จะได้แบบนี้

```console
$ git clean -n
Would remove _posts/2019-06-06-clean-and-stash-with-git.md
Would remove tag/Git.md
$
```

*git stash* - ถัดมาอันนี้ถ้าเกิดเป็นไฟล์ที่โดน track แล้ว หรือ tracked - เช่นจากตัวอย่างถ้าเราเกิดสั่ง `git add .` เข้าไปแบบนี้

```console
$ git add .
$ git status
On branch gh-pages
Your branch is up to date with 'origin/gh-pages'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   _posts/2019-06-06-clean-and-stash-with-git.md
	new file:   tag/Git.md

$
```

แบบนี้ถ้า `git clean` ก็จะไม่เกี่ยวล่ะ เพราะว่า 2 ไฟล์ใหม่นี้กลายเป็นโดน track หรือ tracked ไปเรียบร้อยแล้ว แต่แค่ยังไม่ได้ commit!

ต่อกันเลยนะ - คราวนี้ถ้าจะยังไม่ commit แต่จะเก็บงานที่ทำตรงนี้ไว้ก่อนล่ะ เช่นต้องเก็บไว้ก่อนเพราะยังไม่เสร็จ ถ้า push ไปก็ไม่ได้นะ แต่ก็ต้องไป pull อัพเดทอื่นมา (น่าจะประมาณนี้) เพื่อความสะดวกก็จัดการเก็บสิ่งที่เกิดขึ้น 'ในระหว่างทาง' นี้ด้วยคำสั่ง:

`git stash`

ถ้าจะดูว่ามี stash ตรงไหนบ้างที่เราเก็บไว้กี่ครั้งแล้วก็ใช้คำสั่ง:

`git stash list`

และถ้าจะกลับไปเอา stash ตรงตำแหน่งที่ว่ามาใช้ก็ให้เรียก:

`git stash apply stash@{0}`

และถ้าจะไม่เก็บ stash ไว้แล้วก็ให้เรียก:

`git stash drop stash@{0}`

โดยที่ `stash@{0}` นี่คือ stash ที่ต้องการนั่นเอง

ดูตัวอย่างนี้นะครับ:

```console
$ touch file_1.txt
$ git add .
$ git stash
Saved working directory and index state WIP on gh-pages: fe163ee update and done

$ git stash list
stash@{0}: WIP on gh-pages: fe163ee update and done

$ ls file_1.txt
ls: cannot access 'file_1.txt': No such file or directory

$ git stash apply
$ ls file_1.txt
file_1.txt
$
```

1. ตรงที่เราสร้างไฟล์ใหม่ `touch file_1.txt`
2. เสร็จแล้วก็เพิ่มให้ track ไฟล์นี้เข้าไปด้วย `git add .`
3. แล้วเราก็ `git stash` - เก็บงานส่วนนี้ไปก่อน เอาตัวอย่างแค่ง่ายๆ ในที่นี้คือแค่ไฟล์ใหม่ไฟล์เดียว
4. พอ `ls file_1.txt` ก็จะไม่เจออะไรเพราะถูกเก็บไปแล้ว
5. ถ้าจะกลับไปตรงที่ stash (เพื่อเอาไฟล์นั้นมา) ก็ `git stash apply` - เวลาที่ไม่ได้ระบุว่า stash ไหนก็คือจะหมายถึงอันล่าสุดนั่นเอง

อธิบายตามขั้นตอนก็จะได้ความเข้าใจสักประมาณนี้นะครับ ยังไงลองใช้ดูจะได้เห็นชัดกว่า จบตอนก่อนนะครับและถ้าจะให้ดีกลับไปอ่าน 3 หน้าด้านบน - นะครับนะ!
