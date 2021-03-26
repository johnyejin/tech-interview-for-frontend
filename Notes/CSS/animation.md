# CSS 애니메이션과 JavaScript 애니메이션
웹사이트에 애니메이션 효과를 부여할 때 CSS의 `transition`, `animation` 속성을 사용할 수 있고, JavaScript의 `setInterval()`, `requestAnimationFrame()`을 사용할 수 있다. 하지만 각각을 사용할 때의 특징이 다르고 장단점이 있기 때문에 환경에 맞게 사용하는 것이 중요하다.

<br>

## CSS 애니메이션
마우스를 올렸을 때 혹은 메뉴 버튼의 전환과 같은 간단하게 처리하는 애니메이션의 경우 CSS로 처리한다. 간단한 애니메이션을 JavaScript로 구현하는 경우 브라우저의 렌더링 과정에서 reflow를 발생시키기 때문에 애니메이션이 부자연스럽게 끊기는 듯한 느낌을 받을 수 있다.

### 장점
- 반응형으로 애니메이션을 구현할 때 유용한데, 미디어 쿼리로 애니메이션을 적용하면 된다.
- 외부 라이브러리를 필요로 하지 않는다.
- CSS 자체가 선언형이기 때문에, 어떤 요소가 애니메이션을 가져야 한다는 직관적인 표현이 가능하다.
- 메인 스레드가 아닌 별도의 컴포지터 스레드(Compositor Thread)에서 그려지기 때문에 메인 스레드에서 작업하는 JavaScript보다 효율적이다.

<br>

## JavaScript 애니메이션
CSS로 처리하기에는 훨씬 복잡하고 무거운 애니메이션 작업들을 효율적이고, 세밀하게 다루기 위해 사용한다.

### 장점
- 요소의 스타일이 변하는 순간마다 제어할 수 있기 때문에 애니메이션의 세밀한 구성이 가능해진다.
- GPU를 통한 하드웨어 가속을 제어할 수 있다. 이는 CSS의 특정 속성으로 인한 가속을 막아주는데, 하드웨어 가속이 모바일에서 성능저하를 발행시킬 수 있기 때문에 이런 면에선 좋다.
- 브라우저 호환성 측면에서 `transition`, `animation` 속성보다 뛰어나다.

> 💡 하드웨어 가속을 발생시키는 것 : `opacity`, `transform`

<br>

## 참고
- [github | CSS 애니메이션 vs JS 애니메이션](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/frontend/css-js-animation.md)