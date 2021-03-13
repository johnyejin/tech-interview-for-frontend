# this
자바스크립트는 해당 **함수의 호출 방식에 따라** this에 바인딩되는 객체가 달라진다. 즉, 함수를 선언할 때 this에 바인딩할 객체가 정적으로 결정되는 것이 아니라 함수를 호출할 때 함수가 어떻게 호출되었는지에 따라 this에 바인딩할 객체가 동적으로 결정된다.

## this의 규칙
1. 전역 공간에서의 this는 전역 객체를 참조한다.
2. 어떤 함수를 메서드로서 호출한 경우, this는 메서드 호출 주체(메서드명 앞의 객체)를 참조한다.
3. 어떤 함수를 함수로서 호출한 경우, this는 전역객체를 참조한다. 메서드의 내부 함수에서도 같다.
4. 콜백 함수 내부에서의 this는 해당 콜백 함수의 제어권을 넘겨받은 함수가 정의한 바에 따르며, 정의하지 않은 경우에는 전역객체를 참조한다.
5. 생성자 함수에서의 this는 생성될 인스턴스를 참조한다.
6. apply, call, bind가 함수의 호출/생성에 사용된 경우, 함수 내의 this는 인수로 전달된 객체이다.

### 2번 규칙
객체의 메서드로 호출할 경우, 해당 객체에 바인딩된다.
```js
var obj = {
  name: 'obj name',
  print: function p() { console.log(this.name); }
};
obj.print(); // obj name
```

### 5번 규칙
`new`를 사용했을 때 해당 객체로 바인딩된다.
```js
var name = "global";
function Func() {
  this.name = "Func";
  this.print = function f() { console.log(this.name); };
}
var a = new Func();
a.print(); // Func
```


## 일반 함수와 화살표 함수에서 this의 차이
**일반 함수**의 경우 this는 전역 객체에 바인딩되고, **화살표 함수**의 경우 함수가 생성된 시점에서 주변 스코프의 this 값을 받는다.
**화살표 함수**는 this를 바인딩하지 않기 때문에, 상위 스코프의 this를 그대로 활용할 수 있다.


## 명시적 this 바인딩
### call 메서드
- 메서드의 호출 주체인 함수를 즉시 실행하도록 하는 명령
- 첫번째 인자를 this로 바인딩하고, 이후의 인자들을 호출할 함수의 매개변수로 한다.

### apply 메서드
- call과 기능적으로 완전 동일
- 차이점이 있다면 두번째 인자를 배열로 받아, 그 배열의 요소들을 호출할 함수의 매개변수로 지정한다.

### bind 메서드
- call과 비슷하지만, **함수를 즉시 호출하지는 않고 넘겨받은 this 및 인수들을 바탕으로 새로운 함수를 반환**하기만 하는 메서드
- 다시 새로운 함수를 호출할 때 인수를 넘기면, 그 인수들은 기존 bind 메서드를 호출할 때 전달했던 인수들의 뒤에 이어서 등록된다.

```js
function func() {
  console.log(this.name);
}

var obj = { name: 'obj name' };
func.call(obj); // obj name
func.apply(obj); // obj name
(func.bind(obj))(); // obj name
```
