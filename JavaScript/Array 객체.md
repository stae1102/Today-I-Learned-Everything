- [1. Array 객체란?](#1-array-객체란)
  - [Array 객체로 배열 만들기](#array-객체로-배열-만들기)
  - [배열에서 for문 사용하기](#배열에서-for문-사용하기)
- [2. Array 객체의 함수 알아보기](#2-array-객체의-함수-알아보기)
  - [둘 이상의 배열을 연결하는 `concat()` 함수](#둘-이상의-배열을-연결하는-concat-함수)
  - [배열 요소를 연결하는 `join()` 함수](#배열-요소를-연결하는-join-함수)
  - [새로운 요소를 추가하는 `push()` 함수와 `unshift()` 함수](#새로운-요소를-추가하는-push-함수와-unshift-함수)
  - [배열에서 요소를 추출하는 `pop()` 함수와 `shift()` 함수](#배열에서-요소를-추출하는-pop-함수와-shift-함수)
  - [원하는 위치의 요소를 삭제하거나 추가하는 `splice()`](#원하는-위치의-요소를-삭제하거나-추가하는-splice)
    - [인수가 1개일 경우](#인수가-1개일-경우)
    - [인수가 2개일 경우](#인수가-2개일-경우)
    - [인수가 3개 이상일 경우](#인수가-3개-이상일-경우)
  - [원하는 위치의 요소들을 추출하는 `slice()` 함수](#원하는-위치의-요소들을-추출하는-slice-함수)

# 1. Array 객체란?

여러 개의 항목을 하나의 변수에 저장해야 할 때 '배열(Array)'을 자주 사용합니다.

## Array 객체로 배열 만들기

자바스크립트에서는 배열을 쉽게 만들고 다룰 수 있게 미리 Array 객체가 만들어져 있습니다.

```js
var myArray = new Array(); // Array 객체의 인스턴스를 만듭니다.
```

초깃값이 있는 배열이라면 리터럴을 사용한 방법으로 배열을 만들 수도 있고 Array 객체를 사용해서 만들 수도 있습니다.

```js
var numbers = ["one", "two", "three", "four"];  // 리터럴을 사용한 배열
var numbers = new Array("one", "two", "three", "four");  // Array 객체를 사용한 배열
```

## 배열에서 for문 사용하기

배열은 for문과 함께 자주 사용됩니다. for문을 통해 요소를 처음부터 끝까지 반복할 수 있으며, 배열의 요소 개수를 활용하기 위해서 length 속성을 이용하기도 합니다.

```js
for (let i=0; i<numbers.length; i++) {
    console.log(numbers[i])
}
```

# 2. Array 객체의 함수 알아보기

## 둘 이상의 배열을 연결하는 `concat()` 함수

기존의 배열에 또 다른 배열이나 값을 합쳐서 새로운 배열을 만드는 함수입니다.

```js
var nums = ["1", "2", "3"];
var chars = ["a", "b", "c", "d"];
nums.concat(chars)  // nums 배열에 chars 배열 연결
▶ (7) ["1", "2", "3", "a", "b", "c", "d"]
```

concat()은 새로운 배열을 만들기 때문에 함수에 사용한 기존의 두 배열에는 영향을 미치지 않습니다.

## 배열 요소를 연결하는 `join()` 함수

join() 함수는 배열 요소를 연결하는 함수입니다. 배열요소를 연결할 때 요소들을 구분할 기호가 필요한데 기본값은 콤마(,)이며, 괄호 한에 연결할 기호를 넣어 연결할 수 있습니다.

```js
nums.join("-")
"1-2-3"
```

## 새로운 요소를 추가하는 `push()` 함수와 `unshift()` 함수

배열의 맨 끝에 요소를 추가하려면 push() 함수를, 맨 앞에 요소를 추가하려면 unshift() 함수를 사용합니다.

```js
var nums = ["1", "2", "3"];
nums.push("4", "5");
5   // 새 요소가 추가된 후의 배열 요소의 개수가 반환됨
nums.unshift("0");
6
```

## 배열에서 요소를 추출하는 `pop()` 함수와 `shift()` 함수

배열의 맨 끝에서 요소를 추출하려면 pop() 함수를, 맨 앞에서 요소를 추출하려면 shift() 함수를 사용합니다.

```js
var js = ["es6+", "node", "react", "angular", "vue"]
js.shift()
"es6+"
```

## 원하는 위치의 요소를 삭제하거나 추가하는 `splice()`

배열의 중간 부분에 요소를 추가하거나 삭제하기 위해서 사용하는 함수가 splice() 함수입니다.

### 인수가 1개일 경우

이 경우에 splice() 함수는 인수가 가리키는 인덱스 요소부터 배열의 끝 요소까지 삭제합니다.

```js
var numbers = [0, 1, 2, 3, 4, 5]
numbers.splice(2)
▶ (4) [2, 3, 4, 5]
numbers
▶ (2) [0, 1]
```

### 인수가 2개일 경우

첫 번째 인수는 **인덱스 값**이고, 두 번째 인수는 **삭제할 개수**입니다.
numbers.splice(2, 1)이라고 한다면, numbers에서 인덱스가 2인 값에서 1개를 삭제한다는 의미입니다.

```js
var study = ["html", "css", "web", "jquery"]
study.splice(2, 1)
▶ ["web"]
study
▶ (3) ["html", "css", "jquery"]
```

### 인수가 3개 이상일 경우

첫 번째 인수는 해당 배열에서 삭제할 위치, 두 번째 인수는 삭제할 개수를 알려주며, 세 번째 인수부터는 삭제한 위치에 새로 추가할 요소를 지정합니다.

* 기존 요소를 삭제하지 않고 새로운 요소를 추가하고 싶다면 삭제할 개수를 지정하는 두 번째 인수에 0을 넣으면 됩니다.

## 원하는 위치의 요소들을 추출하는 `slice()` 함수

* 파이썬의 슬라이싱과 사용방법이 동일합니다.

slice() 함수의 첫 번째 인수는 시작위치를, 두 번째 인수는 종료 위치를 의미합니다. slice() 함수는 첫 번째 인수 위치부터 두 번째 인수 위치 직전까지 추출해 반환합니다. 시작 인덱스만 지정할 경우, 시작 인덱스부터 끝까지 추출합니다. **원래 배열에 영향을 주지 않습니다.**