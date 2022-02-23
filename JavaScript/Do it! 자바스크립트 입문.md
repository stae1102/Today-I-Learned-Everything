- [Chapter 2. 자바스크립트와 친해지기](#chapter-2-자바스크립트와-친해지기)
  - [2-3. 외부 스크립트 파일 연결하기](#2-3-외부-스크립트-파일-연결하기)
  - [2-4. 나의 첫번째 자바스크립트 프로그램](#2-4-나의-첫번째-자바스크립트-프로그램)
    - [인사하는 브라우저 만들기](#인사하는-브라우저-만들기)
    - [자바스크립트 프로그램의 실행](#자바스크립트-프로그램의-실행)
  - [2-5. 자바스크립트의 입력과 출력](#2-5-자바스크립트의-입력과-출력)
    - [사용자 입력값 받기 - prompt() 함수](#사용자-입력값-받기---prompt-함수)
    - [알림창으로 출력하기 - alert() 함수](#알림창으로-출력하기---alert-함수)
    - [웹 브라우저 화면에 출력하기 - document.write() 함수](#웹-브라우저-화면에-출력하기---documentwrite-함수)
    - [콘솔에 출력하기 - console.log() 함수](#콘솔에-출력하기---consolelog-함수)
    - [크롬 브라우저 콘솔로 오류 찾아내기](#크롬-브라우저-콘솔로-오류-찾아내기)
  - [2-6. 자바스크립트 소스를 작성할 때 지켜야 할 규칙](#2-6-자바스크립트-소스를-작성할-때-지켜야-할-규칙)
    - [규칙 1 - 대소문자를 구별하여 소스를 작성한다.](#규칙-1---대소문자를-구별하여-소스를-작성한다)
    - [규칙 2 - 읽기 쉽게 들여 쓰는 습관을 들인다.](#규칙-2---읽기-쉽게-들여-쓰는-습관을-들인다)
    - [규칙 3 - 세미콜론으로 문장을 구분한다.](#규칙-3---세미콜론으로-문장을-구분한다)
    - [규칙 4 - 자바스크립트 소스에 메모를 하려면 주석을 사용한다.](#규칙-4---자바스크립트-소스에-메모를-하려면-주석을-사용한다)
    - [규칙 5 - 식별자는 정해진 규칙을 지켜 작성한다.](#규칙-5---식별자는-정해진-규칙을-지켜-작성한다)
    - [규칙 6 - 예약어는 식별자로 사용할 수 없다.](#규칙-6---예약어는-식별자로-사용할-수-없다)
- [Chapter 3. 변수와 자료형 그리고 연산자](#chapter-3-변수와-자료형-그리고-연산자)

# Chapter 2. 자바스크립트와 친해지기

## 2-3. 외부 스크립트 파일 연결하기

* 일괄적으로 js파일을 수정하기 위해 HTML 내부에 작성하는 것이 아니라 외부 파일에 연결하여 효율적으로 스크립트를 적용할 수 있습니다.

```html
<body>
    ... 생략 ...
    <script src="js/*.js"></script>
</body>
```

## 2-4. 나의 첫번째 자바스크립트 프로그램

### 인사하는 브라우저 만들기

* 브라우저를 열었을 때, 이름을 입력하면 환영해주는 페이지를 만들어보고자 합니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<title>Welcome</title>
	<style>
		body {
			font-size:1.3em;
			text-align: center;
		}
	</style>
</head>
<body>
	<h1>어서오세요</h1>
</body>
</html>
```

이때, `<script>`태그를 통해 사용할 수 있습니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<title>Welcome</title>
	<style>
		body {
			font-size:1.3em;
			text-align: center;
		}
	</style>
</head>
<body>
	<h1>어서오세요</h1>
	<script>
		var name = prompt("이름을 입력하세요.");
		document.write("<b><big>" + name + "</big></b>님, 환영합니다.");
	</script>
</body>
</html>
```

### 자바스크립트 프로그램의 실행

* 웹 브라우저에는 HTML 분석기(HTML Parser), CSS 분석기(CSS Parser), 자바스크립트 해석기(Javascript Interpreter)가 포함되어 있습니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
	<meta ...>
	<meta ...>
	<meta ...>
	<title>Welcome</title>
	<style>
		...
	</style>
</head>
<body>
	<h1>어서오세요</h1>
	<script>
		...
	</script>
</body>
</html>
```

1. 1번 줄의 `<!DOCTYPE html>`은 HTML 문서의 시작을 알리는 HTML 태그입니다. 브라우저가 이 태그를 보고 이 소스가 HTML임을 알게 됩니다.
2. HTML 분석기는 주로 HTML태그의 순서와 포함 관계를 확인합니다. 즉, HTML 분석기를 통해 `<head>` 태그 안에는 3 개의 `<meta>`태그와 `<title>`, `<style>`태그가 있고 `<body>`태그 안에는 `<h1>`, `<script>` 태그가 있다는 것을 알게 됩니다.
3. CSS 분석기는 HTML 분석기가 태그 분석을 끝낸 다음 `<style>`태그 사이의 스타일 정보를 분석합니다
4. 마지막으로 자바스크립트 해석기가 `<script>`태그 사이의 자바스크립트 소스를 해석합니다

## 2-5. 자바스크립트의 입력과 출력

### 사용자 입력값 받기 - prompt() 함수

* 사용자에게 어떤 값을 입력받을 때 사용하는 prompt() 함수에 대해서 알아보겠습니다.
* prompt() 함수를 실행하면 사용자가 값을 입력할 수 있도록 작은 창을 만들어줍니다.

```js
prompt();
```

* 브라우저에서 값을 입력하면 콘솔 창에서 입력한 값을 확인할 수 있습니다.
* 또한, prompt() 함수를 사용할 때 소괄호 안에 큰 따옴표나 작은 따옴표로 원하는 문장을 감싸 넣으면 프롬프트 창에 문장을 표시할 수도 있습니다.

```js
prompt("이름을 입력하세요.");
```

* 텍스트 필드 안에 기본값을 표시할 수도 있습니다.

```js
prompt("이름을 입력하세요.", "철수");
```

### 알림창으로 출력하기 - alert() 함수

* 웹 브라우저 화면에서 간단한 알림 내용을 표시하려고 할 때 alert() 함수를 사용합니다.

```js
alert("환영합니다.");
```

### 웹 브라우저 화면에 출력하기 - document.write() 함수

* 자바스크립트로 document.write() 함수를 통해 웹 브라우저에 출력할 수 있습니다.

* document.write() 함수는 prompt() 함수와 달리 document.가 함수 이름 앞에 붙어 있는데, 그 이유는 write() 함수가 document 객체에 포함되어 있기 때문입니다.

### 콘솔에 출력하기 - console.log() 함수

* console.log() 함수는 괄호 안의 내용을 콘솔 창에 출력합니다.

```js
var name = prompt("이름: ");
console.log(name + "님, 어서오세요!")
```

### 크롬 브라우저 콘솔로 오류 찾아내기

* 때로는 작성한 자바스크립트 소스가 원하는 대로 실행되지 않거나 아예 실행되지 않는 경우가 있습니다. 이럴 때, 웹 브라우저의 콘솔을 통해 오류를 확인할 수 있습니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<title>What time is it?</title>
	<style>
		body {
			font-size:2em;
			text-align: center;
		}
	</style>
</head>
<body>
	<script>
		var now = new Date();
		var display = now.toLocaleTimeString();
		document.writ("현재 시각은 " + display);	
	</script>
</body>
</html>
```

```
Uncaught TypeError: document.writ is not a function
    at js-time.html:19:12
```

## 2-6. 자바스크립트 소스를 작성할 때 지켜야 할 규칙

### 규칙 1 - 대소문자를 구별하여 소스를 작성한다.

* 자바 스크립트는 대소문자를 구별합니다. 즉 sum, Sum, SUM을 모두 다르게 인식합니다.

### 규칙 2 - 읽기 쉽게 들여 쓰는 습관을 들인다.

* 자바스크립트 해석기는 소스를 처리할 때 들여쓰기를 신경 쓰지 않습니다. 하지만, 내가 쓴 소스를 다른 프로그래머가 읽거나 오류가 발생해 소스를 수정해야 할 수도 있습니다.

### 규칙 3 - 세미콜론으로 문장을 구분한다.

* 자바스크립트에서 세미콜론(;)은 문장 끝을 나타냅니다. 하지만 자바스크립트 문장 끝에 세미콜론을 붙이지 않아도 잘 실행됩니다.

* 하지만, 실수로 줄 바꿈을 하지 않는다면 오류가 발생합니다. 이를 방지하기 위해 자바스크립트 문장의 끝에는 세미콜론을 붙이는 것이 좋습니다.

### 규칙 4 - 자바스크립트 소스에 메모를 하려면 주석을 사용한다.

* 내가 작성한 자바스크립트 소스를 다른 사람에게 설명하고 싶거나, 나중을 위해 안내 표시를 하고 싶다면 주석을 사용하면 됩니다.

> 한 줄 주석
> ```js
> var today = new Date();     // 날짜를 가져온다.
> var h = today.getHours();   // 시를 추출한다.
> ```

> 여러 줄 주석
> ```js
> /*
>   현재 날짜를 가져와
>   시와 분, 초로 추출하고
>   화면에 표시하는 스크립트
> */
> function startTime() { ... }
> ```

### 규칙 5 - 식별자는 정해진 규칙을 지켜 작성한다.

* 식별자는 앞으로 내가 공부할 자바스크립트 문법의 핵심 요소인 변수, 함수, 속성 등을 구별하기 위해 내가 이름 붙여 준 특정 단어를 의미합니다.

```js
var name = prompt("이름을 입력하세요.");
```

* 식별자의 첫 글자는 반드시 영문자나 밑줄(\_), 또는 달러 기호($)로 시작해야 하고, 그 뒤에 영문자나 밑줄, 달러 기호, 숫자를 사용할 수 있습니다. 두 단어 이상이 모여 하나의 식별자를 만들 경우 단어 사이에 공백을 둘 수 없고, 단어와 단어 사이를 하이픈(-)이나 밑줄(\_)로 연결해서 사용합니다.
* 하이픈이나 밑줄 없이 두 단어를 그대로 붙여서 사용하기도 하는데, 그럴 경우 첫 번째 단어는 소문자로 시작하고 두 번째 단어는 대문자로 시작하는 것이 일반적입니다.

```js
num1            // 영문자로 시작하는 식별자
_doSomething    // 밑줄(_)로 시작하는 식별자
checkTime()     // 두 단어로 만든 식별자
```

### 규칙 6 - 예약어는 식별자로 사용할 수 없다.

* 예약어(Keyword)는 자바스크립트에 먼저 등록된 요소를 가리킵니다. 즉, 예약어는 식별자로 사용할 수 없습니다. 예를 들어 변수를 선언할 때 사용하는 var 예약어는 식별자로 사용하면 오류가 발생합니다.

# Chapter 3. 변수와 자료형 그리고 연산자