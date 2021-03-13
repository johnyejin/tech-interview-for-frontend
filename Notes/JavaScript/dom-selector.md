# DOM 객체
## DOM 선택자
- `querySelector` : css 선택자를 기준으로 제일 첫번째 엘리먼트를 반환한다.
- `querySelectorAll` : css 선택자에 대응하는 모든 요소를 반환한다.
- `getElementById` : dom에서 특정 id 값을 가진 엘리먼트를 반환한다.
- `getElementByClassName` : 특정 class명을 가진 엘리먼트들을 담은 컬렉션을 반환한다.
- `getElementByName` : name에 명시된 조건에 맞는 모든 값들을 담은 컬렉션을 반환한다.
- `getElementByTagName` : 특정 태그명을 가진 엘리먼트들을 담은 컬렉션을 반환한다.

`getElementByClassName`, `getElementByName`, `getElementByTagName` 메서드는 '살아있는 컬렉션'을 반환한다. 즉, 문서에 변경이 있을 때마다 컬렉션이 자동으로 갱신되어 최신 상태를 유지한다.

## getElementBy* vs querySelector 속도 차이
getElementBy*이 querySelector보다 처리속도가 더 빠르다.

## 참고
- [getElement*, querySelector*로 요소 검색하기](https://ko.javascript.info/searching-elements-dom)
