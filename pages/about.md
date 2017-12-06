---
layout: page
title: About
description: 用心感受数据，用生信治病救人
keywords: Shaliu, adam
comments: true
menu: 关于
permalink: /about/
---

Adam @ tongji univ.

## 联系

{% for website in site.data.social %}
* {{ website.sitename }}：[@{{ website.name }}]({{ website.url }})
{% endfor %}

## Skill Keywords

{% for category in site.data.skills %}
### {{ category.name }}
<div class="btn-inline">
{% for keyword in category.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
