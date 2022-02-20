# 목차
- [목차](#목차)
- [1. `<script>` 태그](#1-script-태그)
- [2. 이벤트](#2-이벤트)
  - [2-1. 버튼 이벤트](#2-1-버튼-이벤트)
  - [2-2. 텍스트 상자 이벤트](#2-2-텍스트-상자-이벤트)
- [3. 데이터 타입 - 문자열과 숫자](#3-데이터-타입---문자열과-숫자)

# 1. `<script>` 태그
* 기본적으로 자바스크립트는 HTML 위에서 동작하는 언어이다.
* 자바스크립트 코드를 넣기 위해서 우선 웹 브라우저에게 지금부터 HTML에 자바스크립트 코드가 시작된다는 사실을 알려야 한다.
* 이때, 사용하는 태그가 `<script>`태그이다.
```html
<body>
    <script>
        document.write('Hello world');
    </script>
</body>
```
* 자바스크립트를 통해 나타낸 문자와 HTML 태그를 통해 나타낸 문자의 차이는 자바스크립트의 경우 동적이기 때문에 1+1을 논리적으로 계산하여 동작한다는 점이 특징이다.

```html
<body>
    <script>
        document.write(1+1);
    </script>
    1 + 1
</body>
```

# 2. 이벤트
* 이벤트는 자바스크립트가 사용자와 상호작용하는 데 핵심적인 역할을 한다.
* 예를 들어 버튼을 생성한다고 해보자면

## 2-1. 버튼 이벤트
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <input type="button" value="hi">
    </body>
</html>
```

<body>
    <input type="button" value="hi">
</body>
  
위 코드를 통해 버튼을 생성할 수 있는데 이 기능을 사용자와 상호작용할 수 있도록 자바스크립트 코드를 작성할 수도 있다.

```html
<body>
    <input type="button" value="hi" onclick="alert('hi')">
</body>
```

<body>
    <input type="button" value="hi" onclick="alert('hi')">
</body>

* `onclick`의 속성 값은 웹 브라우저가 기억해 뒀다가, onclick 속성이 위치하고 있는 태그를 사용자가 클릭했을 때, 자바스크립트 코드를 자바스크립트 문법에 따라 해석해서 웹 브라우저가 실행한다.
* 이처럼 웹 브라우저 위에서 일어나는 일들을 사건, 영어로는 이벤트(event)라고 한다.
* 어떤 이벤트가 일어났을 때 어떠한 자바스크립트 코드를 실행하게 하는 것이 `onclick`이라는 것이다.
* 이 외에도 무수한 이벤트가 있는데 다음과 같다.

## 2-2. 텍스트 상자 이벤트
  
```html
<body>
    <input type="text" />
</body>
```
<body>
    <input type="text" />
</body>
  
* 이때 내용이 변했을 때를 체크하는 이벤트도 존재한다.
  
```html
<body>
    <input type="text" onchange="alert('changed')"/>
</body>
```
  
<body>
    <input type="text" onchange="alert('changed')"/>
</body>
  
* 혹은 아무 키를 눌렀을 때 경고창을 생성할 수도 있다.
  
```html
<body>
    <input type="text" onkeydown="alert('key down!')"/>
</body>
```
  
<body>
    <input type="text" onkeydown="alert('key down!')"/>
</body>
  
이처럼 `on`으로 시작하는 속성들이 있는데 이러한 속성들을 자바스크립트에서는 **이벤트**라고 한다.

# 3. 데이터 타입 - 문자열과 숫자

* 데이터 타입은 한국어로 자료형으로 문자와 숫자 등이 존재한다. 