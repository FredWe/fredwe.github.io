---
layout: page
title: 你好 沃德 !
tagline: 开始去做，哪怕只识得一鳞半爪
---
{% include JB/setup %}

### 有什么好的在首页生成posts的摘要列表的方法咩。。。

 > Here's a sample "posts list".  
<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
 >   
这样的根本不够用啊。。。  

Read [Jekyll Quick Start](http://jekyllbootstrap.com/usage/jekyll-quick-start.html)

Complete usage and documentation available at: [Jekyll Bootstrap](http://jekyllbootstrap.com)

## Update Author Attributes

In `_config.yml` remember to specify your own data:
    
    title : My Blog =)
    
    author :
      name : Name Lastname
      email : blah@email.test
      github : username
      twitter : username

The theme should reference these variables whenever needed.
    
## Sample Posts

This blog contains sample posts which help stage pages and blog data.
When you don't need the samples anymore just delete the `_posts/core-samples` folder.

    $ rm -rf _posts/core-samples

Here's a sample "posts list".

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## To-Do

实习啊实习QAQ。。。。。
写报告啊交作业。。。。。。。QAQ

## 可能这样的列表好一些？

{% for post in site.posts %}
  <hr>
  <h1>{{post.title}}</h1>  
  {{post.date|date: "%Y-%m-%d"}}

  {{post.description}}

  {% if post.figure %}
<a href="{{post.url}}"><img src="{{post.img_url}}"/></a>
  {% endif %}

  [阅读全文]({{post.url}})
{% endfor %}

## 第二种列表

然后在posts里面添加
```
<!-- In your posts file, put your marker wherever you want to cut off the post for the main blog page -->

 

---

layout: post

title: truncate example

---

 

Paragraph 1

 

Paragraph 2

 

<!--break-->

 

Paragraph 3

 

Paragraph 4

```

<!-- using the split filter -->

{% for post in site.posts limit:10 %}

   <div class="post-preview">

   <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>

   <span class="post-date">{{ post.date | date: "%B %d, %Y" }}</span>

   {{ post.content | split:'<!--break-->' | first }}

   {% if post.content contains '<!--break-->' %}

      <a href="{{ post.url }}">read more</a>

   {% endif %}

   </div>

   <hr>

{% endfor %}

## 还有就是

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <p>{{ post.excerpt }}</p>
    </li>
  {% endfor %}
</ul>

然后用下面的方式截取：
      \{\{ post.content  | | split:'<!--break-->' | first \}\}  



See [Here](http://jekyllrb.com/docs/posts/)

注意 [liquild api 里的 filter](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers#standard-filters)
