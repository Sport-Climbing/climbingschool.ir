---
layout: default
title: اخبار
description: >-
  اخبار و اطلاعیه‌های مدرسه سنگ‌نوردی.
permalink: /news/
lang: fa-IR
dir_attr: rtl
---

<h1>اخبار</h1>
<p>اخبار و اطلاعیه‌های مدرسه اینجاست. دوره‌ها در <a href="{{ '/courses/' | relative_url }}">فهرست دوره‌ها</a> منتشر می‌شوند.</p>
{% assign wire_posts = site.news | where_exp: "post", "post.layout != 'redirect'" | sort: "date" | reverse %}
{% if wire_posts.size == 0 %}
<p>هنوز خبری در این بخش منتشر نشده است.</p>
{% else %}
{% include hub-filter.html toolname="filter_news" tooldescription="Filter the climbing-school news items listed on this page by title or summary text." %}
<ul data-hub-list data-hub-page-size="10" data-hub-page-key="w">
  {% for post in wire_posts %}
  {% include news-hub-item.html post=post %}
  {% endfor %}
</ul>
{% endif %}
