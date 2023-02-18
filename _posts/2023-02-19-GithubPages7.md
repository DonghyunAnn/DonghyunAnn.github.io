---
layout: single
title: '깃허브 블로그 만들기 for Mac OS: 7. 폰트 디자인 및 사이즈 설정'
categories: 'GitHubBlog'
tags: ['GitHub Pages', 'Jekyll']
toc: true   # 우측 목차 여부
author_profile: True  # 좌측 프로필 여부
---


## 폰트 변경
- [구글폰트(링크)](https://fonts.google.com)이동
- 사이트에서 언어를 Korean으로 선정해주고, Type Something에 한국어와 영어를 동시에 적어놓고 마음에 드는 폰트를 찾는다

![font1](/assets/blog_img/font1.png)

- 마음에 드는 폰트로 들어가서 Select(+)를 눌러준다

![font2](/assets/blog_img/font2.png)

- 이후 @import를 눌러서 해당 부분만 복사해서 _sass/minimal-mistakes.scss 로 이동 후 맨 아래에 다음과 같이 붙여넣기

```scss
/* google fonts */
@import url('https://fonts.googleapis.com/css2?family=Gowun+Batang&display=swap');
```

- _sass/minimal-mistakes/_variables.scss로 이동해서 15번쨰줄에 나의 폰트명을 추가해준다. 폰트명은 구글폰트 우측 하단의 CSS rules to specify families 에 있다.

``` scss
# Line 15 부터
/* system typefaces */
$serif: Georgia, Times, serif !default;
$sans-serif:   'Gowun Batang', -apple-system, BlinkMacSystemFont, "Roboto", "Segoe UI",
   "Helvetica Neue", "Lucida Grande", Arial, sans-serif !default;     # 세번째에 추가했을 때 실행이 안되서 첫번째 자리에 추가함
$monospace: Monaco, Consolas, "Lucida Console", monospace !default;
```

## 폰트 크기 
- 개인적으로 폰트 사이즈가 너무 커서 한번에 전달되는 정보량이 너무 적고, 코드를 보는데 너무 적합하지 않다고 판단해서 전반적으로 폰트사이즈를 줄이고자 했다. 방법은 매우 간단하다. 
- /_sass/minimal-mistakes/_reset.scss 에서 코드 수정
```scss
# 7번째 줄 부터
html {
  /* apply a natural box layout model to all elements */
  box-sizing: border-box;
  background-color: $background-color;
  font-size: 14px;     # 모바일 환경

  @include breakpoint($medium) {
    font-size: 16px;     # HD
  }

  @include breakpoint($large) {
    font-size: 16px;     # FHD 이상
  }

  @include breakpoint($x-large) {
    font-size: 16px;     # FHD 이상
  }

  -webkit-text-size-adjust: 100%;
  -ms-text-size-adjust: 100%;
}
```
