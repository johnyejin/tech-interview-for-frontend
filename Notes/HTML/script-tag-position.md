# script 태그의 위치
HTML에서 `<script>` 태그는 어느 위치에나 올 수 있다. 그러나 브라우저는 HTML의 구조와 CSS 스타일을 렌더링하는 도중 자바스크립트를 만나게 되면 이에 대한 해석과 구현이 완료될 때까지 브라우저 렌더링을 멈추게 되는데, 이때 **프리징 현상**이 발생할 수 있다.

즉, **`<head>` 태그 안에 `<script>` 태그를 넣으면 DOM이 해석되는 도중에 스크립트를 읽기 때문에 장시간 완성되지 못한 화면을 노출할 수 있다.** 또한, DOM 구조가 완성되지 않았기 때문에 **특정 엘리먼트의 참조가 실패할 수 있다.**

따라서, 적절한 `<script>` 태그의 위치는 `<body>` 태그의 최하단이다.
