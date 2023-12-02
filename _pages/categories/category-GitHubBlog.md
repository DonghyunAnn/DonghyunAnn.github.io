---
title: "Jekyll/GitHub 블로그 만들기"
layout: archive
permalink: categories/GitHubBlog
author_profile: true
sidebar_main: true
classes: wide
---

{% assign posts = site.categories.GitHubBlog %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}