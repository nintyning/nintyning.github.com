---
layout: page
title: 안녕하세요!
tagline: Supporting tagline
---
{% include JB/setup %}

안녕하세요.
nintyning의 개인 블로그 입니다. <br />
Programming & Photograph 에 관련된 정보를 포스팅하고 있습니다.


<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

