# 목차
- [목차](#목차)
- [1. `<script>` 태그](#1-script-태그)
- [2. 이벤트](#2-이벤트)
  - [2-1. 버튼 이벤트](#2-1-버튼-이벤트)
  - [2-2. 텍스트 상자 이벤트](#2-2-텍스트-상자-이벤트)
- [3. 데이터 타입 - 문자열과 숫자](#3-데이터-타입---문자열과-숫자)
  - [3-1. 숫자](#3-1-숫자)
  - [3-2. 문자열](#3-2-문자열)
    - [`.length`](#length)
    - [`.toUpperCase()`](#touppercase)
    - [`.index0f()`](#index0f)
    - [`.trim()`](#trim)
- [4. 변수와 대입 연산자](#4-변수와-대입-연산자)
  - [아래 내용은 기존 내용을 복습](#아래-내용은-기존-내용을-복습)
- [5. CSS 기초: style 속성](#5-css-기초-style-속성)
- [6. CSS 기초: `<style>` 태그](#6-css-기초-style-태그)
- [7. CSS 기초: 선택자](#7-css-기초-선택자)
- [8. 제어할 태그 선택하기](#8-제어할-태그-선택하기)
- [9. 조건문 예고](#9-조건문-예고)
- [10. 중복의 제거를 위한 리팩토링](#10-중복의-제거를-위한-리팩토링)

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

## 3-1. 숫자

html 콘솔창에서 숫자를 표현하면
```
alert(1+1)
```
를 입력했을 때 2가 출력된다. 

* 숫자를 의미하는 Number라는 데이터 타입에서 아주 중요한 것은 **연산**이다.
* **더하기(+)** 는 왼쪽에 있는 값과 오른쪽에 있는 값을 더해서 하나의 값을 만든다는 점에서 **이항 연산자**라고 부르고, 이항 연산자 중 산수를 하는 것이기 때문에 **산술 연산자**라고 부른다.
* 더하기 외에도 **빼기(-)** 와 **곱하기**, **나누기** 등이 있다.

```
1+1
2-1
2*4
6/2
```

## 3-2. 문자열
* 문자열은 **따옴표(" " 혹은 ' ')** 로 이루어져 있다.
* 문자열을 처리할 때 이용할 수 있는 명령은 다양하게 있는데 예를 들어 `.length`는 문자열의 길이를 반환한다.
  
### `.length`
  
```
str.length
```
* 이러한 `.length`와 같은 것들을 **프로퍼티(Properties)** 라고 한다.
* 또한, `.toUpperCase()`같은 것도 있다. 이는 결과를 대문자로 출력한다.
  
### `.toUpperCase()`

```javascript
'Hello World'.toUpperCase()
```

### `.index0f()`
* 찾고자 하는 값을 찾아 가장 처음으로 찾은 인덱스를 반환한다.
  
```javascript
'Hello world'.index0f('O')
```

### `.trim()`
* 문자열에서 공백을 제거한다.
  
```javascript
'        hello        '
'        hello        '.trim()
```

# 4. 변수와 대입 연산자

* 변수는 바뀔 수 있는 값으로 콘솔에 x=1이고 y=1을 입력했을 때, x+y를 실행하면 결과가 2로 출력된다.

```javascript
x = 1;
y = 1;
x + y;

x = 1000;
x + y;
```
  
* 여기서 x라는 것을 **변수(variable)** 라고 하고 =는 **대입 연산자**라고 한다. 
* 그런데, `1=2;`를 입력하면 에러가 발생한다. 1=2는 1에 2를 대입한다는 것인데, 1은 변하지 않는 값이기 때문이다.
* x라는 것은 대입 연산자를 통해 값이 바뀔 수 있다는 뜻에서 변수이고, 숫자 1은 언제나 1이기 때문에 바뀌지 않는다는 점에서 상수(constant)라고 한다.

```javascript
1 = 2;
```

* **변수를 사용할 때는 반드시 `var`라는 키워드를 변수 앞에 써주는 것이 좋다.**

```javascript
var name = 'leezche';
```

아래 내용은 기존 내용을 복습
---

# 5. CSS 기초: style 속성
* 특정 태그를 CSS언어로 디자인하고 싶다면, style이라는 속성을 쓰고 그 안에 CSS의 속성이라는 문법을 사용하면 된다.

```html
<h2 style="background-color: coral; color: powderblue;">JavaScript란 무엇인가?</h2>
```

# 6. CSS 기초: `<style>` 태그
* `<span>`을 통해 줄바꿈하지 않고 스타일을 지정
* `<style>`를 통해 원하는 태그 혹은 클래스, 아이디 선택자를 디자인할 수 있음

# 7. CSS 기초: 선택자
* `<style>`태그 내에서 원하는 것을 꾸미기 위해 사용하는 것을 선택자라고 하며, class를 선택할 때는 앞에 `.`를, id를 선택할 때는 `#`를 앞에 넣어 사용한다.
* 클래스는 무언가를 그루핑한다는 것이고 아이디는 하나의 대상을 식별한다는 것이 핵심.
* 따라서 아이디 선택자는 중복되지 않는다.

# 8. 제어할 태그 선택하기
* `<body>`태그를 선택하고자 할 때, javascript를 통해 프로그래밍적으로 상호작용에 의해 넣을 수 있다.

```javascript
document.querySelector('body');
```

* 선택자는 웹 페이지에 있는 모든 태그 중에서 원하는 것을 선택할 수 있다. 클래스 및 아이디를 포함하여 선택할 수 있으며, 이때 각 유형에 따라 `.` 혹은 `#`를 통해 구분하여 선택할 수 있다.
* 선택한 후 `<body>`태그에 스타일 속성을 집어넣을 수 있는데

```javascript
document.querySelector('body').style.
```
  
다음과 같이 작성한다.
  
* 여기서 예를 들어 style 속성 값 중 배경을 바꾸고자 한다면 또 다음과 같이 작성할 수 있다.
  
```javascript
document.querySelector('body').style.backgroundColor = 'black';
```

# 9. 조건문 예고
* 조건문이라고 하는 것은 하나의 프로그램이 하나의 흐름으로 가는 것이 아니라 조건에 따라 다른 순서의 기능들이 실행되게 하는 것이다.
* 본 교재의 예제에서 night 버튼과 day 버튼이 있는데, 사용자가 상태를 보고 night인지 day인지 선택하는 것보다 야간모드일 때 클릭할 때 누르면 주간모드가, 주간모드일 때 클릭하면 야간모드가 되는 기능을 구현하는 편이 더 사용자 편의에 좋을 것 같다.
* 이러한 것을 **토글(toggle)** 이라고 한다.
* 이때, 이 토글을 구현하기 위해 각 조건에 따라 분기하는 것이 중요하며, 이 분기를 조건문을 통해 적용할 수 있다.

```html
<input id="night_day" type="button" value="night" onclick="
    if(document.querySelector('#night_day').value === 'night') {
        document.querySelector('body').style.backgroundColor = 'black';
        document.querySelector('body').style.color = 'white';
        document.querySelector('#night_day').value = 'day';
    } else {
        document.querySelector('body').style.backgroundColor = 'white';
        document.querySelector('body').style.color = 'black';
        document.querySelector('#night_day').value = 'night';
    }
">
```
* if라는 조건문에 따라 참일 때 if 하 코드가, 거짓일 때는 else 하 코드가 실행되는 것이다.
* if의 조건에 있는 `===`는 비교 연산자로 이 비교 연산자를 통해 **불리언(boolean)** 이 만들어졌다.

# 10. 중복의 제거를 위한 리팩토링

* 리팩토링이란 단어에서 팩토리(factory)는 '공장'이며, 리(re)는 '다시'라는 뜻이므로 공장으로 다시 보내 개선한다는 느낌이다.
* 코딩을 하고 났을 때, 코드의 가독성을 높이고, 유지보수를 편리하게 만들고, 중복된 코드를 줄이는 방향으로 코드를 개선하는 작업을 리팩토링이라고 한다.
* 앞선 `javascriptdocument.querySelector('#night_day')`와 같은 코드는 사실 자기 자신을 가리키고 있기 때문에, 이를 대신해 다른 코드가 사용되면 더욱 효율적일 것이다.
* 이때, 같은 이벤트 안에서 실행되는 코드에서는 현재 코드가 속해있는 태그를 가리키도록 약속돼 있는 특수한 키워드를 사용하는데 이것이 바로 `this` 키워드다.
* 이를 고려하여 이전 예제를 수정해보자면,

```html
<input type="button" value="night" onclick="
    if(this.value === 'night') {
        document.querySelector('body').style.backgroundColor = 'black';
        document.querySelector('body').style.color = 'white';
        document.querySelector('#night_day').value = 'day';
    } else {
        document.querySelector('body').style.backgroundColor = 'white';
        document.querySelector('body').style.color = 'black';
        this.value = 'night';
    }
">
```

* 또, 여기서 `document.querySelector('body')`도 중복되는데 이러한 것도 간결하게 표현하는 것이 클린 코드라고 할 수 있다.
* 예를 들어 이러한 경우 target이라는 변수를 생성하여 할당하는 방법도 있다.
  
```html
<input id="night_day" type="button" value="night" onclick="
    var target = document.querySelector('body');
    if(this.value === 'night') {
        target.style.backgroundColor = 'black';
        target.style.color = 'white';
        document.querySelector('#night_day').value = 'day';
    } else {
        target.style.backgroundColor = 'white';
        target.style.color = 'black';
        this.value = 'night';
    }
">
```

