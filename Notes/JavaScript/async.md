# JavaScript 비동기 처리
자바스크립트의 비동기 처리란 특정 코드의 연산이 끝날 때까지 코드의 실행을 멈추지 않고 다음 코드를 먼저 실행하는 자바스크립트의 특성을 의미한다.

예를 들어, 서버에 데이터를 요청하는 경우 서버가 요청에 대한 응답을 줄때까지 마냥 기다릴 수 없어 비동기 처리가 필요하다. 즉시 처리하지 못하는 이벤트들을 web api를 이용해 콜백큐로 보내고, 이벤트 루프를 통해 콜스택이 비었을 경우 콜백 함수들을 실행한다.

<br>

## 비동기 작업의 과정
자세한 내용은 이벤트 루프에서 다룰 것이다.

1. 코드가 실행되면 call stack에 쌓이고 마지막으로 들어온 코드부터 실행된다.
2. 비동기 함수가 실행되면 web api가 호출된다.
3. web api는 비동기 함수의 콜백 함수를 callback queue에 넣는다.
   - `promise`는 microtask queue로, `timeout`은 task queue로, `requestAnimationFrame`은 animation frame으로 콜백 함수를 넣는다.
   - 콜백 이동 우선순위는 microtask > animation > task queue 이다.
4. event loop는 call stack이 빈 상태가 되면 콜백을 call stack으로 이동시킨다.

<br>

## 비동기 에러 처리
- response가 ok일 때만 정상 데이터가 리턴된다.
- 에러 발생 시 단순히 Error 객체를 던지기보단 공통된 에러 처리가 가능한 객체로 내려주면 받는 쪽에서 에러 처리를 하기 더욱 쉬워진다.

```js
{
	isError: true,
	errorData: {
		message: errorData.message,
		statusCode: response.status,
	},
}
```
이런 방식으로 에러 객체를 리턴해주면 상태 코드에 관계 없이 혹은 HTTPError 같은 특정 에러 객체에 관계 없이 이미 정의해놓은 인터페이스에 맞는 객체가 리턴된다는 것을 보장할 수 있다.

<br>

## 비동기 처리 방법
- [promise](promise.md)
- async/await
- [generator](ES6.md)

### async/await
ES8(2017)에서 나온 비동기 코드를 작성하는 새로운 방법이다. promise의 단점을 보완하고 가독성있는 코드를 작성할 수 있게 도와준다.

function 키워드 앞에 `async`를 붙여주고 function 내부의 promise를 반환하는 비동기 처리 함수 앞에 `await`을 붙여준다.

### promise vs async/await
- promise는 then과 catch를 사용해 에러 처리를 하는 반면, async/await은 try-catch 문을 활용해 에러 처리를 할 수 있다.
- async/await을 사용하면 promise보다 간결하고 가독성있게 코드를 작성할 수 있다.

<br>

## 참고
- [비동기 처리 과정 - 이벤트 루프](https://velog.io/@thms200/Event-Loop-%EC%9D%B4%EB%B2%A4%ED%8A%B8-%EB%A3%A8%ED%94%84)
- [비동기 에러 처리](https://rinae.dev/posts/how-to-handle-errors-1)
