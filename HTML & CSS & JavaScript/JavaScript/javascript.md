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
- [11. 반복문 예고](#11-반복문-예고)
- [12. 배열](#12-배열)
- [13. 반복문](#13-반복문)
- [14. 배열과 반복문](#14-배열과-반복문)
- [15. 배열과 반복문의 활용](#15-배열과-반복문의-활용)
- [16. 함수 예고](#16-함수-예고)
- [17. 함수](#17-함수)
- [18. 매개변수와 인자](#18-매개변수와-인자)
- [19. 함수(return 문)](#19-함수return-문)
- [20. 함수의 활용](#20-함수의-활용)
- [21. 객체 예고](#21-객체-예고)
- [22. 객체 쓰기와 읽기](#22-객체-쓰기와-읽기)
- [23. 객체와 반복문](#23-객체와-반복문)

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

# 11. 반복문 예고

* 설정한 링크 태그의 style 값을 각각 설정하였을 때, 그 횟수가 적다면 수정하기에 부담스럽지 않지만, 그것이 1억 개라면 1억 번의 반복적인 작업을 수행해야 한다.
* 따라서 이를 해결하기 위해 반복을 통해 내용을 수정하는 것이 더욱 효율적이다.

```javascript
var alist = document.querySelectorAll('a');
var i = 0;
while(i < alist.length) {
    alist[i].style.color = 'powderblue';
    console.log(alist[i]);
    i = i + 1;
}
```

# 12. 배열
* 데이터 중에서 서로 연관된 데이터를 잘 정리 정돈해서 담아두는 일종의 수납 상자를 **배열(array)** 라고 생각하면 된다.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <h1>Array</h1>
        <h2>Syntax</h2>
        <script>
            var coworkers = ["egoing", "leezche"];
        </script>
    </body>
</html>
```

* 배열에 들어있는 항목을 가져올 때는 변수에 []를 입력하여 가져올 수 있다.
* 본 코드를 예로 들자면 coworkers[0]라고 쓸 수 있다.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <h1>Array</h1>
        <h2>Syntax</h2>
        <script>
            var coworkers = ["egoing", "leezche"];
        </script>

        <h2>get</h2>
        <script>
            document.write(coworkers[0]);
            document.write(coworkers[1]);
        </script>
    </body>
</html>
```

* 배열 안에 몇 개의 값이 있는지도 javascript 코드를 통해 확인할 수 있다.

```html
<script>
    document.write(coworkers.length);
</script>
```
* data를 추가하고 싶을 때는 `.push(value)`를 추가한다.

```html
<script>
    coworkers.push('duru');
    coworkers.push('taeho');
</script>
```

# 13. 반복문

* 반복문(루프)
* 여러 코드를 최소한의 코드로 나타내기 위해 반복문을 사용할 수 있다.
* 반복문은 조건이 True일 때, 코드가 실행되고 false일 때 반복이 종료되어 while문 바깥쪽에 있는 코드가 실행된다.
* 즉, 반복문이라는 것은 순서대로 실행되는 프로그램의 흐름을 제어하는 제어문이라고 할 수 있다.
* 반복문은 언제 종료될 것인가를 잘 지정하는 것이 중요하다. 그러기 위해서는 두 줄의 코드가 몇 번 실행되는지 어딘가에 적어둘 필요가 있다. 이를 위해서 **변수**가 필요하다.
* i=i+1은 '기존의 i의 값에 1을 더한 결과를 i의 새로운 값으로 준다'라는 뜻이다.

```html
<script>
    document.write('<li>1</li>');
    var i = 0;
    while(i < 3) {
        document.write('<li>2</li>');
        document.write('<li>3</li>');
        i = i + 1;
    }
    document.write('<li>4</li>');
</script>
```

# 14. 배열과 반복문

예를 들어 아래와 같은 코드가 있다고 할 때,

```html
<ul>
    <li>egoing</li>
    <li>leezche</li>
    <li>duru</li>
    <li>taeho</li>
</ul>
```
혹은 `<li>` 태그 대신 목록이 아주 복잡한 태그이고 이것에 대한 수정이 빈번하게 일어난다면 글 목록을 작성하는 것이 쉽지 않을 것이다. 이처럼 서로 연관된 데이터를 담는 방법 중 배열이 있는데, 이 배열에 담긴 데이터를 순차적으로 꺼내 `<li>`라는 태그를 만들어 문제를 해결할 수 있다.

```html
<body>
    <h1>Loop & Array</h1>
    <script>
        var coworkers = ['egoing', 'leezche', 'duru', 'taeho'];
    </script>
    <h2>Co workers</h2>
    <ul>
        <script>
            var i = 0;
            while(i < coworkers.length) {
                document.write('<li>' + coworkers[i] + '</li>');
                i = i + 1;
            }
        </script>
    </ul>
</body>
```

하지만 위와 같은 방법은 데이터가 바뀌어도 유연하게 작동하지 않는다. 따라서 `i < 4`가 아니라 coworkers의 배열에 담긴 원소의 개수로 설정하면 직접 개수를 입력하지 않더라도 적절히 실행될 것이다.

# 15. 배열과 반복문의 활용

* 리스트를 변수에 넣어 반복문을 통해 조건을 수행할 수 있다.

```html
<input id="night_day" type="button" value="night" onclick="
            var target = document.querySelector('body');
            if(this.value === 'night') {
                target.style.backgroundColor = 'black';
                target.style.color = 'white';
                this.value = 'day';

                var alist = document.querySelectorAll('a');
                var i = 0;
                while(i < alist.length) {
                    alist[i].style.color = 'powderblue';
                    console.log(alist[i]);
                    i = i + 1;
                }

            } else {
                target.style.backgroundColor = 'white';
                target.style.color = 'black';
                this.value = 'night';

                var alist = document.querySelectorAll('a');
                var i = 0;
                while(i < alist.length) {
                    alist[i].style.color = 'blue';
                    console.log(alist[i]);
                    i = i + 1;
                }
            }
">
```

# 16. 함수 예고

* 코드가 많아지면 그 코드를 잘 정돈하기 위한 도구가 필요하다. 그때 사용할 수 있는 도구가 **함수**이고, 그것보다 더 큰 도구는 **객체(추후 살펴 볼 예정)** 이다.

* 위 상황에서도 `<input>`태그가 반복되게 된다면 이를 해결하기 위해 많은 리소스가 소모된다. 따라서, 이를 해결하기 위한 방법이 필요하다.

```html
<head>
    <title>WEB1 - JavaScript</title>
    <meta charset="utf-8">
    <script>
        function nightDayHandler(self) {
            var target = document.querySelector('body');
            if(this.value === 'night') {
                target.style.backgroundColor = 'black';
                target.style.color = 'white';
                this.value = 'day';

                var alist = document.querySelectorAll('a');
                var i = 0;
                while(i < alist.length) {
                    alist[i].style.color = 'powderblue';
                    console.log(alist[i]);
                    i = i + 1;
                }

            } else {
                target.style.backgroundColor = 'white';
                target.style.color = 'black';
                this.value = 'night';

                var alist = document.querySelectorAll('a');
                var i = 0;
                while(i < alist.length) {
                    alist[i].style.color = 'blue';
                    console.log(alist[i]);
                    i = i + 1;
                }
            }
        }
    </script>
</head>

... 생략 ...

<input id="night_day" type="button" value="night" onclick="
            nightDayHandler(this);
">

... 생략 ...

<input id="night_day" type="button" value="night" onclick="
    nightDayHandler(this);
">

```

# 17. 함수

* 반복문을 쓰고자 한들 반복문을 쓸 수 없는 경우가 있다. 연속적으로 반복되는 것이 아니라 연속되지 않게 반복된다면 반복문을 사용하는 것이 어렵거나 불가능해진다.
* 이럴 때, 반복되는 코드를 함수로 작성한다.

```html
<script>
    function two() {
        document.write('<li>2-1</li>');
        document.write('<li>2-2</li>');
    }
    document.write('<li>1</li>');
    two();
    document.write('<li>3</li>');
    two();
</script>
```

* 함수 function을 정의한 후 함수를 실행하면 *중괄호에 있는 함수 내용이 실행된다. 이것이 기본적인 함수의 문법이다.

# 18. 매개변수와 인자

* 자판기를 사용할 때, 언제나 똑같은 제품을 받을 수 있는 자판기도 있지만, 원하는 제품을 선택하면 그 제품에 해당하는 제품을 제공하는 자판기가 더 효용이 있을 것이다.
* 이때, 제품을 선택하는 것을 입력이라 할 수 있고, 자판기가 그 입력에 대해 해당하는 제품을 제공하는 것은 출력이라 할 수 있다.
* 이 입력에 해당하는 것을 **매개변수(parameter)** 또는 **인자(argument)** 라고한다.
* 출력에 해당하는 것은 **return**과 관련있다.

```html
<script>
function onePlusOne() {
    document.write(1+1+'<br>');
}
onePlusOne();
</script>
```

이렇게 함수를 정의할 수도 있지만,

```html
<script>
function sum(left, right) {
    document.write(left + right + '<br>');
}
sum(2, 3);
sum(3, 4);
```

* 위처럼 `left`, `right`같은 변수를 매개하는 **매개변수(parameter)** 를 설정하여 유연하게 함수를 사용할 수 있다.
* 이후 함수에 직접 값을 삽입하여 함수를 실행할 수 있는데, 이 입력하는 값을 **인자(argument)** 라고 한다.

# 19. 함수(return 문)

* 이번에 배울 출력은 **return**이라는 것과 관련이 있다.
* 그럼 return을 배우기 전에 **표현식(expression)** 이라는 것이 무엇인지 확인하겠다.
* 내가 함수를 사용해 정보를 출력하는 데에 있어 줄바꿈을 포함한 채 출력하거나 하는 등의 과정을 표현할 수 있는데, 더욱 다양하게 사용하기 위해서 값을 반환하는 return을 사용할 수 있다.

```html
<script>
    function sum2(left, right) {
        return left + right;
    }
    document.write(sum2(2, 3) + '<br>');
    document.write('<div style="color: red;">' + sum2(2, 3) + '</div><br>');
    document.write('<div style="font-size: 3rem">' + sum2(2, 3) + '</div><br>')
</script>
```
계산한 값을 리턴하므로 원자화된 기능을 다양한 맥락에서 사용할 수 있는 자유가 생기게 된다. return을 통해 출력함으로써 다양한 용도로 함수를 활용할 수 있게 된다.

# 20. 함수의 활용

* 앞서 사용한 `nightDayHandler()` 함수를 정의하고 `<input>` 태그를 재작성 했을 때,

```html
... 생략 ...

<head>
    <title>WEB1 - JavaScript</title>
    <meta charset="utf-8">
    <script>
        function nightDayHandler() {
            var target = document.querySelector('body');
            if(this.value === 'night') {
                target.style.backgroundColor = 'black';
                target.style.color = 'white';
                this.value = 'day';

                var alist = document.querySelectorAll('a');
                var i = 0;
                while(i < alist.length) {
                    alist[i].style.color = 'powderblue';
                    console.log(alist[i]);
                    i = i + 1;
                }

            } else {
                target.style.backgroundColor = 'white';
                target.style.color = 'black';
                this.value = 'night';

                var alist = document.querySelectorAll('a');
                var i = 0;
                while(i < alist.length) {
                    alist[i].style.color = 'blue';
                    console.log(alist[i]);
                    i = i + 1;
                }
            }
        }
    </script>
</head>

... 생략 ...

<input type="button" value="night" onclick="
    nightDayHandler();
">

... 생략 ...

<input type="button" value="night" onclick="
    nightDayHandler();
">
```

* 이렇게 했을 때 버튼을 두 번 클릭했을 때부터 변화가 생기며, input 버튼의 값이 night에서 day로 레이블이 바뀌지 않는다.
* onclick 이벤트 안에서 this는 이 이벤트가 소속된 태그를 가리키도록 되어 있는데, 독립된 `nightDayHandler()` 안의 코드에서 this라는 값은 더 이상 input 버튼이 아니고, 전역 객체를 갖게 된다.
* 그래서 함수 안에서 this 값이 input 버튼을 가리키도록 `nightDayHandler()`이 실행될 때 this 값을 준다.

```html
... 생략 ...

<head>
    <title>WEB1 - JavaScript</title>
    <meta charset="utf-8">
    <script>
        function nightDayHandler(self) {        // self 매개변수 추가
            var target = document.querySelector('body');
            if(self.value === 'night') {        // this -> self로 변경
                target.style.backgroundColor = 'black';
                target.style.color = 'white';
                self.value = 'day';             // this -> self로 변경

                var alist = document.querySelectorAll('a');
                var i = 0;
                while(i < alist.length) {
                    alist[i].style.color = 'powderblue';
                    console.log(alist[i]);
                    i = i + 1;
                }

            } else {
                target.style.backgroundColor = 'white';
                target.style.color = 'black';
                self.value = 'night';           // this -> self로 변경

                var alist = document.querySelectorAll('a');
                var i = 0;
                while(i < alist.length) {
                    alist[i].style.color = 'blue';
                    console.log(alist[i]);
                    i = i + 1;
                }
            }
        }
    </script>
</head>

... 생략 ...

<input type="button" value="night" onclick="
    nightDayHandler(this); // this 인자 추가
">

... 생략 ...

<input type="button" value="night" onclick="
    nightDayHandler(this); // this 인자 추가
">
```

# 21. 객체 예고

* 프로그래밍을 하다 보면 코드가 많아지고, 코드가 많아지면 잘 정리 정돈하기 위해 함수라는 것을 쓴다. 그리고 함수뿐만 아니라 연관돼 있는 변수가 엄청나게 많아지면 역시나 똑같이 복잡도의 한계에 도달하게 된다. 바로 그러한 상황에서 서로 연관된 함수와 변수를 같은 이름으로 그루핑해서 잘 정리 정돈하기 위한 도구가 바로 **객체**이다.

```html
<script>
    function LinksSetColor(color) {
        var alist = document.querySelectorAll('a');
        var i = 0;
        while(i < alist.length) {
            alist[i].style.color = color;
            console.log(alist[i]);
            i = i + 1;
        }
    }
    function BodySetColor(color) {
        document.querySelector('body').style.color = color;
    }
    function BodySetBackgroundColor(color) {
        document.querySelector('body').style.backgroundColor = color;
    }
    function nightDayHandler(self) {
        var target = document.querySelector('body');
        if(self.value === 'night') {
            BodySetBackgroundColor('black');
            BodySetColor('white');
            self.value = 'day';

            LinksSetColor('powderblue');
        } else {
            BodySetBackgroundColor('white');
            BodySetColor('black');
            self.value = 'night';

            LinksSetColor('blue');
        }
    }
</script>
```
이전 코드를 위 코드로 변경함으로써 함수를 더 명확하고 간결하게 이해할 수 있다.

* 그런데 이름을 바꾸는 것 외에도 서로 연관된 함수와 변수를 그루핑해서 사용할 수 있도록 객체를 사용할 수도 있다. 

예를 들어 Body와 Links 라는 객체가 있다면, 다음과 같이 작성할 수도 있다.

```html
<!-- 실제로 동작하기 않는 코드 -->
<script>
    
    ... 생략 ...

    function nightDayHandler(self) {
        var target = document.querySelector('body');
        if(self.value === 'night') {
            Body.setBackgroundColor('black');
            Body.setColor('white');
            self.value = 'day';

            Links.setColor('powderblue');
        } else {
            Body.setBackgroundColor('white');
            Body.setColor('black');
            self.value = 'night';

            Links.setColor('blue');
        }
    }
</script>
```

* 단순히 함수의 이름 자체를 바꾸는 것보다 간결하게 그루핑할 수 있기 때문에 정리정돈이 더 깔끔한 것을 볼 수 있다.
* 또한 `document`의 경우에도 역시 객체임을 알 수 있다. 즉, `querySelector()`라는 것이 `document`라는 객체에 속한 함수임을 알 수 있다.
* 그리고 객체에 속한 함수는 함수라 하지 않고 **메서드**라고 부른다.

# 22. 객체 쓰기와 읽기

* 앞서 배열은 정보를 담는 그릇이면서 동시에 정보가 순서대로 저장된다는 특징을 지니고 있다.
* 이에 반해 순서 없이 저장할 수 있는 정보가 있는데 그것이 바로 **객체**이다.
* 하지만 데이터를 무작위로 집어넣는 것이 아니라 어떤 물건을 수납 상자에 집어 넣으면서 그 물건이나 사물에 대한 이름을 함께 넣어야 그 이름으로 물건을 꺼낼 수 있게 된다.

```html
<script>
    var coworkers = {
        
    }
</script>
```

이 상태에서 coworkers 변수에 객체를 담을 건데, 객체를 만들 때 사용하는 기호를 **객체 리터럴(object literal)** 이라고 한다. 그리고 객체는 중괄호를 사용한다.

```html
<script>
    var coworkers = {
        "programmer":"egoing",
        "designer":"leezche"
    }
</script>
```

이후 정보를 꺼낼 때는

```html
<script>
    var coworkers = {
        "programmer":"egoing",
        "designer":"leezche"
    }
    document.write("programmer : " + coworkers.programmer + "<br>");
    document.write("designer : " + coworkers.designer + "<br>")
</script>
```

이와 같이 뽑아낼 수 있다. 즉, coworkers 다음에 있는 점(.)은 **객체 접근 연산자(object access operator)** 라고 한다. 객체에 접근하는 연산자인 것이다.

* 객체에 정보를 추가하는 방법 또한, 어렵지 않다.

```html
<script>
    var coworkers = {
        "programmer":"egoing",
        "designer":"leezche"
    }
    document.write("programmer : " + coworkers.programmer + "<br>");
    document.write("designer : " + coworkers.designer + "<br>");
    coworkers.bookkeeper = "duru";
    document.write("bookkeeper : " + coworkers.bookkeeper + "<br>");
</script>
```

그런데, data scientist라는 이름을 넣고자 할 때 문법적으로 오류가 발생할 수 있다. 이것은 점(.)으로 할 수 없고 대괄호를 써서 문자열 형태로 넣으면 똑같은 효과를 가져올 수 있다.

```html
<script>
    
    ... 생략 ...

    coworkers["data scientist"] = "taeho";
    document.write("data scientist : " + coworkers["data scientist"] + "<br>");
</script>
```

# 23. 객체와 반복문