---
layout: single
title: '깃허브 블로그 만들기 for Mac OS: 8.페이지 좌 우측 공간 넓히기, 좌측 목차, 하이퍼링크 밑줄 제거'
excerpt: ''
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

- Before

![before](/assets/blog_img/linkbefore.png)

- After

![after](/assets/blog_img/linkafter.png)


## 블로그 좌측 사이드바

### 결과 예시
<img src="/assets/blog_img/sidebar_result.png" width="250" height="500"/>

### 방문자수 체크
![hits](/assets/blog_img/hits.png)

  - [HITS](https://hits.seeyoufarm.com)로 들어가서 target url에 자신의 블로그 url 입력
  - 자신이 원하는 디자인으로 Options 선택 (이모티콘 및 색상 설정 가능)
  - 생성된 HTML LINK 복사 

### 좌측 카테고리 목차
  - _pages/category-archieve.md 수정
  ``` python
  title: "Category"
  layout: "categories"
  permalink: "/categories/"
  author_profile: true
  sidebar_main: true    # 추가
  ```

  - _includes/nav_list_main 생성 (아래 코드 그대로 붙이시고 <ul> 태그 위주로 수정해주시면 됩니다)
  
  ``` python
  <!--전체 글 수를 세기 위한 연산. sum 변수에 전체 글 수 저장-->
  {% assign sum = site.posts | size %}
  <nav class="nav__list">
    <input id="ac-toc" name="accordion-toc" type="checkbox" />
    <label for="ac-toc">{{ site.data.ui-text[site.locale].menu_label }}</label>
    <ul class="nav__items" id="category_tag_menu">
        <!--전체 글 수-->
        <li>
              📑 <span style="font-family:'Cafe24Oneprettynight';">전체 글 수</style> <span style="font-family:'Coming Soon';">{{sum}}</style> <span style="font-family:'Cafe24Oneprettynight';">개</style> 
        </li>
        
        <!--여기서부터 카테고리별로 나누기-->
        <li>
          <!--span 태그로 카테고리들을 크게 분류-->
          <span class="nav__sub-title">ETC</span>
              <!--ul 태그로 같은 카테고리들 모아둔 페이지들 나열-->
              <ul>
                  <!--Cpp 카테고리 글들을 모아둔 페이지인 /categories/cpp 주소의 글로 링크 연결-->
                  <!--category[1].size 로 해당 카테고리를 가진 글의 개수 표시--> 
                  {% for category in site.categories %}
                      {% if category[0] == "GitHubBlog" %}
                          <li><a href="/categories/GitHubBlog" class="">Blog ({{category[1].size}})</a></li>
                      {% endif %}
                  {% endfor %}
              </ul>
          <span class="nav__sub-title">Side Project</span>
          <span class="nav__sub-title">Data Engineering</span>
          <span class="nav__sub-title">Deep Learning</span>
        </li>
    </ul>
  </nav>
  ```
- _includes.sidebar.html 수정 (최종)
![sidebar_category](/assets/blog_img/sidebar_category.png)s
