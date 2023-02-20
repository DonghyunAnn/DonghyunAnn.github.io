---
layout: single
title: '깃허브 블로그 만들기 for Mac OS: 8.페이지 좌 우측 공간 넓히기, 좌측 목차, 하이퍼링크 밑줄 제거'
excerpt: ' '
categories: 'GitHubBlog'
tags: ['GitHub Pages', 'Jekyll']
toc: true   # 우측 목차 여부
toc_sticky: true   # 우측 목차 따라오기

author_profile: True  # 좌측 프로필 여부
published: true
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
$right-sidebar-width: 250px !default;
$right-sidebar-width-wide: 300px !default;
// $right-sidebar-width: 300px !default;
// $right-sidebar-width-wide: 400px !default;
```

- Before
![before](/assets/blog_img/before.png)

- After
![after](/assets/blog_img/after.png)

## 좌측 글 모음 붙이기
그리고 더 알차게 화면을 채우기 위해서 좌측에 목차를 추가하려고 한다. 이와 관련되 내용은 [식빵맘님 블로그 링크](https://ansohxxn.github.io/blog/category/)에 설명이 너무 자세히 잘 되어있어서 추가 작성의 필요성을 느끼진 목했다.

## 하이퍼링크 밑줄제거
- _sass/_minimal-mistakes/_base.scss 로 이동해서 127번쨰 줄 코드 수정
- 훨씬 깖끔하고 가독성도 좋아진 느낌을 받는다,

```scss
a {
  text-decoration: none; // 추가된 코드

  &:focus {
    @extend %tab-focus;
  }

  &:visited {
    color: $link-color-visited;
  }

  &:hover {
    color: $link-color-hover;
    outline: 0;
  }
}
```
-before
![before](/assets/blog_img/linkbefore.png)

-after
![after](/assets/blog_img/linkafter.png)
