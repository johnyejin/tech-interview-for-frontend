# height 속성
- height는 content 영역의 높이만을 의미한다. (margin, padding, border는 포함하지 않는다)
- `min-height`, `max-height`는 height 속성을 무시한다. 즉, height와 `min-height` 속성이 동시에 설정될 경우, `min-height` 값이 적용된다.

height 속성은 다음과 같은 값들을 갖는다.

### auto
기본값. 브라우저가 높이를 계산한다.

### max-content
최대한의 content 크기를 갖게 해준다. 텍스트 content의 경우 텍스트가 차지할 수 있는 최대의 공간은 모든 텍스트가 한 줄로 표현될 수 있는 공간이다. 오버플로우가 발생하더라도 부모에 의해 텍스트 content가 감싸지지 않는다. (그냥 오버플로우 되게 내버려 둔다)

![image](https://user-images.githubusercontent.com/26537048/112463548-bde5b400-8da5-11eb-97c5-efdaa69edeaf.png)


### min-content
최소한의 content 크기를 나타낸다. 텍스트 content의 경우 띄어쓰기 한 부분을 기준으로 줄바꿈된다. 즉, content를 유지하는 가장 최소의 공간을 갖는다.

![image](https://user-images.githubusercontent.com/26537048/112463603-cb9b3980-8da5-11eb-93ee-6904c6e4c025.png)


<br>

## 참고
- [blog | min-content, max-content, minmax 활용과 css grid의 auto-fit, auto-fill](https://justmakeyourself.tistory.com/entry/grid-extra)