# TypeScript
타입스크립트는 자바스크립트에 타입을 부여한 언어이다. 자바스크립트의 확장된 언어라고 볼 수 있다. 또한, 타입스크립트는 런타임 이전에 정적으로 타입을 검사할 수 있는 자바스크립트이다.

<br>

## 장단점
### 장점
- 에러의 사전 방지
- 코드 자동완성 -> 개발 생산성 향상
- 개발 커뮤니티 활성화
- 절차지향, 객체지향, 함수형 등 여러가지 패러다임 활용 가능

### 단점
- 초반 환경 설정이 불편하다.
- 코드의 길이가 길어지기 때문에 자바스크립트에 비해 가독성이 떨어진다.
- 타입 에러를 해결한다해도 자바스크립트의 고질적인 에러는 계속 발생할 수 있다.

<br>

## 왜 타입스크립트를 써야할까?
타입스크립트는 아래 2가지 관점에서 자바스크립트 코드의 품질과 개발 생산성을 높일 수 있다.

### 에러의 사전 방지
타입스크립트는 에러를 사전에 미리 예방할 수 있다.

```ts
// math.ts
function sum(a: number, b: number) {
  return a + b;
}
sum('10', '20'); // Error: '10'은 number에 할당될 수 없습니다.
```
위의 코드처럼 의도하지 않은 코드의 동작을 예방할 수 있다.


### 코드 가이드 및 자동 완성
타입스크립트의 또 다른 장점은 코드를 작성할 때 개발 툴의 기능을 최대로 활용할 수 있다는 것이다. 요즘에 프런트엔드 개발을 할 때 가장 많이 사용되는 Visual Studio Code는 툴의 내부가 타입스크립트로 작성되어 있어 타입스크립트 개발에 최적화 되어 있다.

```ts
function sum(a: number, b: number): number {
  return a + b;
}
var total = sum(10, 20);
total.toLocaleString();
```

위의 sum 함수를 자바스크립트로 작성하면 `total` 변수의 타입이 정해져있지 않기 때문에 Number 자료형에서 제공하는 API인 `toLocaleString()`을 일일이 작성해야 한다. 만약 오탈자라도 나서 `toLocalString()` 이라고 했다면 브라우저에서 실행했을 때만 오류를 확인할 수 있을 것이다.

하지만 타입스크립트로 작성하면 `total` 변수의 타입이 number로 지정되기 때문에 VSCode에서 해당 타입에 대한 API를 미리 보기로 띄워줄 수 있고 따라서 API를 일일이 치는 것이 아니라 tab으로 빠르고 정확하게 작성해나갈 수 있다.


<br>

## 참고
- [캡틴판교 | 타입스크립트 핸드북 - Why typescript?](https://joshua1988.github.io/ts/why-ts.html#%EC%99%9C-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%A5%BC-%EC%8D%A8%EC%95%BC%ED%95%A0%EA%B9%8C%EC%9A%94)
- [달달한 제안, TypeScript](https://jbee.io/typescript/you_might_need_typescript/)
