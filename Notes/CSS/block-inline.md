# block vs inline

## block
1. 줄바꿈이 된다.
2. margin과 padding 속성을 사용할 수 있다.
3. width, height 속성을 사용할 수 있다.

## inline
1. 줄바꿈이 안된다.
2. 상하 margin과 padding 속성을 사용할 수 없다.
3. width, height 속성을 사용할 수 없다.

<br>

## block vs inline vs inline-block

| 특징                         | block              | inline             | inline-block       |
| ---------------------------- | ------------------ | ------------------ | ------------------ |
| 상하 마진/패딩               | :white_check_mark: | :x:                | :white_check_mark: |
| 좌우 마진/패딩               | :white_check_mark: | :white_check_mark: | :white_check_mark: |
| 요소 사이 줄바꿈             | :white_check_mark: | :x:                | :x:                |
| 기본너비가 부모너비          | :white_check_mark: | :x:                | :x:                |
| 요소 사이 공백               | :x:                | :white_check_mark: | :white_check_mark: |
| 너비와 높이 명시했을 때 적용 | :white_check_mark: | :x:                | :white_check_mark: |

<br>

![image](https://user-images.githubusercontent.com/26537048/112465013-8e37ab80-8da7-11eb-97dd-3bdf4a305821.png)

inline-block은 요소들이 한 줄에 위치하지만, block 요소처럼 행동한다.

<br>

## 참고
- [github | block vs inline vs inline-block](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/css/block-inline-inline-block.md)
- [Stackoverflow | CSS display: inline vs inline-block](https://stackoverflow.com/questions/9189810/css-display-inline-vs-inline-block)