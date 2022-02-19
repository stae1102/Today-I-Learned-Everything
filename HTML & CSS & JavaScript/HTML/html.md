# HTML의 정의

* HyperText Markup Language로 단어 그 자체로 하나의 언어로서 프로그래밍을 위해 사용되며, 특히 웹 페이지 및 웹 사이트를 구성하는 것이다.

# 제목

* 웹 페이지의 제목을 나타내기 위해서 단순히 글씨의 크기만을 키울 수 있지만, 따로 제목으로 설정할 수 있는 방법이 있다.

```html
<h1>제목</h1>
```

* 이때, <와 >로 구성된 것을 태그라고 하며 이 태그가 html의 핵심이다.
* h1 ~ h6으로 숫자의 크기가 커질수록 크기 또한 줄어든다.
  
# 공백

* HTML 문서를 작성할 때, 공백은 두 칸 이상 처리하지 못하는 문제가 있다. 예를 들어,

```html
<h1>Hello, HTML</h1>
<h1>Hello,       HTML</h1>
<h1>
    Hello,  
    HTML
</h1>
```

* 위 세 가지 표현은 최종적으로 모두 같은 형태의 문장을 출력하게 된다. 

# 줄바꿈

* html에서 줄바꿈을 하기 위해서는 태그를 이용하여 줄바꿈을 명확히 표시해야 한다.
* 이때, 줄바꿈을 하는 태그는 `<br>`태그인데, 닫힘 태그가 없는 **빈 태그**이다.
* `<br>`을 반복하여 단락을 나누고자 할 때는 오히려 `<p>`를 통해 단락을 명확히 구분해주는 것이 더욱 중요하다.

> 예)
> ```html
> <p>Hypertext Markup Language (HTML) is the standard markup language for <strong>creating <u>web</u> pages</strong> and web applications. Web browsers receive HTML documents from a web server or from local storage and render them into multimedia web pages. HTML describes the structure of a web page semantically and originally included cues for the appearance of the document.</p>
> ```

# 이미지 삽입

```html
<img src="https://unsplash.com/photos/OqtafYT5kTw">
```

* 위와 같이 `<img>`태그를 사용하고, src(source)를 통해 값을 작성한다.

```html
<img src="https://unsplash.com/photos/OqtafYT5kTw" width="100%">
```
* 이미지를 불러오는 것 뿐만 아니라 화면의 %로 나타내거나 px로 지정할 수 있다.
* 이때, src와 width 등은 속성으로 순서에 자유롭게 사용가능하다.

# 부모 자식과 목록
* html에서는 태그 안에 태그를 두어 정보를 출력할 수 있는데, 바깥에 있는 상위 태그를 부모, 그 속에 있는 태그를 자식이라고 한다.

> 예)
> ```html
> <parent>
>     <child></child>
> </parent>
> ```

위와 같은 형태로 구성할 수 있다.(옳은 코드는 아님)

이때, 정보를 효율적으로 나타내는 리스트 또한 부모, 자식 태그로 구성되어 있다.
## Ordered list
> ol(Ordered list)의 예
> ```html
> <h1>심부름 목록</h1>
> <ol>
>     <li>대파</li>
>     <li>양상추</li>
> </ol>
> ```
> <h1>심부름 목록</h1>
> <ol>
>     <li>대파</li>
>     <li>양상추</li>
> </ol>

## Unordered list
> ul(Unordered list)의 예
> ```html
> <h1>To do list</h1>
> <ul>
>     <li>끝내주게 숨쉬기</li>
>     <li>간지나게 자기</li>
>     <li>작살나게 밥먹기<li>
> <ul>
> ```
> <h1>To do list</h1>
> <ul>
>     <li>끝내주게 숨쉬기</li>
>     <li>간지나게 자기</li>
>     <li>작살나게 밥먹기</li>
> <ul>

## Table
> Table(표)의 예
> ```html
> <table>
>     <tr>
>         <td>head</td>
>         <td>98.1%</td>
>     </tr>
>     <tr>
>         <td>body</td>
>         <td>97.9%</td>
>     </tr>
>     <tr>
>         <td>html</td>
>         <td>97.9%</td>
>     </tr>
> </table>
> ```
> <table>
>     <tr>
>         <td>head</td>
>         <td>98.1%</td>
>     </tr>
>     <tr>
>         <td>body</td>
>         <td>97.9%</td>
>     </tr>
>     <tr>
>         <td>html</td>
>         <td>97.9%</td>
>     </tr>
> </table>

# 기본적인 HTML의 구조