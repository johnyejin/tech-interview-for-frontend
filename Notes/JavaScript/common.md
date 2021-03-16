# JavaScript 기본
- [null vs undefined](#null-vs-undefined)
- [var vs let vs const](#var-vs-let-vs-const)
- [네이티브 객체 vs 호스트 객체](#네이티브-객체-vs-호스트-객체)
- [falsy한 값](#falsy한-값)
- [== vs ===](#-vs-)
- [엄격 모드](#엄격-모드-strict-mode)

<br>

## null vs undefined
둘 다 '없음'을 나타내는 값이다. `undefined`는 어떤 변수에 값이 존재하지 않을 경우를 의미하고 `null`은 사용자가 명시적으로 '없음'을 표현하기 위해 대입한 값이다.

본래의 의미에 따라 사용자가 없음을 표현하기 위해 명시적으로 `undefined`를 대입하는 것은 지양하는 것이 좋다.
즉, `undefined`는 오직 **값을 대입하지 않은 변수에 접근하고자 할 때 자바스크립트 엔진이 반환해주는 값**으로서만 존재하게 한다.

### 자바스크립트 엔진이 undefined를 반환하는 경우
1. 값을 대입하지 않은 변수에 접근할 때
2. 객체 내부의 존재하지 않는 프로퍼티에 접근하려고 할 때
3. return문이 없거나 호출되지 않는 함수의 실행 결과

<br>

## `var` vs `let` vs `const`
모두 변수를 선언하는 키워드라는 것은 동일하다. 하지만, let과 const는 ES6에서 등장했고 여러 다른 특성을 갖는다.

#### 스코프 규칙
- var는 함수 스코프를 갖는다.
- let과 const는 블록 스코프를 갖는다.

#### 호이스팅
- var는 함수 스코프의 최상단으로 호이스팅되고 선언과 동시에 undefined로 초기화된다.
- let과 const는 블록 스코프의 최상단으로 호이스팅되고 선언만 되고 값이 할당되기 전까지 어떤 값으로도 초기화되지 않는다. -> 선언 전에 호출하면 에러가 발생한다.

#### 글로벌 객체로의 바인딩
- var는 글로벌 스코프에서 선언되었을 경우 글로벌 객체에 바인딩된다.
- let과 const는 글로벌 스코프에서 선언되었을 경우, 글로벌 객체에 바인딩되지 않는다.

#### 재선언
- var는 재선언이 가능하다.
- let과 const는 재선언이 불가능하다.

### `const`로 객체를 선언한 경우, 객체의 프로퍼티는 바뀌지 않을까?
`const`로 객체를 선언한 경우 재할당은 불가능하지만, 할당된 객체의 프로퍼티는 보호되지 않는다. 객체의 내용이 변경되더라도 객체 타입 변수에 할당된 주소값은 변경되지 않기 때문이다.

<br>

## 네이티브 객체 vs 호스트 객체
### 네이티브 객체
ESMAScript 명세에 정의된 객체. 애플리케이션 전역의 공통 기능을 제공한다. 네이티브 객체는 애플리케이션의 환경과 관계없이 언제나 사용할 수 있다. `Object`, `String`, `Number`, `Function`, `Array`, `RegExp`, `Date`, `Math` 등이 있다.

### 호스트 객체
호스트 객체는 호스트 환경에 정의된 객체를 말한다. 예를 들어, 브라우저에서 동작하는 환경과 브라우저 외부에서 동작하는 환경의 자바스크립트(node.js)는 다른 호스트 객체를 사용할 수 있다.

만약 브라우저 환경이라면 다음과 같은 것들이 존재한다.
`window`, `document`, `location`, `XMLHttpRequest`, `querySelectorAll`,,,

[Built-in Object | PoiemaWeb](https://poiemaweb.com/js-built-in-object)

<br>

## falsy한 값
다음 값들은 모두 false로 변환되어 if 블록이 실행되지 않는다.

- if (false)
- if (null)
- if (undefined)
- if (0)
- if (-0)
- if (0n)
- if (NaN)
- if ("")

[Truthy and Falsy](https://learnjs.vlpt.us/useful/02-truthy-and-falsy.html)

<br>

## == vs ===
둘 다 동일한 비교를 하지만 엄격한 동등 비교 연산자(===)의 경우, 타입변환이 일어나지 않으며 타입이 일치해야 한다. 단, 객체/배열의 경우는 참조타입이기 때문에 두 연산자 모두 동일하게 동작한다.

문자열의 경우는 좀 특별한데, 자바스크립트에서 문자열은 원시 타입이지만 객체로도 만들 수 있기 때문에 동등 비교가 다르다.

```js
var a = "string"
var b = new String("string")
a == b // true
a === b // false
```

<br>

## 엄격 모드 (Strict Mode)
ES5부터 도입된 기능으로 **기존에 무시되던 에러들로 하여금 에러를 발생시키게 한다.** 파일 전체에 적용시킬수도 있고 함수 스코프에 적용시킬수도 있지만, 블록 스코프는 불가능하다. 이를 통해 실수를 잡아낼 수 있고 안전하지 않은 것들을 예방할 수 있다.

### 엄격모드에 의해 에러가 발생하는 것
- `var`가 생략된 변수를 전역객체에 바인딩하지 않는다.
- 제거할 수 없는 프로퍼티를 제거할 수 없다. (`delete Object.prototype`)
- 함수의 매개변수 이름은 중복될 수 없다. (`function sum(x,x){}`)
- `NaN = 5` 같은 할당 구문은 불가능하다.
- `with` 키워드를 사용할 수 없다.
- 일반 변수를 삭제할 수 없다. (`delete x`)
- `arguments.callee` 를 사용할 수 없다.
- `arguments` 객체는 항상 원본 인자를 저장한다, 즉 매개변수를 바꿔도 `arguments` 의 값은 바뀌지 않는다.
- 8진수를 사용할 수 없다. (`var a = 013`)
- `eval` 은 새로운 변수를 스코프에 추가하지 않는다.

[엄격 모드 참고](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/javascript/strict-mode.md)
