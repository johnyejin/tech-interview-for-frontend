# Promise
자바스크립트 비동기 처리에 사용되는 객체이다. 콜백 지옥을 해결하기 위해, 비동기적인 일련의 작업을 동기적으로 혹은 동기적인 것처럼 보이게 해주기 위해 등장한 것이 promise이다.

promise 패턴을 사용하면 비동기 작업들을 순차적으로 실행하거나, 병렬로 진행하는 등의 작업이 수월해진다. 또한, 예외처리에 대한 구조가 존재하기 때문에 오류 처리를 보다 가시적으로 관리할 수 있다.

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

<br>

## promise가 필요한 이유
promise는 주로 서버에서 받아온 데이터를 화면에 표시할 때 사용한다. 서버에 요청을 보냈는데 데이터를 받아오기도 전에 마치 데이터를 받아온 것처럼 화면에 표시하려고 한다면, 오류가 발생하거나 빈 화면이 뜨게 된다. 이와 같은 문제점을 해결하기 위한 방법 중 하나가 promise이다.
