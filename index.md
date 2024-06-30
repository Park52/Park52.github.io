---
layout: home
title: Welcome to My Blog
---

# Welcome to My Blog

This is the home page of my Jekyll blog.

## About Me

![Profile Image](/assets/images/arsenal.svg)

Hello! I'm a software developer passionate about open source and software development. Welcome to my personal blog where I share my projects and ideas. I also love football and Arsenal.

## Latest Blog Posts

<ul>
  {% for post in site.posts limit:5 %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <small>{{ post.date | date_to_string }}</small>
    </li>
  {% endfor %}
</ul>

## study
Below are the posts related to my studies.

<ul>
  {% for post in site.posts %}
    {% if post.categories contains 'study' %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        <small>{{ post.date | date_to_string }}</small>
      </li>
    {% endif %}
  {% endfor %}
</ul>

## Projects

<ul>
  <li><a href="/projects/project1/">Project 1</a>: A brief description of Project 1.</li>
  <li><a href="/projects/project2/">Project 2</a>: A brief description of Project 2.</li>
</ul>

## Contact

You can reach me at [wogus8660@naver.com](mailto:wogus8660@naver.com).