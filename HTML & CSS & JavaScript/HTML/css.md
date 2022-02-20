# 목차
- [목차](#목차)
- [CSS가 등장하기 이전](#css가-등장하기-이전)
- [CSS의 등장](#css의-등장)
- [CSS 선택자의 기본](#css-선택자의-기본)
- [선택자 속성](#선택자-속성)
  - [선택자 속성 제어 예시](#선택자-속성-제어-예시)
  - [ID 선택자 사용](#id-선택자-사용)
- [박스 모델](#박스-모델)

# CSS가 등장하기 이전
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

# CSS의 등장
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

# CSS 선택자의 기본

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

하지만 이러한 상황에서는 계속해서 중복이 발생하고 수정하기 위해선 중복된 만큼의 시간이 더 많이 소요되어 비효율적이다. 따라서 이때 class 혹은 id와 같은 속성을 사용해준다.

# 선택자 속성

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

<ol>
    <li><a href="1.html" class="saw">HTML</a></li>
    <li><a href="2.html" class="saw active">CSS</a></li>
    <li><a href="3.html">JavaScript</a></li>
</ol>

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

<ol>
    <li><a href="1.html" class="saw">HTML</a></li>
    <li><a href="2.html" class="saw" id="active">CSS</a></li>
    <li><a href="3.html">JavaScript</a></li>
</ol>

* 이때 알 수 있는 것은 ID 선택자가 먼저 선언됐음에도 불구하고 css가 정상적으로 activation됐다는 것이다. 즉, class 선택자를 id 선택자를 이겼다는 것으로 볼 수 있다.

# 박스 모델