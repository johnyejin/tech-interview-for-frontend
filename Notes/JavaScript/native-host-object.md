# 네이티브 객체 vs 호스트 객체
## 네이티브 객체
ESMAScript 명세에 정의된 객체. 애플리케이션 전역의 공통 기능을 제공한다. 네이티브 객체는 애플리케이션의 환경과 관계없이 언제나 사용할 수 있다. `Object`, `String`, `Number`, `Function`, `Array`, `RegExp`, `Date`, `Math` 등이 있다.

## 호스트 객체
호스트 객체는 호스트 환경에 정의된 객체를 말한다. 예를 들어, 브라우저에서 동작하는 환경과 브라우저 외부에서 동작하는 환경의 자바스크립트(node.js)는 다른 호스트 객체를 사용할 수 있다.

만약 브라우저 환경이라면 다음과 같은 것들이 존재한다. `window`, `document`, `location`, `XMLHttpRequest`, `querySelectorAll`,,,

<br>

## 참고
- [PoiemaWeb | Built-in Object](https://poiemaweb.com/js-built-in-object)
