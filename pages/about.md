---
layout: page
title: About
description: 打码改变世界
keywords: chuanliang Zhu, 朱传亮
comments: true
menu: 关于
permalink: /about/
---

我是朱传亮

来自重庆邮电大学的普通小硕一枚

坚信越努力，越幸运，努力可以改变人生。  

**欢迎关注我哦**  
![微信](http://images2017.cnblogs.com/blog/1161753/201710/1161753-20171004141054365-1663016846.png "微信")  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**微信**  
![QQ](http://images2017.cnblogs.com/blog/1161753/201710/1161753-20171004141232396-1196985087.png "QQ")  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**QQ**
  
  




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
