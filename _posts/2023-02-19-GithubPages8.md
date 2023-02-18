---
layout: single
title: '깃허브 블로그 만들기 for Mac OS: 8.페이지 좌 우측 공간'
categories: 'GitHubBlog'
tags: ['GitHub Pages', 'Jekyll']
toc: true   # 우측 목차 여부
author_profile: True  # 좌측 프로필 여부
published: false 
---
## 좌우측 공간
폰트사이즈를 줄여도 좌 우측 공간때문에 보는 입장에서 답답함이 느껴져서 이 부분을 수정하고자 한다. 이 방벙 또한 간단하다.
- _sass/minimal-mistakes/_variables.scss로 이동해 코드를 수정하는데 이 때 코드는 좁을 때와 넓을 때에 따라 다르게 여백이 바뀐다.
- 프로필에 큰 내용이 없기때문에 구조가 어색해지지 않는 선에서 최대한 여백을 줄여보았다.

```scss
# Line 154부터
/*
   Grid
   ========================================================================== */

$right-sidebar-width-narrow: 200px !default;
$right-sidebar-width: 220px !default;
$right-sidebar-width-wide: 250px !default;
// $right-sidebar-width: 300px !default;
// $right-sidebar-width-wide: 400px !default;
```
## 좌측 글 모음 붙이기

## search 이모티콘으로

## About 페이지
