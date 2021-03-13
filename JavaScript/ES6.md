# ES6의 특징

- [let vs const](#let-vs-const)
- [화살표 함수](#화살표-함수)
- [클래스](#클래스)
- [기본값 할당하기 + Rest 문법 + Spread 문법](#기본값-할당하기--rest-문법--spread-문법)
- [반복자(iterator) + for...of](#반복자iterator--forof)
- [Generator](#generator)
- [Symbol](#symbol)
- [Map + Set + WeakMap + WeakSet](#map--set--weakmap--weakset)
- [Number + String + Array + Object 에 추가된 것들](#number--string--array--object-에-추가된-것들)
- [Promise](#promise) -> 비동기 처리에서 추가로 다룰 것이당
- [모듈 (import + export)](#모듈module) -> 모듈 시스템에서 추가로 다룰 것이당
- 템플릿 리터럴
- 비구조화


## let vs const
#### 공통점
- 블록 스코프를 갖는다.
- 재선언이 불가능하다.
- 선언 어전에 사용할 수 없다.

#### 차이점
- let은 재할당이 자유로우나, const는 재할당이 금지된다.
- const는 선언과 동시에 할당이 이루어져야 한다.


## 화살표 함수
- 일반 함수와 달리 this가 함수 스코프에 바인딩되지 않고 렉시컬 스코프를 가진다. 즉, 자신을 감싸는 코드와 동일한 this를 공유한다.
- 화살표 함수 표현식은 기존의 function 표현 방식보다 간결하게 함수를 표현할 수 있다.
- 화살표 함수는 항상 익명이며, 자신의 `this`, `argument`, `super`, `new.target`을 바인딩하지 않기 때문에 생성자로는 사용할 수 없다.


## 클래스
프로토타입 기반의 객체지향 패턴을 쉽게 만든 장치로, 상속과 생성자 및 인스턴스와 정적 메서드를 지원한다.

#### 정적 메서드
- `prototype`이 아닌 클래스 함수 자체에 메서드를 설정할 수 있는데, 이런 메서드를 정적(static) 메서드라고 한다.
- 정적 메서드는 특정 클래스 인스턴스가 아닌 클래스 전체에 필요한 기능을 만들 때 사용할 수 있다.
- 정적 메서드는 클래스 안에서 `static` 키워드를 붙여 만들 수 있다.

#### 정적 프로퍼티
- 정적 프로퍼티는 데이터를 클래스 수준에 저장하고 싶을 때 사용한다.
- 정적 프로퍼티 역시 개별 인스턴스에 묶이지 않는다.

#### Class 참고
[정적 메서드와 정적 프로퍼티](https://ko.javascript.info/static-properties-methods)


## 기본값 할당하기 + Rest 문법 + Spread 문법
### 기본값
기본값은 주어지는 값이 없을 때 초기화시키는 값이다.
`function f(x=1) {}`

### Rest 문법
Rest 문법은 명시한 변수 외에 나머지를 배열로 가져오는 것이다.
```js
function f(x, ...y) {
  // y는 배열이다. ["hello", true]
  return y.length;
}
f(3, "hello", true) == 2
```

### Spread 문법
Spread 문법은 배열을 반대로 펼치는 역할이다.


## 반복자(iterator) + for...of
반복자는 자신만의 반복을 정의하는 규약이고 이는 `for...of`를 통해 순회할 수 있다. `[Symbor.iterator]`라는 이름의 메서드를 정의해야하며 그 메서드는 반드시 `next()` 메서드를 가진 객체를 반환해야 한다.

아래는 반복자 함수의 예시이다.
```js
const fibonacci = {
  [Symbor.iterator]() {
    let pre = 0, cur = 1;
    return {
      next() {
        [pre, cur] = [cur, pre + cur];
        return { done: false, value: cur };
      }
    };
  }
};

for (const n of fibonacci) {
  if (n > 1000) break;
  console.log(n);
}
```

### iterable 객체
반복 가능한 객체. iterable한 객체는 `Symbol.iterator`라는 키를 갖고 이 프로퍼티가 있으면 `for...of` 등을 이용해 iterator의 값을 반복할 수 있다.

#### iterable한 객체
- String
- Array
- TypedArray
- Map
- Set

#### iterable한 구문
- for...of
- spread 연산자
- 구조 분해 할당
- yield* 표현식

> **`yield*` 키워드** <br>
> yield* 뒤에 iterable한 객체를 붙일 수 있다. <br>
> 이렇게 되면 yield가 수행될 때 iterable 객체를 순회하게 된다. <br>
> 예시 -> `yield* [1, 2, 3]`

#### iterator 참고
- [JavaScript와 iterator](https://pks2974.medium.com/javascript%EC%99%80-iterator-cdee90b11c0f)
- [iterable](https://helloworldjavascript.net/pages/260-iteration.html)


## Generator
Generator는 반복자를 쉽게 생성해주는 것으로 function*과 yield를 사용한다. 반복자의 하위 타입으로 next와 throw를 포함한다.

### Generator 함수
- iterable을 생성하는 함수. generator 함수를 사용하면 iteration 프로토콜을 준수해 iterable을 생성하는 방식보다 간편하게 iterable을 구현할 수 있다.
- gererator 함수는 일반 함수와 다르게 함수 코드 블록의 실행을 일시 중지했다가 필요한 시점에 재시작할 수 있는 함수이기 때문에, 비동기 처리에 유용하게 사용할 수 있다.
- generator 함수를 실행하면 iterator가 반환되는데, iterator는 next()라는 메서드를 갖는다. next() 메서드를 실행하면 generator 함수 내부에서 가장 먼저 등장하는 yield에서 함수의 실행을 멈춘다.

#### Generator 참고
- [Generator](https://jaeyeophan.github.io/2017/04/22/ES6-10-Generator/)
- [JavaScript Generator 이해하기](https://wonism.github.io/javascript-generator/)
- [poiemaweb - 제너레이터와 async/awit](https://poiemaweb.com/es6-generator)


## Symbol
Symbol은 ES6에서 추가된 유일하고 변경 불가능한 원시 타입으로 객체의 접근제어를 가능하게 한다. `description` 매개변수를 이용해 디버깅이 가능하며 `Object.getOwnPropertySymbols` 를 통해 객체의 심볼 프로퍼티들을 볼 수 있다.

```js
var MyClass = (function() {

  // IIFE 안의 심볼, 모듈화 된 것.
  // 즉, 심볼로 private 데이터 만듦
  var key = Symbol("key");

  function MyClass(privateData) {
    this[key] = privateData;
  }

  MyClass.prototype = {
    doStuff: function() {
      ... this[key] ...
    }
  };

  return MyClass;
})();

var c = new MyClass("hello");
// "key"와 Symbol("key")는 다르다.
c["key"] === undefined
```

## Map + Set + WeakMap + WeakSet
Weak가 붙은 것은 가비지 컬렉션을 허용하며, size 프로퍼티를 가지지 않는다.


## Number + String + Array + Object 에 추가된 것들
```js
Number.isInteger(Infinity) // false
Number.isNaN("NaN") // false

"abcde".includes("cd") // true
"abc".repeat(3) // "abcabcabc"

Array.from(document.querySelectorAll('*')) // 유사배열객체를 배열로 변환
Array.of(1, 2, 3) // [1,2,3]
[0, 0, 0].fill(7, 1) // [0,7,7]
[1, 2, 3].find(x => x == 3) // 3
[1, 2, 3].findIndex(x => x == 2) // 1
[1, 2, 3, 4, 5].copyWithin(3, 0) // [1, 2, 3, 1, 2]
["a", "b", "c"].entries() // 반복자 [0, "a"], [1,"b"], [2,"c"]
["a", "b", "c"].keys() // 반복자 0, 1, 2
["a", "b", "c"].values() // 반복자 "a", "b", "c"

Object.assign(Point, { origin: new Point(0,0) }) // 얕은 복사
```


## Promise
자바스크립트 비동기 처리에 사용되는 객체이다. 콜백 지옥을 해결하기 위해, 비동기적인 일련의 작업을 동기적으로 혹은 동기적인 것처럼 보이게 해주기 위해 등장한 것이 promise이다.

promise 패턴을 사용하면 비동기 작업들을 순차적으로 실행하거나, 병렬로 진행하는 등의 작업이 수웧해진다. 또한, 예외처리에 대한 구조가 존재하기 때문에 오류 처리를 보다 가시적으로 관리할 수 있다.

```js
function timeout(duration = 0) {
    return new Promise((resolve, reject) => {
        setTimeout(resolve, duration);
    });
}

var p = timeout(1000).then(() => {
    return timeout(2000);
}).then(() => {
    throw new Error("hmm");
}).catch(err => {
    return Promise.all([timeout(100), timeout(200)]);
});
```

### promise가 필요한 이유
promise는 주로 서버에서 받아온 데이터를 화면에 표시할 때 사용한다. 서버에 요청을 보냈는데 데이터를 받아오기도 전에 마치 데이터를 받아온 것처럼 화면에 표시하려고 한다면, 오류가 발생하거나 빈 화면이 뜨게 된다. 이와 같은 문제점을 해결하기 위한 방법 중 하나가 promise이다.


## 모듈(Module)
- export로 모듈 내보내기

```js
// lib/math.js
export function sum(x, y) {
  return x + y;
}
export var pi = 3.141593;
```

- import로 모듈 불러오기

```js
// app.js
import * as math from "lib/math";
alert("2π = " + math.sum(math.pi, math.pi));

// otherApp.js
import {sum, pi} from "lib/math";
alert("2π = " + sum(pi, pi));
```


## 참고
[ES6의 특징들](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/javascript/es6.md)