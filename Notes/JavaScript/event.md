# JavaScript 이벤트
## 이벤트 등록 및 해제
### 이벤트 등록
addEventListener로 이벤트를 등록할 수 있다. 같은 요소의 같은 이벤트에 여러 개의 이벤트 리스너를 등록할 수 있다.

### 이벤트 제거
removeEventListener로 이미 등록한 이벤트 리스너 중 동일한 인자를 받는 이벤트 리스너를 삭제한다.

이벤트를 제거하기 위해 세가지 값이 필요하다.
1. 제거할 엘리먼트 요소
2. click, keypress 등의 이벤트 타입
3. 제거할 이벤트 콜백 함수

<br>

## 이벤트 버블링과 캡처링
이벤트 버블링, 캡쳐링은 **브라우저가 이벤트를 감지하는 방식**이다.

### 이벤트 버블링
하위 엘리먼트에서 상위 엘리먼트로 이벤트가 전파되는 특성을 말한다. 브라우저는 특정 화면 요소에서 이벤트가 발생했을 때, 그 이벤트를 최상위에 있는 화면 요소까지 이벤트를 전파시킨다.

### 이벤트 캡처링
버블링과 반대방향으로 진행되는 이벤트 전파 방식이다. 해당 기능은 `addEventListener()` API에서 옵션 객체에 `capture:true`를 설정해주면 구현할 수 있다.

<br>

## 이벤트 위임 (Event Delegation)
**하위 요소에 각각 이벤트를 붙이지 않고 상위 요소에서 하위 요소의 이벤트들을 제어하는 방식**이다. 리스트 아이템이 많아지면 많아질수록 이벤트 리스너를 다는 작업 자체가 매우 번거롭다. 이 번거로운 작업을 해결할 수 있는 방법이 바로 이벤트 위임이다.

<br>

## stopPropagation vs preventDefault
### stopPropagation()
이벤트 버블링이나 캡쳐링 같은 이벤트가 전파되는 것을 막아주는 api이다. 이벤트 버블링의 경우에는 클릭한 요소의 이벤트만 발생시키고 상위 요소로 이벤트를 전달하는 것을 방해한다.

이벤트 캡쳐의 경우에는 클릭한 요소의 최상위 요소의 이벤트만 동작시키고 하위 요소들로 이벤트를 전달하지 않는다.

### preventDefault()
현재 이벤트의 기본 동작을 중단시키기 위해 사용한다. 예를들어 a 태그에 클릭이벤트를 달고 콜백함수에 preventDefault를 사용하게 되면 a 태그의 href 속성이 중단된다.

<br>

## 참고
- [이벤트 버블링, 이벤트 캡처 그리고 이벤트 위임까지](https://joshua1988.github.io/web-development/javascript/event-propagation-delegation/)