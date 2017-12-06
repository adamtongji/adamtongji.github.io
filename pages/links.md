---
layout: page
title: Links
description: 引用自模板：没有链接的博客是孤独的
keywords: 友情链接（希望更多）
comments: true
menu: 链接
permalink: /links/
---

> God made relatives. Thank God we can choose our friends.

{% for link in site.data.links %}
* [{{ link.name }}]({{ link.url }})
{% endfor %}
