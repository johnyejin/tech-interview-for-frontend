# Reflow, Repaint
- `reflow` : 생성된 DOM 노드의 레이아웃 수치(너비, 높이, 위치 등) 변경 시 영향 받은 모든 노드의 수치를 다시 계산하여 렌더 트리를 재생성하는 과정
- `repaint` : reflow 과정이 끝난 후 재생성된 렌더 트리를 다시 그리는 과정

<br>

## Reflow 발생

**Reflow가 일어나는 과정**

- Click 이벤트 handler
- Recalcurate(변경된 스타일 수치 계산 수행)
- Layout(Reflow 과정 수행)
- Paint(Repaint 과정 수행)

<br>

## Repaint 발생

Reflow 발생 이유와 같이 스타일의 모든 변경이 레이아웃 수치에 영향을 받는것은 아니다.

즉, 노드의 background-color, visibillty, outline 등의 스타일 변경 시에는 레이아웃 수치가 변경되지 않으므로 Reflow 과정이 생략된 Repaint 과정만 일어나게 된다.

**Repaint가 일어나는 과정**

- Click 이벤트 handler
- Recalcurate(변경된 스타일 수치 계산 수행)
- Paint(Repaint 과정 수행)

<br>

## **Reflow 과정이 일어나는 상황**

- 노드의 추가 또는 제거시
- 요소의 위치 변경 시
- 요소의 크기 변경 시 (margin, padding, border, width, height, 등..)
- 폰트 변경 과(텍스트 내용) 이미지 크기 변경 시 (크기가 다른 이미지로 변경 시)
- 페이지 초기 랜더링 시 (최초 Layout 과정)
- 윈도우 리사이징 시

<br>

## Reflow 최적화 방법

- **최대한 node 말단에 존재하는 DOM을 변경하도록 한다.**

- **인라인 스타일을 최대한 배제하자.**

- **애니메이션이 들어간 요소는 가급적 position:fixed, position:absolute를 사용하여 전체 노드에서 분리하여 관리한다.**

  보통 (JS(Javascript) + CSS)를 활용한 에니메이션 효과는 해당 프레임에 따라 무수히 많은 Reflow 비용이 발생하게 된다. 하지만 position 속성을 "fixed" 또는 "absoute"로 값을 주면 지정된 노드는 전체 노드에서 분리된다.
  즉, 전체 노드에 걸쳐 Reflow 비용이 들지 않으며, 해당 노드의 Repaint 비용만 들어가게 된다. 또한, 노드의 position 값을 초기에 적용하지 않았더라도 에니메이션 시작 시 값을 변경(fixed, absolute)하고 종료 시 다시 원복 시키는 방법을 사용해도 무관하다.

- **테이블 레이아웃을 피하자.**

  테이블로 구성된 페이지 레이아웃은 점진적(progressive) 페이지 렌더링이 적용되지 않으며, 모두 로드되고 계산(Recalculate)된 후에야 화면에 뿌려지게 된다.
  하지만 해당 테이블에 table-layout:fixed 속성을 주는 것이 디폴트값인 auto에 비해 성능면에서 더 좋다고 한다.

- **CSS에서의 JS 표현식을 피하자.**

  CSS 표현식(expression)의 비용이 매우 높은 이유는, 문서 전체 또는 문서 중 일부가 Reflow될 때마다 표현식이 다시 계산되기 때문이다.
  결국 애니메이션과 같은 변화에 의해 리플로우가 발생했을 때, 경우에 따라 초당 수천, 수만번의 표현식 계산이 진행될 수 있다는 것을 의미한다.

  ```css
  // css 표현식 예시
  .expression { 
    width: expression(document.documentElement.clientWidth > 0 ? '1000px' : 'auto'); 
  }
  ```

- **JS를 통해 스타일변화를 주어야 할 경우, 가급적 한번에 처리하라.**

  ```jsx
  function collect() { 
    var elem = document.getElementById('container'); 
    elem.style.cssText = 'background:red;width:200px;height:200px;'; 
    return false; 
  }

  // or

  function collect() { 
    var elem = document.getElementById('container'); 
    elem.className = 'collect'; 
    return false; 
  }
  ```

<br>

## 참고
- [blog | Reflow 원인과 마크업 최적화 Tip](https://zinee-world.tistory.com/295)
- [blog | Reflow or Repaint(or ReDraw)과정 설명 및 최적화 방법](https://webclub.tistory.com/346)
