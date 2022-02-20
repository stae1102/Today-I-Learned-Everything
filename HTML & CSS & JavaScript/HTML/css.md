# 목차
- [목차](#목차)
- [1. CSS가 등장하기 이전](#1-css가-등장하기-이전)
- [2. CSS의 등장](#2-css의-등장)
- [3. CSS 선택자의 기본](#3-css-선택자의-기본)
- [4. 선택자 속성](#4-선택자-속성)
  - [선택자 속성 제어 예시](#선택자-속성-제어-예시)
  - [ID 선택자 사용](#id-선택자-사용)
- [5. 박스 모델](#5-박스-모델)
  - [공간 조정하기](#공간-조정하기)
    - [padding](#padding)
    - [margin](#margin)
- [6. 그리드 소개](#6-그리드-소개)
  - [`<div>` 태그 사용 예시](#div-태그-사용-예시)
  - [grid 값 사용](#grid-값-사용)
- [7. 미디어 쿼리 소개](#7-미디어-쿼리-소개)
  - [미디어 쿼리 적용](#미디어-쿼리-적용)
- [8. CSS 코드의 재사용](#8-css-코드의-재사용)

# 1. CSS가 등장하기 이전
* css 이전 태그 각각에 직접 스타일을 구성해야 했기 때문에 문서를 총괄적으로 수정할 때 시간이 매우 오래 걸리는 것이 문제점이었다.

> 예시
> ```html
> <!-- 생략 -->
> <h1><font color='red'>WEB</font></h1>
> <ol>
>     <li><font color='red'>HTML</font></li>
>     <li><font color='red'>CSS</font></li>
>     <li><font color='red'>JavaScript</font></li>
> </ol>
> <!-- 생략 -->
> ```

# 2. CSS의 등장
* CSS가 등장하며 HTML코드와는 다르게 새롭게 문법을 해석
* `<style>` 태그를 통해 html이 css코드를 해석하고, 독자적인 언어를 사용할 수 있게 됨

> 예시
> ```html
> <!-- 생략 -->
> <head>
>     <title>WEB1 - CSS</title>
>     <meta charset='utf-8'>
>     <style>
> 
>     </style>
> </head>
> <!-- 생략 -->
> ```
> a 태그를 한 번에 꾸미기 위해서
> ```html
> <!-- 생략 -->
> <style>
>     a {
>         color: red;
>     }
> </style>
> <!-- 생략 -->
> ```

위와 같이 css를 사용하여 디자인을 구성하였을 때, 효율적으로 코드를 구성할 수 있다.

또한, style 속성을 사용하여 css 효과를 사용할 수도 있다.

```html
<li><a href='2.html' style='color:red'>CSS</a></li>
```

* 위 예시에서 `a`는 선언자, `color:red`는 선언 혹은 효과, `color`는 속성, `red`는 값을 의미한다. (`;`를 사용하는 이유는 값이 어디까지인지 명확하게 구분하기 위함)

# 3. CSS 선택자의 기본

때로는 같은 태그를 사용한 코드 내에서도 각각의 코드에 따라 다른 스타일을 지정하고 싶을 때가 존재한다. 예를 들어

```html
... 생략 ...

<style>
    a {
        color: black;
        text-decoration: none;
    }
</style>

... 생략 ...

<ol>
    <li><a href="1.html" style="color:gray;">HTML</a></li>
    <li><a href="2.html" style="color:gray;">CSS</a></li>
    <li><a href="3.html">JavaScript</a></li>
</ol>
```

하지만 이러한 상황에서는 계속해서 중복이 발생하고 수정하기 위해선 중복된 만큼의 시간이 더 많이 소요되어 비효율적이다. 따라서 이때 class 혹은 id와 같은 속성을 사용해준다.

# 4. 선택자 속성

```html
... 생략 ...

<style>
    a {
        color: black;
        text-decoration: none;
    }
    .saw {
        color: gray;
    }
</style>

... 생략 ...

<ol>
    <li><a href="1.html" class="saw">HTML</a></li>
    <li><a href="2.html" class="saw">CSS</a></li>
    <li><a href="3.html">JavaScript</a></li>
</ol>
```

class에서도 띄어쓰기를 통해 다양한 태그를 통해 제어할 수 있다.

## 선택자 속성 제어 예시

```html
... 생략 ...

<style>
    a {
        color: black;
        text-decoration: none;
    }
    .saw {
        color: gray;
    }
    .active {
        color: red;
    }

</style>

... 생략 ...

<ol>
    <li><a href="1.html" class="saw">HTML</a></li>
    <li><a href="2.html" class="saw active">CSS</a></li>
    <li><a href="3.html">JavaScript</a></li>
</ol>
```

* 하지만 위 방법은 클래스 내 우선순위가 있기 때문에 클래스가 선언된 순서대로 css를 작성했을 때 정상적으로 작동하기 때문에 좋은 방법이라고 할 수 없다.

```html
<style>
    a {
        color: black;
        text-decoration: none;
    }
    .active {
        color: red;
    }
    .saw {
        color: gray;
    }

</style>

<ol>
    <li><a href="1.html" class="saw">HTML</a></li>
    <li><a href="2.html" class="saw active">CSS</a></li>
    <li><a href="3.html">JavaScript</a></li>
</ol>
```

* **따라서**, 우선순위가 더 높은 속성을 입력하여 확실하게 구분하는 방법이 더 효과적이다.

## ID 선택자 사용
```html
... 생략 ...

<style>
    a {
        color: black;
        text-decoration: none;
    }
    #active {
        color: red;
    }
    .saw {
        color: gray;
    }

</style>

... 생략 ...

<ol>
    <li><a href="1.html" class="saw">HTML</a></li>
    <li><a href="2.html" class="saw" id="active">CSS</a></li>
    <li><a href="3.html">JavaScript</a></li>
</ol>
```

* 이때 알 수 있는 것은 ID 선택자가 먼저 선언됐음에도 불구하고 css가 정상적으로 activation됐다는 것이다. 즉, class 선택자를 id 선택자를 이겼다는 것으로 볼 수 있다.

# 5. 박스 모델

* HTML의 각 태그를 보면 `<h1>`의 경우는 페이지 내에서 여러 개의 줄을 차지하지만, `<a>` 태그나 `<strong>` 태그 등은 글자와 혼용되어 페이지를 차지하지 않는다.
* 이때, `<h1>`과 같이 화면 전체를 쓰는 태그들을 **블록 레벨 엘리먼트(block level element)**, `<a>`와 같이 자기 자신의 콘텐츠 크기만큼 쓰는 태그들을 **인라인 엘리먼트(inline element)** 라고 한다.

> 무조건 적용되는 것은 아니고 css display의 default 값이 block, inline으로 지정돼있기 때문이며, `display: inline;` 혹은 `display: block;`을 통해 엘리먼트를 조절할 수 있다.

## 공간 조정하기

* CSS를 조정하여 콘텐츠와 테두리 사이의 간격과 여백을 조정할 수 있다.

### padding

```html
... 생략 ...
<style>
    h1 {
        border: 5px solid red;
        padding: 20px;
    }
</style>
... 생략 ...
```

### margin

```html
... 생략 ...
<style>
    h1 {
        border: 5px solid red;
        padding: 20px;
        margin: 0;
    }
</style>
... 생략 ...
```

<img src='https://upload.wikimedia.org/wikipedia/commons/thumb/6/64/W3C_and_Internet_Explorer_box_models.svg/450px-W3C_and_Internet_Explorer_box_models.svg.png' width='70%' height='70%'>

따라서 여백을 조정하고 html의 디자인 구조를 변형시킬 수 있으며 `border-bottom: 1px solid gray;` 등의 css 언어로 페이지의 구역을 명확히 표현할 수 있다.

# 6. 그리드 소개

* 간혹 좌측에는 인덱스를, 우측에는 정보들을 나열하고 싶을 때가 있다. 이를 위해 사용하는 방법이 바로 **그리드(Grid)** 이다.
* 그런데 각 구역을 설정하기 전에 HTML의 정체성에 따라 HTML의 코드는 의미가 명확하게 드러나야 하는데, 디자인을 설정하는 것은 실질적인 의미를 내포하고 있지 않기 때문에 이를 위해 의미 없는 태그를 사용해서 구분해야 한다.
* 그럴 때 사용하는 태그가 바로 `<div>`태그와 `<span>`이다.
* `<div>`는 블록 레벨 엘리먼트, `<span>`은 인라인 엘리먼트라는 점에서 차이가 있다.

## `<div>` 태그 사용 예시
```html
<body>
    <div>ARTICLE</div>
</body>
```

* 각각 `<div>`로 구역을 분할하였다면 그 다음 `display`를 사용해 표시 방법을 바꿀 수 있다. 이때, grid 값을 사용할 수 있다.

## grid 값 사용
```html
<style>
    #grid {
        border: 5px solid pink;
        display: grid;
        grid-template-columns: 150px 1fr;
    }
</style>
```

* `display: grid;`를 통해 grid로 표시하게 됐고,
* `grid-template-columns`로 각 div의 크기를 조정할 수 있는데(열; column), 띄어쓰기로 구분하여 순서대로 적용한다.
* px는 절대적인 크기, fr은 상태적인 크기이다.
* 또한 grid에서도 명확하게 태그를 구분하여 grid 태그 하에 있는 태그 선택자를 사용할 수도 있다.

```html
<style>
    #grid ol {
        ... ...
    }
</style>
```

# 7. 미디어 쿼리 소개

* 현재의 웹은 pc 외에도 다양한 디바이스를 통해 접속할 수 있으며, 각 디바이스의 디스플레이 크기에 맞게 웹 사이트의 구성이 변경되는 것이 클라이언트에게 더욱 만족스러운 경험을 제공할 수 있다.
* 이때, 사용자에게 맞춰 웹 페이지를 변경시키는 것이 **반응형 디자인**이라고 할 수 있다.
* 또한, 반응형 디자인을 사용한 웹 페이지를 **반응형 웹** 또는 **반응형 웹 디자인**이라고 하며, 영어로는 **'responsive web'** 이라고 한다.

## 미디어 쿼리 적용
* 이때 반응형 디자인을 위한 CSS의 개념인 **미디어 쿼리**를 통해 구현할 수 있다.
* `@media`로 선언하여 사용할 수 있으며 내용을 추가하여 의미를 나타낼 수 있다.

```html
<style>
    ... 생략 ...
    @media(min-width: 800px) {
        div {
            display: none;
        }
    }
</style>
```

# 8. CSS 코드의 재사용