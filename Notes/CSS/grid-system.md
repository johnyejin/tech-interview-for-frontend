# 그리드 시스템
그리드 레이아웃을 구현하기 위해 설계한 시스템으로 너비 960px 혹은 1200px를 기준으로 정해놓은 시스템들이 있다. 열의 개수에 따라 12단/16단/24단 그리드라고 부른다. 그리드 레이아웃을 구현하는 방법은 여러가지가 있는데 그중 `float`, `flexbox`, `grid`에 대해 알아볼 것이다.

<br>

## Float grid system
flexbox나 grid가 나오기 이전에 사용하던 방식으로 float 속성을 사용해 구현한다. float된 높이를 잡기 위해 clearfix 핵을 사용해야 하며, 각 너비를 열/행의 간격에 맞게 계산해주어야 한다.

> 💡 **clearfix란?**<br>
> HTML 문서 구조에서 부모 요소가 자식 요소를 감싸고 있을 때, 자식 요소에게 float 형식을 적용하면 부모 요소가 자식 요소를 더 이상 감싸지 않게되고 높이 값을 파악하지 못하게 되는 버그가 발생한다. 따라서 부모 요소의 높이 값이 0px로 출력되고, 전체적인 HTML 요소들이 뒤엉켜버리는 경우가 많다. <br> 
> 이때 부모 요소가 다시 자식 요소를 감쌀 수 있게 float을 초기화(clear) 하여 버그를 고쳐주는(fix) 코드가 필요한데 이것을 clearfix라고 한다.

<br>

## Flexbox grid system
대부분 float를 사용한 방식과 동일하되, clearfix 핵을 없애고 flex를 적용한 것이다.

<br>

## Gird layout grid system
grid를 사용한 경우로, flat/flexbox와는 완전히 다르다. 너비를 계산하지도 않고 열/행을 따로 지정하지 않는다. 단순하게 grid 관련 속성을 사용해 열/행의 너비 및 높이와 각 항목의 비율을 지정한다.

<br>

## 참고
- [github | 그리드 시스템](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/css/grid.md)
- [flexbox froggy](http://flexboxfroggy.com/#ko)