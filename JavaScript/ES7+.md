# ES7(2016) ~ ES11(2020)

## ES7
- Array.prototype.includes
- exponentiation (2 ** 2)

## ES8
- async/await
- Object.entries()
- Object.values()
- Object.getOwnPropertyDescriptors()

## ES9
- async 반복자
- Object rest/spread 문법
- Promise.prototype.finally -> 무조건 실행

## ES10
- Array.prototype.flat()/flatMap()
- Object.fromEntries() -> 배열로부터 객체를 만듦
- String.prototype.trimStart()/trimEnd() -> 앞뒤 공백 지우기
- Symbol.prototype.description
- catch의 에러 인자 생략 가능

## ES11
- String.prototype.matchAll
- Dynamic import
- BigInt
- Promise.allSettled
- Optional Chaining -> `?.`를 사용해 프로퍼티의 존재 여부 확인
- [null 병합 연산자](#null-병합-연산자)

## null 병합 연산자
보통 기본값을 할당하기 위해 `||`를 사용하여 좌변이 null이나 undefined면 다른 값을 사용하는 방식을 많이 사용했다. 이를 `??`로 해결하였다.

```js
const values = {
  nullValue: null
};

const value = values.nullValue ?? "default value";
```
