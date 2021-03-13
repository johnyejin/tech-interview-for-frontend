# 모듈 시스템 (Module System)
모듈이란 여러 기능들에 관한 코드가 모여있는 하나의 파일로 다음과 같은 것들을 위해 사용한다.

#### 유지보수성
기능들이 모듈화가 잘 되어 있다면, 의존성을 그만큼 줄일 수 있기 때문에 어떤 기능을 개선한다거나 수정할 때 훨씬 편하게 할 수 있다.

#### 네임스페이스화
자바스크립트에서 전역변수는 전역공간을 가지기 때문에 코드의 양이 많아질수록 겹치는 네임스페이스가 많아질 수 있다. 그러나 모듈로 분리하면 모듈만의 네임스페이스를 갖기 때문에 문제를 해결할 수 있다.

#### 재사용성
똑같은 코드를 반복하지 않고 모듈로 분리시켜서 필요할때마다 사용할 수 있다.
<br>

이런 장점들을 살리기 위해 모듈 개념이 필요했고, 자바스크립트에선 모듈일 개발하기 위한 여러 시도들이 있었다. 그 중 CommonJS, AMD, UMD 및 ES6의 import&export가 대표적인 시도들이다.

## CommonJS
자바스크립트의 공식 스펙이 브라우저만 지원했기 때문에 이를 서버사이드 및 데스크탑 어플리케이션에서 지원하기 위한 노력이 있었다. 그걸 위해 만든 그룹이 CommonJS이며 여기선 자바스크립트가 범용적인 언어로 쓰이기 위한 스펙을 정의하고 있다.

다른 모듈을 사용할 때는 `require`를, 모듈을 해당 스코프 밖으로 내보낼 때에는 `module.exports`를 사용하는 방식으로, Node.js에선 현재 이 방식을 사용하고 있다.

## AMD
CommonJS 그룹에서 의견이 맞지 않아 나온 사람들이 만든 그룹으로, **비동기 모듈에 대한 표준안을 다루는 그룹**이다. CommonJS가 서버쪽에서 장점이 많은 반면, AMD는 브라우저 쪽에서 더 큰 효과를 발휘한다. 브라우저에서는 모든 모듈이 다 로딩될 때까지 기다릴 수 없기 때문에 비동기 모듈 로딩 방식으로 구현해놓았다.

이 방식에서 사용하는 함수는 `define()`과 `require()`이며 AMD 스펙을 가장 잘 구현한 모듈로더는 RequireJS 이다.

## UMD
모듈 구현 방식이 CommonJS와 AMD로 나뉘기 때문에 그걸 통합하기 위한 하나의 패턴이라고 할 수 있다.

통합하는 방식은 2개의 인자를 전달받는 함수를 실행하는 것으로, 첫번째 인자는 Browser 쪽을 구현할 root에 넘길 값으로 `undefined`이면 `this`로, 아니라면 `window`로 설정한다. 두번째 인자로는 빈 객체 리터럴을 리턴하는 함수를 보낸다.

이렇게 되면 각각의 환경에서 모두 모듈 개념을 사용할 수 있다.

## ES6 방식
import와 export 구문을 사용하는 방식이다. 모든 브라우저에서 지원하지 않기 때문에 Babel의 플러그인을 통해 변환시켜 사용한다.

### default 유무에 따른 사용법
export를 사용할 때는 `named export`와 `default export`를 사용할 수 있다. 단, `default export`는 모듈 내에서 한 번만 사용할 수 있고 `named export`는 여러 번 사용할 수 있다.

`default export`로 내보내면 import에선 내보낸 이름 그대로 바로 사용할 수 있지만, `named export`로 내보내면 `{}`로 묶어서 불러와야 한다.

### 또다른 사용법
별칭(alias)를 `as`로 주어서 다른 이름으로 사용할 수도 있고, `*` 와일드카드를 사용해 한 번에 불러오거나 내보낼 수도 있다. 이런 여러가지 변형기법의 사용은 [여기](https://velog.io/@doondoony/JavaScript-Module-System#-es6-modulesesm)를 참고하자.

- default export
```js
// moduleA.js
const A = () => {};
export default A;

// index.js
import A from 'moduleA';
```

- named export
```js
// moduleB.js
export const B = () => {};

// index.js
import { B } from 'moduleB';
```

## 참고
- [📦 JavaScript Module System](https://velog.io/@doondoony/JavaScript-Module-System#-es6-modulesesm)
- [모듈 시스템: CommonJS, AMD, UMD, ES6](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/javascript/module.md)
