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

### Relative URL
ส่วนมากจะใช้เพื่อให้อ้าง URL ได้สะดวกเวลาที่เราต้องเขียน `include:` พวกหน้าการจัด `Pagination` - ตัวอย่าง Code:

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

เทียบกับแบบที่เป็นการอ้าง URL ทั่วๆ ไป:

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
