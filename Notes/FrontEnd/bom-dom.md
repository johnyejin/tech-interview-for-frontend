# BOM과 DOM
## BOM (Browser Object Model)
- **브라우저의 창이나 프레임을 프로그래밍적으로 제어할 수 있게 해주는 객체 모델**이다. 이를 통해서 브라우저의 새 창을 열거나 다른 문서로 이동하는 등의 기능을 실행시킬 수 있다.
- 전역객체로 `window`가 있으며 하위 객체들로 `location`, `navigator`, `document`, `screen`, `history`가 포함되어 있다.

![BOM](https://user-images.githubusercontent.com/26537048/111450317-9c584d00-8753-11eb-9b0e-87e29387e5b5.png)


<br>

## DOM (Document Object Model)
- 사전적 정의는 객체지향 모델로써 구조화된 문서를 표현하는 방식이다.
  - 쉽게 말하면.. 브라우저가 웹 문서를 이해할 수 있도록 구성된 것을 DOM 이라고 한다.
  - 즉, 모든 요소들과의 관계를 부자 관계로 표현할 수 있는 트리 구조로 구성한 것이 DOM 이다.
-  DOM 은 웹 페이지의 객체 지향 표현이며, 자바스크립트와 같은 스크립팅 언어를 이용해 DOM 을 수정할 수 있다.
- 최상위 인터페이스로 `Node`가 있으며 하위 객체들로 `Document`, `CharacterData`, `Element`, `Attr` 가 포함되어 있다.
- 이런 DOM을 다루기 위해선 `getElementsById` , `querySelector` , `firstElementChild` 등과 같은
브라우저가 제공하는 **DOM API**를 사용하면 된다.

<br>

DOM 트리 구조에서 주로 쓰이는 노드 4종류이다.

| Node | Description |
| --- | :--- |
| Document Node | 트리의 최상위에 존재하며 각각의 하위요소들(element, attribute, text 노드)에 접근하려면 문서노드를 통해야 한다. 즉, 시작점이다. |
| Element Node | 쉽게 말해 태그이다. `<p>`, `<span>`, `<div>` 등 |
| Attribute Node | `<input>` 태그 안에는 name, value 등의 속성을 사용할 수 있는데, 이러한 속성들을 가리키는 노드이다. |
| Text Node | 태그 내 텍스트를 표현한다. 텍스트 노드는 엘리먼트 노드의 자식이며 자신의 자식 노드를 가질 수 없기 때문에 돔 트리의 최종단이다. `<span>안녕</span>`일 경우 텍스트 노드는 '안녕'이다. |

<br>

![DOM](https://user-images.githubusercontent.com/26537048/111450398-aed28680-8753-11eb-901e-70534c43ccad.png)

위의 트리구조를 보면 엘리먼트 뿐만 아니라 텍스트와 주석도 있는 것을 알 수 있는데, 이런 것들까지도 DOM 트리에 포함된다. 실제적인 DOM 트리는 아래와 같이 생성된다.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>제목</title>
  </head>
  <body>
  <div class="클래스"></div>
  <!-- 주석 -->
  <a href="https://naver.com">네이버</a>
  </body>
</html>
```

![DOM Tree](https://user-images.githubusercontent.com/26537048/111450555-d9bcda80-8753-11eb-8d1a-c47316a8c0e5.png)

👆 [Live DOM Viewer](https://software.hixie.ch/utilities/js/live-dom-viewer/) 를 사용해서 DOM 트리를 구성해 본것으로, 엘리먼트 뿐만 아니라 텍스트 노드와 주석 노드까지 포함하고 있다.

<br>

## 참고
- [Gihub | BOM과 DOM](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/frontend/bom-dom.md)
- [Window, DOM, BOM이란?](https://cbw1030.tistory.com/46)
