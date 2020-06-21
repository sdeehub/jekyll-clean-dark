---
layout: post
title: "มาดู YAML ที่ใช้ใน Jekyll กัน"
date: 2019-03-11 17:35:19 +0700
description: Post นี้เราจะมาดู YAML ที่ใช้ในงานร่วมกับ Jekyll กัน - มี 2 ตัวอย่างที่เอามาในวันนี้คือ Relative URL กับ Sort
tags: Jekyll
comments: true
---
*ก่อนอื่นขอแนะนำ:*
- [YAML Tutorial](https://rhnh.net/2011/01/31/yaml-tutorial/)
- [YAML Tutorial in the Context of Jekyll](https://deepnn.github.io/mydoc_yaml_tutorial.html)

### 1) Relative URL
ส่วนมากจะใช้เพื่อให้อ้าง URL ได้สะดวกเวลาที่เราต้องเขียน `includes html` เช่นพวกหน้าการจัด `Pagination` - ดูตัวอย่าง Code:

{% raw %}
```html
{% if paginator.previous_page %}
  <a href="{{ paginator.previous_page_path | relative_url }}" class="previous"><i class="fa fa-angle-left" aria-hidden="true"></i> Previous</a>
{% endif %}
{% if paginator.next_page %}
  <a href="{{ paginator.next_page_path | relative_url }}" class="next">Next <i class="fa fa-angle-right" aria-hidden="true"></i></a>
{% endif %}
```
{% endraw %}

ถ้าเทียบกับแบบที่เป็นการอ้าง URL ทั่ว ๆ ไป:

{% raw %}
```html
{% if post.title %}
  <a href="{{ post.url | prepend: site.baseurl }}" class="recent-item" style="background: url({{post.img}}) center no-repeat; background-size: cover;"><span>{{ post.title }}</span></a>
{% endif %}

{% for tag in page.tags %}
  <a href="{{site.baseurl}}/tags#{{tag}}" class="tag">| {{ tag }}</a>
{% endfor %}
```
{% endraw %}

### 2) Sort
เอาไว้ใช้เวลาทำหน้า `pages` ที่ต้องแสดง list ของเนื้อหาต่าง ๆ เช่นตอนเรียงลำดับ `Posts` ที่แยกตาม `Tags` ต่างๆ

{% raw %}
```html
<!--cycles through tag list and creates subheader for each tag name...-->
  {% for item in (0..site.tags.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ tag_words[item] | strip_newlines }}{% endcapture %}
      <h2 id="{{ this_word | cgi_escape }}">{{ this_word }}</h2>
<!--  lists all posts corresponding to specific tag...-->
    {% assign sorted = (site.tags[this_word] | sort) %}
    {% for post in sorted %}{% if post.title != null %}
      <div class="tag-list">
          <span><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></span>
          <small><span>| {{ post.date | date_to_string }}</span></small>
      </div>
    {% endif %}{% endfor %}
  {% endunless %}{% endfor %}
```
{% endraw %}

จากตัวอย่าง code ที่แปะไว้นี่น่าจะช่วยทำให้พวกเราทำงานกับ YAML และ Jekyll ได้ง่ายขึ้นแล้วนะครับ - วันนี้พอแค่นี้ก่อน สวัสดี 24 มีค. เตรียมตัวไปใช้สิทธิเลือกตั้งกันด้วยนะพวกเรา
