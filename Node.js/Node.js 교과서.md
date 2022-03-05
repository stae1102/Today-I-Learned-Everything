```
「Node.js 교과서」, 조현영, 길벗
을 참고하며
```

- [1장. 노드 시작하기](#1장-노드-시작하기)
  - [1.1 핵심 개념 이해하기](#11-핵심-개념-이해하기)
    - [1.1.1 서버](#111-서버)
    - [1.1.2 자바스크립트 런타임](#112-자바스크립트-런타임)
    - [1.1.3 이벤트 기반](#113-이벤트-기반)
    - [1.1.4 논 블로킹 I/O](#114-논-블로킹-io)
    - [1.1.5 싱글 스레드](#115-싱글-스레드)
  - [1.2 서버로서의 노드](#12-서버로서의-노드)
  - [1.3 서버 외의 노드](#13-서버-외의-노드)
- [2장. 알아두어야 할 자바스크립트](#2장-알아두어야-할-자바스크립트)
  - [2.1 ES2015+](#21-es2015)
    - [2.1.1 const, let](#211-const-let)
    - [2.1.2 템플릿 문자열](#212-템플릿-문자열)
    - [2.1.3 객체 리터럴](#213-객체-리터럴)
    - [2.1.4 화살표 함수](#214-화살표-함수)
    - [2.1.5 구조분해 할당](#215-구조분해-할당)
    - [2.1.6 클래스](#216-클래스)
    - [2.1.7 프로미스](#217-프로미스)
    - [2.1.8 async/await](#218-asyncawait)
  - [2.2 프런트엔드 자바스크립트](#22-프런트엔드-자바스크립트)
    - [2.2.1 AJAX](#221-ajax)
    - [2.2.2 FormData](#222-formdata)
    - [2.2.3 encodeURIComponent, decodeURIComponent](#223-encodeuricomponent-decodeuricomponent)
    - [2.2.4 데이터 속성과 dataset](#224-데이터-속성과-dataset)

# 1장. 노드 시작하기

런타임, 이벤트 기반, 논 블로킹 I/O, 싱글 스레드 모델 등 핵심 개념을 다룹니다.

## 1.1 핵심 개념 이해하기

### 1.1.1 서버

* 서버는 네트워크를 통해 클라이언트에 정보나 서비스를 제공하는 컴퓨터 또는 프로그램을 말합니다. 클라이언트란 요청을 보내는 주체로 브라우저일 수도 데스크톱 프로그램일 수도 있고, 모바일 앱일 수도 있고, 다른 서버에 요청을 보내는 서버일 수도 있습니다.
  
예를 들어 길벗출판사의 웹 사이트를 방문한다고 생각해봅시다. 주소창에 길벗출판사의 웹사이트 주소를 입력 **(요청)** 하면 브라우저는 그 주소에 해당하는 길벗출판사의 컴퓨터 위치를 파악합니다. 그리고 그 컴퓨터로부터 길벗출판사의 웹 사이트 페이지를 받아와서 요청자의 브라우저(클라이언트)에 띄웁니다 **(응답)**. 이런 일을 하는 컴퓨터가 바로 서버입니다.  
  
모바일 앱을 설치하는 경우를 생각해봅시다. 구글 플레이 스토어나 애플 앱스토어에서 원하는 앱을 고른 후 설치 버튼을 누르면 **(요청)** 내려받기 **(응답)** 가 시작됩니다. 앱 설치 파일은 이미 어딘가에 저장되어 있으므로 여러분이 그곳에서 데이터를 받아와 모바일 기기에 설치할 수 있는 것입니다. 플레이 스토어와 애플 스토어는 클라이언트 역할을 하는 것이고요.

* 데이터를 어딘가에 저장하고, 그 어딘가에 클라이언트로 데이터를 받아와야 합니다. 이곳이 바로 서버입니다.

* 서버는 다른 서버에도 요청을 보낼 수도 있는데 이때는 서버가 클라이언트 역할을 합니다.

* 노드는 자바스크립트 프로그램이 서버로서 기능하기 위한 도구를 제공하므로 서버 역할을 수행할 수 있습니다.

### 1.1.2 자바스크립트 런타임

* 노드는 자바스크립트 런타임입니다. 런타임은 **특정 언어로 만든 프로그램들을 실행할 수 있는 환경**을 뜻합니다. 따라서 노드는 자바스크립트 프로그램을 컴퓨터에서 실행할 수 있습니다. 

<table border="1">
    <tr>
        <td colspan = "2" align='center'>Node.js Core Library</td>
    </tr>
    <tr>
        <td colspan = "2" align='center'>Node.js Bindings</td>
    </tr>
    <tr>
        <td align='center'>V8</td>
        <td align='center'>libuv</td>
    </tr>
</table>

V8: 오픈 소스 자바스크립트 엔진  
libuv: 비동기 I/O

* 노드는 V8과 더불어 libuv 라이브러리를 사용합니다. libuv 라이브러리는 노드의 특성인 **이벤트 기반, 논 블로킹 I/O 모델**을 구현하고 있습니다.

### 1.1.3 이벤트 기반

* 이벤트 기반(event-driven)이란 이벤트가 발생할 때 미리 지정해둔 작업을 수행하는 방식을 의미합니다.

이벤트 기반 시스템에서는 특정 이벤트가 발생할 때 무엇을 할지 미리 등록해두어야 합니다. 이를 **이벤트 리스너(event listener)** 에 **콜백(callback)** 함수를 등록한다고 표현합니다. 

노드도 이벤트 기반 방식으로 동작하므로, 이벤트가 발생하면 이벤트 리스너에 등록해둔 콜백 함수를 호출합니다. 발생한 이벤트가 없거나 발생했던 이벤트를 다 처리하면, 노드는 다음 이벤트가 발생할 때까지 대기합니다.  
  
이벤트 기반 모델에서는 **이벤트 루프(event loop)** 라는 개념이 등장합니다. 여러 이벤트가 동시에 발생했을 때 어떤 순서로 콜백 함수를 호출할지를 이벤트 루프가 판단합니다.  

* 노드는 자바스크립트 코드의 맨 위부터 한 줄씩 실행합니다. 함수 호출 부분을 발견했다면 호출한 함수를 **호출 스택(call stack)** 에 넣습니다.

```js
function first() {
    second();
    console.log('첫 번째');
}
function second() {
    third();
    console.log('두 번째');
}
function third() {
    console.log('세 번째');
}
first();
```

위 과정에서 함수는 first 함수가 제일 먼저 호출되고, second 함수가 호출된 뒤, third 함수가 호출됩니다. 실행은 호출된 순서와 반대로 실행이 완료됩니다. 따라서 콘솔에는 '세 번째', '두 번째', '첫 번째' 순서로 찍히게 됩니다.  

third() -> second() -> first() -> anonymous 순서로 실행됩니다. anonymous 함수는 처음 실행 시의 **전역 컨텍스트(global context)** 를 의미합니다. 컨텍스트는 함수가 호출되었을 때 생성되는 환경을 의미합니다.  

다음 코드도 알아보겠습니다.

```js
function run() {
    console.log('3초 후 실행');
}
undefined
console.log('시작');
setTimeout(run, 3000);
console.log('끝');
```
결과는 다음과 같습니다.
```
시작
끝
3초 후 실행
```
이는 setTimeout 함수의 콜백인 run이 호출 스택에 언제 들어가는지 파악해야 합니다. 이를 파악하기 위해서는 이벤트 루프, 태스크 큐(task queue), 백그라운드(background)를 알아야 합니다.

* 이벤트 루프: 이벤트 발생 시 호출할 콜백 함수들을 관리하고, 호출된 콜백 함수의 실행 순서를 결정하는 역할을 담당합니다. 노드가 종료될 때까지 이벤트 처리를 위한 작업을 반복하므로 루프(loop)라고 합니다.

* 백그라운드: setTimeout 같은 타이머나 이벤트 리스너들이 대기하는 공간입니다. 자바스크립트가 아닌 다른 언어로 작성된 프로그램이라고 봐도 됩니다. 여러 작업이 동시에 실행될 수 있습니다.

* 태스크 큐: 이벤트 발생 후, 백그라운드에서는 태스크 큐로 타이머나 이벤트 리스너의 콜백 함수를 보냅니다. 정해진 순서대로 콜백들이 줄을 서 있으므로 콜백 큐라고도 부릅니다. 콜백들은 보통 완료된 순서대로 줄을 서 있지만 특정한 경우에는 순서가 바뀌기도 합니다.

먼저 전역 컨텍스트인 anonymous가 호출 스택에 들어갑니다. 그 뒤 setTimeout이 호출 스택에 들어갑니다.  

호출 스택에 들어간 순서와 반대로 실행되므로, setTimeout이 먼저 실행됩니다. setTimeout이 실행되면 타이머와 함께 run 콜백을 백그라운드로 보내고, setTimeout은 호출 스택에서 빠집니다. 그 다음으로 anonymous가 호출 스택에서 빠집니다. 백그라운드에서는 3초를 센 후 run 함수를 태스크 큐로 보냅니다. 3초를 세었다는 것은 백그라운드에 맡겨진 작업이 완료된 것으로 이해해도 됩니다.  

태스크 큐는 하나의 큐처럼 보이지만, 여러 개의 큐로 이루어져 있습니다. 이벤트 루프는 정해진 규칙에 따라 콜백 함수들을 호출 스택으로 부릅니다.  

이벤트 루프는 호출 스택이 비어 있으면 태스크 큐에서 함수를 하나씩 가져와 호출 스택에 넣고 실행합니다.  

이벤트 루프가 run 콜백을 태스크 큐에서 꺼내 호출 스택으로 올렸습니다. 호출 스택으로 올려진 run은 실행되고, 실행 완료 후 호출 스택에서 비워집니다. 이벤트 루프는 태스크 큐에 콜백 함수가 들어올 때까지 계속 대기합니다.  

만약 호출 스택에 함수들이 너무 많이 들어 있으면 3초가 지난 후에도 run 함수가 실행되지 않을 수 있습니다. 이벤트 루프는 호출 스택이 비어있을 때만 태스크 큐에서 있는 함수를 호출 스택으로 가져오기 때문입니다. 이때문에 setTimeout의 시간이 정확하지 않을 수도 있습니다.

### 1.1.4 논 블로킹 I/O

이벤트 루프를 잘 활용하면 오래 걸리는 작업을 효율적으로 처리할 수 있습니다. 작업에는 두 가지 종류가 있는데, **동시에 실행될 수 있는 작업**과 **동시에 실행될 수 없는 작업**입니다. 기본적으로 여러분이 작성한 자바스크립트 코드는 동시에 실행될 수 없습니다. 하지만 자바스크립트상에서 돌아가는 것이 아닌 I/O 작업 같은 것은 동시에 처리될 수 있습니다.  

I/O는 **입력(Input)/출력(Output)** 을 의미합니다. 파일 시스템 접근(파일 읽기, 파일 쓰기, 폴더 만들기 등)이나 네트워크를 통한 요청 같은 작업이 I/O의 일종입니다. 이러한 작업을 할 때 노드는 논 블로킹 방식으로 처리하는 방법을 제공합니다. **논 블로킹**이란 **이전 작업이 완료될 때까지 대기하지 않고 다음 작업을 수행함을 뜻합니다**. 반대로 **블로킹**은 이전 작업이 끝나야만 다음 작업을 수행하는 것을 의미합니다.  

* 노드는 I/O 작업을 백그라운드로 넘겨 동시에 처리하곤 합니다. 따라서 동시에 처리할 수 있는 작업들은 최대한 묶어서 백그라운드로 넘겨야 시간을 절약할 수 있습니다.

동시에 처리할 수 있는 I/O 작업이라도 논 블로킹 방식으로 코딩하지 않으면 의미가 퇴색되므로 논 블로킹 방식으로 코딩하는 습관을 들여야 합니다.  

다음은 블로킹 방식의 코드입니다.

```js
function longRunningTask() {
    // 오래 걸리는 작업
    console.log('작업 끝');
}

console.log('시작');
longRunningTask();
console.log('다음 작업');
```

이 함수가 블로킹 방식으로 I/O 작업을 한다고 할 때, longRunningTask를 완료하기 전까지 이어지는 작업이 호출되지 않습니다.  

이번에는 setTimeout을 사용해서 코드를 바꿔보겠습니다.

```js
function longRunningTask() {
    // 오래 걸리는 작업
    console.log('작업 끝');
}

console.log('시작');
setTimeout(longRunningTask, 0);
console.log('다음 작업');
```
결과는 '다음 작업'이 먼저 출력된 후 '작업 끝'이 출력됩니다.  

setTimeout(콜백, 0)은 코드를 논 블로킹으로 만들기 위해 사용하는 기법 중 하나입니다. 이벤트 루프로 인해 setTimeout의 콜백 함수인 longRunningTask가 태스크 큐로 보내지므로 순서대로 실행되지 않는다는 것을 알 수 있습니다. 다음 작업이 먼저 실행된 후, 오래 걸리는 작업이 완료됩니다.  

다만, 아무리 논 블로킹 방식으로 코드를 작성하더라도 코드가 전부 여러분이 작성한 것이라면 전체 소요 시간이 짧아지지는 않습니다. 여러분의 코드는 서로 동시에 실행되지 않기 때문입니다. 단순히 실행 순서만 바뀔 뿐입니다.  

그렇다고 I/O 작업이 없다고 해서 논 블로킹이 의미가 없는 것은 아닙니다. **오래 걸리는 작업을 처리해야 하는 경우, 논 블로킹을 통해 실행 순서를 바꿔줌으로써 그 작업 때문에 간단한 작업들이 대기하는 상황을 막을 수 있다는 점에서 의의가 있습니다.** 또한, **논 블로킹**과 **동시**가 같은 의미가 아니라는 것도 알아두세요. **동시성**은 **동시 처리가 가능한 작업을 논 블로킹 처리해야 얻을 수 있습니다.**  

* 노드에서는 동기와 비동기라는 개념도 있는데, 일단 동기와 블로킹이 유사하고 비동기와 논 블로킹이 유사하다고만 알아둡시다.

### 1.1.5 싱글 스레드

* **싱글 스레드**란 스레드가 하나뿐이라는 것을 의미합니다. 여러분이 작성한 자바스크립트 코드가 동시에 실행될 수 없는 이유이기도 합니다.

* 프로세스는 **운영체제에서 할당하는 작업의 단위**입니다. 노드나 웹 브라우저 같은 프로그램은 개별적인 프로세스입니다. 프로세스 간에는 메모리 등의 자원을 공유하지 않습니다.

* 스레드는 **프로세스 내에서 실행되는 흐름의 단위**입니다. 프로세스는 스레드를 여러 개 생성해 여러 작업을 동시에 처리할 수 있습니다. 스레드들은 부모 프로세스의 자원을 공유합니다. 같은 주소의 메모리에 접근 가능하므로 데이터를 공유할 수 있습니다.

노드를 실행하면 먼저 프로세스가 하나 생성됩니다. 그리고 그 프로세스에서 스레드들을 생성하는데, 이때 내부적으로 스레드를 여러 개 생성합니다. 그중에서 여러분이 직접 제어할 수 있는 스레드는 하나뿐입니다. 그래서 흔히 노드가 싱글 스레드라고 여겨지는 것입니다.  

스레드를 작업을 처리하는 일손으로 표현하기도 하는데, 하나의 스레드만 직접 조작할 수 있으므로 일손이 하나인 셈입니다. 요청이 많이 들어오면 한 번에 하나씩 요청을 처리합니다. 블로킹이 심하게 일어나는 작업을 처리하지만 않는다면 스레드 하나로도 충분합니다. 블로킹이 발생할 것같은 경우에는 논 블로킹 방법으로 대기 시간을 최대한 줄입니다.  

언뜻 보면 멀티 스레드가 더 좋아보이지만 꼭 그런 것은 아닙니다. 손님의 수가 늘어날수록 점원의 수도 늘어나고, 손님 수가 줄어들었을 때 일을 하지 않고 노는 점원이 있다는 것도 문제가 됩니다. 점원을 새로 고용하거나 해고하는데는 비용이 발생합니다.  
  
멀티 스레드가 모두 논 블로킹 방식으로 주문을 받으면 더 좋은데, 멀티 스레드 방식으로 프로그래밍하는 것은 상당히 어렵기 때문에 멀티 프로세싱으로 대신 사용합니다. I/O 요청에는 멀티 프로세싱이 더 효율적이기도 합니다.  

I/O 작업을 처리할 때는 멀티 스레딩보다 멀티 프로세싱이 효율적이므로 노드는 멀티 프로세싱을 많이 합니다.

## 1.2 서버로서의 노드

* 노드는 기본적으로 싱글 스레드, 논 블로킹 모델을 사용하므로, 노드 서버 또한 동일한 모델일 수밖에 없습니다. **따라서 노드 서버의 장단점은 싱글 스레드, 논 블로킹 모델의 장단점과 크게 다르지 않습니다.**

서버에는 기본적으로 I/O 요청이 많이 발생하므로, **I/O 처리를 잘하는 노드를 서버로 사용**하면 좋습니다. 노드는 libuv 라이브러리를 사용하여 I/O 작업을 **논 블로킹 방식**으로 처리합니다. **따라서 스레드 하나가 많은 수의 I/O를 혼자서도 감당**할 수 있습니다. 하지만 노드는 CPU 부하가 큰 작업에는 적합하지 않습니다. 우리가 작성하는 코드는 모두 스레드 하나에서 처리됩니다. 코드가 CPU 연산을 많이 요구하면 스레드 하나가 혼자서 감당하기 어렵습니다. 

이와 같은 특성을 활용하려면 노드를 어디에 사용해야 할까요? **개수는 많지만 크기는 작은 데이터(CPU연산이 적은 데이터)를 실시간으로 주고받는 데 적합**합니다. 네트워크나 데이터베이스, 디스크 작업 같은 I/O에 특화되어 있기 때문입니다. 실시간 채팅 애플리케이션이나 주식 차트, JSON 데이터를 제공하는 API 서버가 노드를 많이 사용합니다.  

노드 12 버전에서 워커 스레드 기능의 안정화로 멀티 스레드 작업을 할 수 있게 되었지만, 멀티 스레드 프로그래밍을 하는 것은 싱글 스레드에 비해 어렵습니다. 특히 스레드가 작업을 나눠서 처리할 수 있게 직접 나누어주는 것이 그렇습니다. 또한, 멀티 스레드 프로그래밍을 하더라도 C, C++, Rust, Go와 같은 언어에 비해 속도가 많이 느립니다.  

따라서 멀티 스레드 기능이 있다고 하더라도 이미지나 비디오 처리, 혹은 대규모 데이터 처리처럼 CPU를 많이 사용하는 작업을 위한 서버로는 권장하지 않습니다. 그럼에도 사용하고자 한다면 AWS 람다(AWS Lambda)나 구글 클라우드 펑션스(Google Cloud Functions) 같은 서비스에서 노드로 CPU를 많이 사용하는 작업을 처리하는 것을 지원하므로 고려해야 합니다. **싱글 스레드 방식의 프로그래밍은 하나뿐인 스레드가 에러로 인해 멈추지 않도록 잘 관리해야 합니다.** 에러를 제대로 처리하지 못하면 하나뿐인 스레드가 죽어버려서 서버 전체가 멈추기 때문입니다. 노드에는 웹 서버가 내장되어 있으므로 편리하지만, 나중에 서버 규모가 커지면 nginx 등의 웹 서버를 노드 서버와 연결해야만 합니다.

노드를 사용하면 자바스크립트를 사용하기에 하나의 언어로 웹 사이트를 개발할 수 있습니다. 생산성은 매우 좋지만, Go처럼 비동기에 강점을 보이는 언어나 nginx처럼 정적 파일 제공, 로드 밸런싱에 특화된 웹 서버에 비해서는 속도가 느립니다. 자바스크립트를 사용함으로써 얻을 수 있는 또 다른 장점은 JSON을 사용할 때 노드에서 쉽게 처리할 수 있는 것입니다.

## 1.3 서버 외의 노드

노드를 대부분 서버로 사용했지만, 노드는 자바스크립트 런타임이므로 용도가 서버에만 한정되지 않습니다. 웹, 모바일, 데스크톱 애플리케이션 개발에도 사용되기 시작했습니다. 노드 기반 웹 프레임워크로는 앵귤러(Angular), 리액트(React), 뷰(Vue) 등이 있습니다. 앵귤러는 구글 진영에서 프런트엔드 앱을 만들 때, 리액트는 페이스북 진영에서 주로 사용합니다. 모바일 개발 도구로는 리액트 네이티브(React Native)를 많이 사용합니다. 페이스북, 인스타그램, 핀터레스트, 월마트, 테슬라 등이 리액트 네이티브를 사용하여 모바일 앱을 운영 중입니다. 데스크톱 개발 도구로는 일렉트론(Electron)이 대표적입니다. 일렉트론으로 만들어진 프로그램으로는 Atom, Slack, Discord 등이 있습니다.

# 2장. 알아두어야 할 자바스크립트

## 2.1 ES2015+

### 2.1.1 const, let

```js
if (true) {
    var x = 3;
}
console.log(x); // 3

if (true) {
    const y = 3;
}
console.log(y); // Uncaught ReferenceError: y is not defined
```

var은 함수 스코프를 가지므로 if문의 블록과 관계없이 접근할 수 있습니다. 하지만 **const와 let은 블록 스코프를 가지므로** 블록 밖에서는 변수에 접근할 수 없습니다. 블록의 범위는 **if, while, for, function 등에서 볼 수 있는 중괄호({와 } 사이)** 입니다. 함수 스코프 대신 블록 스코프를 사용함으로써 호이스팅 같은 문제도 해결되고 코드 관리도 수월해졌습니다.

* const는 한 번 값을 할당하면 다른 값을 할당할 수 없습니다. 다른 값을 할당하려고 하면 에러가 발생합니다. 또한, 초기화할 때 값을 할당하지 않으면 에러가 발생합니다. **따라서 const로 선언한 변수를 상수라고 부르기도 합니다.

```js
const a = 1;
a = 0; // 에러 발생
let b = 0;
b = 1;
const c; // 에러 발생
```

* 자바스크립트에서 한 번 초기화했던 변수에 다른 값을 할당하는 경우는 의외로 적기 때문에 변수 선언시에는 **기본적으로 const를 사용하고, 다른 값을 할당해야 하는 상황이 생겼을 때 let을 사용**하면 됩니다.

### 2.1.2 템플릿 문자열

백틱(`)으로 문자열을 감싸면 문자열 아에 변수를 넣을 수 있습니다.

```js
const num3 = 1;
const num4 = 2;
const result2 = 3;
const string2 = `${num3} 더하기 ${num4}는 '${result2}'`;
console.log(string2); // 1 더하기 2는 '3'
```

* ${변수} 형식으로 변수를 더하기 기호(연결 연산자) 없이 문자열에 넣을 수 있습니다. 백틱을 사용하기에 작은따옴표나 큰따옴표를 이스케이프 하지 않아도 됩니다.

### 2.1.3 객체 리터럴

다음 코드는 oldObject 객체에 동적으로 속성을 추가하고 있습니다.

```js
var sayNode = function() {
    console.log('Node');
};
var es = 'ES';
var oldObject = {
    sayJS: function() {
        console.log('JS');
    },
    sayNode: sayNode,
};
oldObject[es + 6] = 'Fantastic';
oldObject.sayNode();    // Node
oldObject.sayJS();      // JS
console.log(oldObject.ES6);
```

이 코드를 다음과 같이 쓸 수 있습니다.

```js
const newObject = {
    sayJS() {
        console.log('JS');
    },
    sayNode,
    [es + 6]: 'Fantastic',
};
newObject.sayNode();    // Node
newObject.sayJS();      // JS
console.log(newObject.ES6); // Fantastic
```

* sayJS 같은 객체의 메서드에 함수를 연결할 때 더는 콜론(:)과 function을 붙이지 않아도 됩니다.

* sayNode: sayNode처럼 속성명과 변수명이 동일한 경우에는 한 번만 써도 되게 바뀌었습니다. 즉, 다음과 같은 경우 코드의 중복을 피할 수 있습니다.

```js
{ name: name, age: age } // ES5
{ name, age } // ES2015
```

객체의 속성명은 **동적으로 생성할 수 있습니다.** 예전 문법은 객체 리터럴 바깥에서 [es + 6]를 해야 했지만, ES2015문법에서는 객체 리터럴 안에 동적 속성을 선언해도 됩니다. newObject 안에서 [es + 6]가 속성명으로 바로 사용되고 있습니다.

### 2.1.4 화살표 함수

```js
function add1(x, y) {
    return x + y;
}

const add2 = (x, y) => {
    return x + y;
};

const add3 = (x, y) => x + y;

const add4 = (x, y) => (x + y);

function not1(x) {
    return !x;
}

const not2 = x => !x;
```

add1, add2, add3, add4는 같은 기능을 하는 함수입니다. 마찬가지로 not1과 not2도 같은 기능을 합니다. 화살표 함수에서는 function 선언 대신 => 기호로 함수를 선언합니다. 또한 **변수에 대입하면 나중에 재사용할 수 있습니다.** 함수에서 내부에 return 밖에 없으면 return문을 줄일 수 있습니다.

기존 function과 다른 점은 this 바인드 방식입니다.

```js
var relationship1 = {
    name: 'zero',
    friends: ['nero', 'hero', 'xero'],
    logFriends: function() {
        var that = this;    // relationship1을 가리키는 this를 that에 저장
        this.friends.forEach(function (friend) {
            console.log(that.name, friend);
        });
    };
};
relationship1.logFriends();
// zero nero
// zero hero
// zero xero

const relationship2 = {
    name: 'zero',
    friends: ['nero', 'hero', 'xero'],
    logFriends() {
        this.friends.forEach(friend => {
            console.log(this.name, friend);
        });
    }
};
relationship2.logFriends();
// zero nero
// zero hero
// zero xero
```

relationship1.logFriends() 안의 forEach문에서는 function 선언문을 사용했습니다. **각자 다른 함수 스코프의 this를 가지므로** that이라는 변수를 사용해서 relationship1에 간접적으로 접근하고 있습니다.

하지만 relationship2.logFriend() 안의 forEach문에서는 화살표 함수를 사용했습니다. 따라서 **바깥 스코프인 logFriend()의 this를 그대로 사용**할 수 있습니다. **상위 스코프의 this를 그대로 물려받는 것입니다.**

즉, 기본적으로는 화살표 함수를 쓰되, this를 사용해야 하는 경우에는 화살표 함수와 함수 선언문(function) 중에서 하나를 고르면 됩니다.

### 2.1.5 구조분해 할당

구조분해 할당을 사용하면 객체와 배열로부터 속성이나 요소를 쉽게 꺼낼 수 있습니다. 다음은 객체의 속성을 같은 이름의 변수에 대입하는 코드입니다.

```js
var candyMachine = {
    status: {
        name: 'node',
        count: 5,
    },
    getCandy: function () {
        this.status.count--;
        return this.status.count;
    },
};
var getCandy = candyMachine.getCandy;
var count = candyMachine.status.count;
```
이 코드를 다음과 같이 바꿀 수 있습니다.
```js
const candyMachine = {
    status: {
        name:'node',
        count: 5,
    },
    getCandy() {
        this.status.count--;
        return this.status.count;
    },
};
const { getCandy, status: { count } } = candyMachine;
```

candyMachine 객체 안의 속성을 찾아서 변수와 매칭합니다. count처럼 여러 단계 안의 속성도 찾을 수 있습니다. getCandy와 count 변수가 초기화된 것입니다. 다만 구조분해 할당을 사용하면 함수의 this가 달라질 수 있습니다. 달라진 this를 원래대로 바꿔주려면 bind 함수를 따로 사용해야 합니다.

* 배열에 대한 구조분해 할당 문법도 존재합니다.

```js
var array = ['nodejs', {}, 10, true];
var node = array[0];
var obj = array[1];
var bool = array[3];
```
다음과 같이 바꿀 수 있습니다.
```js
const array = ['nodejs', {}, 10, true];
const [node, obj, , bool] = array;
```
10은 변수를 주지 않았으므로 무시합니다. 노드는 모듈 시스템을 사용하므로 이러한 방식을 자주 씁니다.

### 2.1.6 클래스

클래스 문법도 추가되었습니다. 하지만 다른 언어처럼 클래스 기반으로 동작하는 것이 아니라 여전히 프로토타입 기반으로 동작합니다. 프로토타입 기반 문법을 보기 좋게 클래스로 바꾼 것입니다.

다음은 프로토타입 상속 예제 코드입니다.

```js
var Human = function(type) {    // Human이라는 프로토타입 생성. type의 기본값은 human임
    this.type = type || 'human';
};

Human.isHuman = function(human) {   // 인수 human이 Human의 인스턴스라면 true를 반환하며, 아닐 시 false를 반환
    return human instanceof Human;
}

Human.prototype.breathe = function() {  // Human의 인스턴스에 breathe() 메서드 추가
    alert('h-a-a-a-m');
};

var Zero = function(type, firstName, lastName) {    // human의 type에 적용. Zero에서 첫 번째 매개변수에 인수를 넣으면 human에 type을 넣은 것과 동일한 효과
    Human.apply(this, arguments);
    this.firstName = firstName;
    this.lastName = lastName;
}

Zero.prototype = Object.create(Human.prototype);    // human의 메서드를 받음 breathe()를 입력하면 정상 작동됨, 생성자 Human.isHuman(oldZero)를 하면 true를 반환
Zero.prototype.constructor = Zero;  // Zero를 통해 인스턴스를 생성할 때 상속하는 부분
Zero.prototype.sayName = function() {   // Zero의 메서드
    alert(this.firstName + ' ' + this.lastName);
};
var oldZero = new Zero('human','Zero', 'Cho');
Human.isHuman(oldZero); // true
```

Zero 생성자 함수를 보면  상속받기 위한 코드가 상당히 난해합니다. Human.apply와 Object.create 부분이 상속받는 부분입니다.

위 코드를 클래스 기반 코드로 바꿉니다.

```js
class Human {
    constructor(type = 'human') {
        this.type = type;
    }

    static isHuman(human) {
        return human instanceof Human;
    }

    breathe() {
        alert('h-a-a-a-m');
    }
}

class Zero extends Human {
    constructor(type, firstName, lastName) {
        super(type);
        this.firstName = firstName;
        this.lastName = lastName;
    }

    sayName() {
        super.breathe();
        alert(`${this.firstName} ${this.lastName}`);
    }
}

const newZero = new Zero('human', 'Zero', 'Cho');
Human.isHuman(newZero);    // true
```

전반적으로 class 안으로 그룹화된 것을 볼 수 있습니다. 생성자 함수는 constructor 안으로 들어갔고, Human.isHuman 같은 클래스 함수는 static 키워드로 전환되었습니다. 프로토타입 함수들도 모두 class 블록 안에 포함되어 어떤 함수가 어떤 클래스 소속인지 보기 쉽습니다. 상속도 간단해져서 extends 키워드로 쉽게 상속 가능합니다. 다만, 자바스크립트는 클래스 문법으로 바뀌었더라도 프로토타입 기반으로 동작한다는 것을 명심해야 합니다.

### 2.1.7 프로미스

자바스크립트와 노드에서는 주로 **비동기**를 접합니다. 특히 이벤트 리스너를 사용할 때 콜백 함수를 자주 사용합니다. ES2015부터는 자바스크립트와 노드의 API들이 콜백 대신 **프로미스(Promise)** 기반으로 재구성되며, 악명 높은 콜백 지옥(callback hell) 현상을 극복했다는 평가를 받고 있습니다.

프로미스는 다음과 같은 규칙이 있습니다. 먼저 프로미스 객체를 생성해야 합니다.

```js
const condition = true; // true면 resolve, false면 reject
const promise = new Promise((resolve, reject) => {
    if (condition) {
        resolve('성공');
    } else {
        reject('실패');
    }
});
// 다른 코드가 들어갈 수 있음
promise
    .then((message) => {
        console.log(message);   // 성공(resolve)한 경우 실행
    })
    .catch((error) => {
        console.error(error);   // 실패(reject)한 경우 실행
    })
    .finally(() => {    // 끝나고 무조건 실행
        console.log('무조건');
    });
```

new Promise로 프로미스를 생성할 수 있으며, 그 내부에 resolve와 reject를 매개변수로 갖는 콜백 함수를 넣습니다.이렇게 만든 promise 변수에 then과 catch 메서드를 붙일 수 있습니다. 프로미스 내부에서 resolve가 호출되면 then이 실행되고, reject가 호출되면 catch가 실행됩니다. finally 부분은 성공/실패 여부와 상관없이 실행됩니다.

resolve와 reject에 넣어준 인수는 각각 then과 catch의 매개변수에서 받을 수 있습니다. 즉, **`resolve('성공')`이 호출되면 then의 message가 '성공'이 됩니다.** 만약 **`reject('실패')`가 호출되면 catch의 error가 '실패'가 되는 것입니다.** condition 변수를 false로 바꿔보면 catch에서 에러가 로깅됩니다.

프로미스를 쉽게 설명하자면, **실행은 바로 하되 결괏값은 나중에 받는 객체입니다.** 결괏값은 실행이 완료된 후 then이나 catch 메서드를 통해 받습니다. 위 예제에서는 new Promise와 promise, then 사이에 다른 코드가 들어갈 수도 있습니다. new Promise는 바로 실행되지만, 결괏값은 then을 붙였을 때 받게 됩니다.

then이나 catch에서 다시 다른 then이나 catch를 붙일 수 있습니다. **이전 then의 return 값을 다음 then의 매개변수로 넘깁니다.** 프로미스를 return한 경우에는 **프로미스가 수행된 후 다음 then이나 catch가 호출**됩니다.

```js
promise
    .then((message) => {
        return new Promise((resolve, reject) => {
            resolve(message);
        });
    })
    .then((message2) => {
        console.log(message2);
        return new Promise((resolve, reject) => {
            resolve(message2);
        })
    })
    .then((message3) => {
        console.log(message3);
    })
    .catch((error) => {
        console.log(error);
    });
```

처음 then에서 message를 resolve하면 다음 then에서 message2로 받을 수 있습니다. 여기서 다시 message2를 resolve한 것을 다음 then에서 message3으로 받았습니다. 단, then에서 newPromise를 return해야 다음 then에서 받을 수 있다는 것을 기억하세요.

이것을 활용해서 콜백을 프로미스로 바꿀 수 있습니다. 다음은 콜백을 쓰는 패턴 중 하나입니다. 이를 프로미스로 바꿔보겠습니다.

```js
function findAndSaveUser(Users) {
    Users.findOne({}, (err, user) => {  // 첫 번째 콜백
        if (err) {
            return console.error(err);
        }
        user.name = 'zero';
        user.save((err) => { // 두 번째 콜백
            if (err) {
                return console.error(err);
            }
            Users.findOne({ gender: 'm' }, (err, user) => { // 세 번째 콜백
                // 생략
            })
        })
    })
}
```

콜백 함수가 세 번 중첩되어 있습니다. 콜백 함수가 나올 때마다 코드의 깊이가 깊어집니다. 각 콜백 함수마다 에러도 따로 처리해줘야 합니다. 이 코드를 다음과 같이 바꿀 수 있습니다.

```js
function findAndSaveUser(Users) {
    Users.findOne({})
    .then((user) => {
        user.name = 'zero';
        return user.save();
    })
    .then((user) => {
        return Users.findOne({ gender: 'm' });
    })
    .then((user) => {
        // 생략
    })
    .catch(err => {
        console.error(err);
    });
}
```

코드의 깊이가 세 단계 이상 깊어지지 않습니다. 위 코드에서 then 메서드들은 순차적으로 실행됩니다. 콜백에서 매번 따로 처리해야 했던 에러도 마지막 catch에서 한 번에 처리할 수 있습니다. 하지만 모든 콜백 함수를 위와 같이 바꿀 수 있는 것은 아닙니다. 메서드가 프로미스 방식을 지원해야 합니다.

예제의 코드는 findOne과 save 메서드가 내부적으로 프로미스 객체를 가지고 있다고 가정했기에 가능합니다(new Promise가 함수 내부에 구현되어 있어야 합니다). 지원하지 않는 경우 콜백 함수를 프로미스로 바꿀 수 있는 방법은 3.5.6 절에 나와 있습니다.

프로미스 여러 개를 한 번에 실행할 수 있는 방법이 있습니다. 기존의 콜백 패턴이었다면 콜백을 여러 번 중첩해서 사용해야 했을 것입니다. 하지만 Promise.all을 활용하면 간단히 할 수 있습니다.

```js
const promise1 = Promise.resolve('성공1');
const promise2 = Promise.resolve('성공2');
Promise.all([promise1, promise2])
    .then((result) => {
        console.log(result); // ['성공1', '성공2'];
    })
    .catch((error) => {
        console.log(error);
    });
```

Promise.resolve는 즉시 resolve하는 프로미스를 만드는 방법입니다. 비슷한 것으로 즉시 reject하는 Promise.reject도 있습니다. 프로미스가 여러 개 있을 때 Promise.all에 넣으면 모두 resolve될 때까지 기다렸다가 then으로 넘어갑니다. result 매개변수에 각각의 프로미스 결괏값이 배열로 들어 있습니다. Promise 중 하나라도 reject가 되면 catch로 넘어갑니다.

### 2.1.8 async/await

노드처럼 비동기 위주로 프로그래밍을 해야 할 때 도움이 많이 됩니다. 프로미스가 콜백 지옥을 해결했다지만, 여전히 코드가 장황합니다. then과 catch가 계속 반복되기 때문입니다. async/await 문법은 프로미스를 사용한 코드를 한 번 더 깔끔하게 줄입니다.

2.1.7 절의 프로미스 코드를 다시 한 번 보겠습니다.

```js
function findAndSaveUser(Users) {
    Users.findOne({})
    .then((user) => {
        user.name = 'zero';
        return user.save();
    })
    .then((user) => {
        return Users.findOne({ gender: 'm' });
    })
    .then((user) => {
        // 생략
    })
    .catch(err => {
        console.error(err);
    });
}
```

콜백과 다르게 코드의 깊이가 깊어지진 않지만, 코드는 여전히 깁니다. async/await 문법을 사용하면 다음과 같이 바꿀 수 있습니다. async function이라는 것이 추가되었습니다.

```js
async function findAndSaveUser(Users) {
    let user = await User.findOne({});
    user.name = 'zero';
    user = await user.save();
    user = await User.findOne({ gender: 'm' });
    // 생략
}
```

놀라운 정도로 코드가 짧아졌습니다. 함수 선언부를 일반 함수 대신 async function으로 교체한 후, 프로미스 앞에 await을 붙였습니다. 이제 함수는 해당 프로미스가 resolve될 때까지 기다린 뒤 다음 로직으로 넘어갑니다. 예를 들명 await Users.findOne({})이 resolve될 때까지 기다린 다음에 user 변수를 초기화하는 것입니다.

위 코드는 에러를 처리하는 부분(프로미스가 reject된 경우)이 없으므로 다음과 같은 추가 작업이 필요합니다.

```js
async function findAndSaveUser(Users) {
    try {
        let user = await Users.findOne({});
        user.name = 'zero';
        user = await user.save();
        user = await Users.findOne({ gender: 'm'});
        // 생략
    } catch (error) {
        console.error(error);
    }
}
```

try/catch문으로 로직을 감쌌습니다. 프로미스의 catch 메서드처럼 try/catch문의 catch가 에러를 처리합니다.

화살표 함수도 async와 같이 사용할 수 있습니다.

```js
const findAndSaveUser = async (Users) => {
    try {
        let user = await Users.findOne({});
        user.name = 'zero';
        user = await user.save();
        user = await Users.findOne({ gender: 'm'});
        // 생략
    } catch (error) {
        console.error(error);
    }
};
```

for문과 async/await을 같이 써서 프로미스를 순차적으로 실행할 수 있습니다.

```js
const promise1 = Promise.resolve('성공1');
const promise2 = Promise.resolve('성공2');
(async () => {
    for await (promise of [promise1, promise2]) {
        console.log(promise);
    }
})();
```

for await of문을 사용해서 프로미스 배열을 순회하는 모습입니다. async 함수의 반환값은 항상 Promise로 감싸집니다. 따라서 실행 후 then을 붙이거나 또 다른 async 함수 안에서 await를 붙여서 처리할 수 있습니다.

```js
async function findAndSaveUser(Users) {
    // 생략
}
findAndSaveUser().then(() =< { /* 생략 */ }>);
// 또는
async function other() {
    const result = await fundAndSaveUser();
}
```

앞으로 중첩되는 콜백 함수가 있다면 프로미스를 거쳐 async/await 문법으로 바꾸는 연습을 하는 것이 좋습니다.

## 2.2 프런트엔드 자바스크립트

### 2.2.1 AJAX

AJAX(Asynchronous Javascript And XML)는 비동기적 웹 서비스를 개발할 때 사용하는 기법입니다. 이름에 XML이 들어있지만 JSON을 더 많이 사용합니다. **쉽게 말해 페이지 이동 없이 서버에 요청을 보내고 응답을 받는 기술입니다.** 웹 사이트 중에서 페이지 전환 없이 새로운 데이터를 불러오는 사이트는 대부분 AJAX 기술을 사용하고 있다고 보면 됩니다.

보통 AJAX 요청은 jQuery나 axios 같은 라이브러리를 이용해서 보냅니다. XMLHttpRequest는 사용 방법이 복잡하고 서버에서는 사용할 수 없으므로 이 책에서는 axios를 사용합니다.

프런트엔드에서 사용하려면 HTML 파일을 하나 만들고 그 안에 script 태그를 추가해야 합니다. 두 번째 script 태그 안에 앞으로 나오는 프런트엔드 예제 코드를 넣으면 됩니다.

```html
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
<script>
    // 예제 코드 삽입
</script>
```

먼저 요청의 한 종류인 GET 요청을 보내겠습니다.

axios.get 함수의 인수로 요청을 보낼 주소를 넣으면 됩니다.

```js
axios.get('https://www.zerocho.com/api/get')
    .then((result) => {
        console.log(result);
        console.log(result.data); // {}
    })
    .catch((error) => {
        console.error(error);
    });
```

axios.get도 내부에 new Promise가 들어 있으므로 then과 catch를 사용할 수 있습니다. result.data에는 서버로부터 보낸 데이터가 들어 있습니다.

프로미스이므로 async/await 방식으로 변경할 수 있습니다. 익명 함수라서 즉시 실행을 위해 코드를 소괄호로 감싸 호출했습니다.

```js
(async () => {
        try {
            const result = await axios.get('https://www.zerocho.com/api/get');
            console.log(result);
            console.log(result.data); // {}
        } catch (error) {
            console.error(error);
        }
    })();
```

이번에는 POST 방식의 요청을 보내겠습니다. POST 요청에서는 데이터를 서버로 보낼 수 있습니다.

```js
(async () => {
        try {
            const result = await axios.post('https://www.zerocho.com/api/post/json', {
                name: 'zerocho',
                birth: '1994',
            });
            console.log(result);
            console.log(result.data); // {}
        } catch (error) {
            console.error(error);
        }
    })();
```

전체적인 구조는 비슷한데 두 번째 인수로 데이터를 넣어 보내는 것이 다릅니다. GET 요청이면 axios.get을, POST 요청이면 axios.post를 사용합니다.

### 2.2.2 FormData

HTML form 태그의 데이터를 동적으로 제어할 수 있는 기능입니다. 주로 AJAX와 함께 사용됩니다.

먼저 FormData 생성자로 formData 객체를 만듭니다.

```js
const formData = new FormData();
formData.append('name', 'zerocho');
formData.append('item', 'orange');
formData.append('item', 'melon');
formData.has('item'); //true
formData.has('money'); //false
formData.get('item'); //'orange'
formData.getAll('item'); // (2) ['orange', 'melon']
formData.append('test', ['hi', 'zero']);
formData.get('test'); //'hi,zero'
formData.delete('test');
formData.get('test'); //null
formData.set('item', 'apple');
formData.getAll('item'); // ['apple']
```

생성된 객체의 **append 메서드로 키-값 형식의 데이터를 저장**할 수 있습니다. append 메서드를 여러 번 사용해서 키 하나에 여러 개의 값을 추가해도 됩니다. **has 메서드는 주어진 키에 해당하는 값이 있는지 여부를 알립니다.** **get 메서드는 주어진 키에 해당하는 값 하나를 가져오고, getAll 메서드는 해당하는 모든 값을 가져옵니다.** **delete 메서드는 현재 키를 제거하는 메서드**고, **set은 현재 키를 수정하는 메서드**입니다.

이제 axios로 폼 데이터를 서버에 보내면 됩니다.

```js
(async () => {
    try {
        const formData = new FormData();
        formData.append('name', 'zerocho');
        formData.append('birth', 1994);
        const result = await axios.post('https://www.zerocho.com/api/post/formdata', formData);
        console.log(result);
        console.log(result.data);
    } catch (error) {
        console.error(error);
    }
})();
```

두 번째 인수에 데이터를 넣어 보냅니다.

### 2.2.3 encodeURIComponent, decodeURIComponent

AJAX 요청을 보낼 때, 'http://localhost:4000/search/노드'처럼 주소에 한글이 들어가는 경우가 있습니다. 서버 종류에 따라 다르지만 **서버가 한글 주소를 이해하지 못하는 경우가 있는데, 이럴 때는 window 객체의 메서드인 encodeURIComponent 메서드를 사용**합니다. 한글 주소 부분만 encodeURIComponent 메서드로 감쌉니다.

```js
(async () => {
    try {
        const result = await axios.get(`https://www.zerocho.com/api/search/${encodeURIComponent('노드')}`);
        console.log(result);
        console.log(result.data); // {}
    } catch (error) {
        console.error(error);
    }
})();
```

노드라는 한글 주소가 %EB%85%B8%EB%93%9C라는 문자열로 변환되었습니다.

받는 쪽에서는 decodeURIComponent를 사용하면 됩니다. 역시 브라우저뿐만 아니라 노드에서도 사용할 수 있습니다.

```js
decodeURIComponent('%EB%85%B8%EB%93%9C'); // 노드
```

### 2.2.4 데이터 속성과 dataset

노드를 웹 서버로 사용하는 경우, 클라이언트(프런트엔드)와 빈번하게 데이터를 주고받게 됩니다. 이때 서버에서 보내준 데이터를 프런트엔드 어디에 넣어야 할지 고민하게 됩니다.

프런트엔드에 데이터를 내려보낼 때 첫 번째로 고려해야 할 점은 보안입니다. 클라이언트를 믿지 말라는 말이 있을 정도로 프런트엔드에 민감한 데이터를 내려보내는 것은 실수입니다. 비밀번호 같은 건 절대 내려보내지 마세요.

보안과 무관한 데이터들은 자유롭게 프런트엔드로 보내도 됩니다. 자바스크립트 변수에 저장해도 되지만 HTML5에도 HTML과 관련된 데이터를 저장하는 공식적인 방법이 있습니다. 바로 속성(data attribute)입니다.

```html
<ul>
    <li data-id="1" data-user-job="programmer">Zero</li>
    <li data-id="2" data-user-job="designer">Nero</li>
    <li data-id="3" data-user-job="programmer">Hero</li>
    <li data-id="4" data-user-job="ceo">Kero</li>
</ul>
<script>
    console.log(document.querySelector('li').dataset);
    // { id: '1', userJob: 'programmer' }
</script>
```

위와 같이 HTML 태그의 속성으로 data-로 시작하는 것들을 넣습니다. 이들이 데이터 속성입니다. 여기서는 data-id와 data-user-job을 주었습니다. 화면에 나타나지는 않지만 웹 애플리케이션 구동에 필요한 데이터들입니다. 나중에 이 데이터들을 사용해 서버에 요청을 보내게 됩니다.

데이터 속성의 장점은 **자바스크립트로 쉽게 접근**할 수 있다는 점입니다. script 태그를 보면 dataset 속성을 통해 첫 번째 li 태그의 데이터 속성에 접근하고 있습니다. 단, 데이터 속성 이름이 조금씩 변형되었습니다. 앞의 data- 접두어는 사라지고 - 뒤에 위치한 글자는 대문자가 됩니다. data-id는 id, data-user-job은 userJob이 되는 것입니다.

반대로 dataset에 데이터를 넣어도 HTML 태그에 반영됩니다. dataset.monthSalary = 10000; 을 넣으면 data-month-salary="10000"이라는 속성이 생깁니다.