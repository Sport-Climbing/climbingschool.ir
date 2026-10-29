---
layout: default
title: دوره‌ها
description: >-
  دوره‌های آموزش سنگ‌نوردی مدرسه. هر دوره وقتی اعلام شود در این فهرست می‌آید.
permalink: /courses/
lang: fa-IR
dir_attr: rtl
---

<h1>دوره‌ها</h1>
<p>دوره‌های آموزش سنگ‌نوردی مدرسه در این فهرست منتشر می‌شود. معرفی مدرسه در <a href="{{ '/' | relative_url }}">خانه</a> است.</p>
{% assign course_posts = site.courses | sort: "date" | reverse %}
{% if course_posts.size == 0 %}
<p>هنوز دوره‌ای در سایت ثبت نشده است.</p>
{% else %}
{% include hub-filter.html toolname="filter_courses" tooldescription="Filter the published climbing-school courses listed on this page by title or summary text." %}
<ul data-hub-list>
  {% for post in course_posts %}
  <li class="news-hub-item">
    <a href="{{ post.url }}">{{ post.title }}</a>
    {% if post.date %}
    <p class="meta">
      <time datetime="{{ post.date | date_to_xmlschema }}">{% include jalali-date.html date=post.date %}</time>
    </p>
    {% endif %}
    {% if post.description %}
    <p class="news-hub-blurb">{{ post.description }}</p>
    {% elsif post.excerpt %}
    <p class="news-hub-blurb">{{ post.excerpt | strip_html | truncatewords: 22 }}</p>
    {% endif %}
  </li>
  {% endfor %}
</ul>
{% endif %}
