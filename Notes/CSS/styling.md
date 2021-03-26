# 스타일링 방식
리액트에서는 컴포넌트를 스타일링할 때 다양한 방식을 사용할 수 있다. 그 중 자주 사용하는 Sass와 styled-components에 대해 알아볼 것이다.

<br>

## Sass(Scss)
Sass(Syntactically Awesome Style Sheets)는 CSS pre-processor로서, 다음과 같은 장점을 갖고 있다.

- 복잡한 작업을 쉽게 할 수 있게 해준다.
- 코드의 재활용성을 높여준다.
- 코드의 가독성을 높여줘 유지보수를 쉽게 해준다.

Sass에서는 두가지 확장자 .scss/.sass를 지원한다. 그중 Scss는 Sass 세번째 버전에서 추가되었는데, Sass의 모든 기능을 지원하면서 CSS 구문과 완전히 호환되도록 만들어졌다.

### Scss 특징
#### 부모 요소를 반복적으로 기술하지 않고 사용할 수 있다. (nesting)
```scss
// CSS
.wrapper {
    width: 100%;
    height: 100%;
}
.wrapper div {
    width: 500px;
    height: 200px;
}
.wrapper div span {
    background-color: blue;
}

// SCSS
.wrapper {
    width: 100%;
    height: 100%;
    div {
        width: 500px;
        height: 200px;
        span {
            background-color: blue;
        }
    }
}
```

#### `$` 변수를 사용해 공통된 속성을 재활용할 수 있다.
```scss
$font-color: red;
.content {
    color: $font-color;
    float:left;
    .title {
        color: $font-color;
        font-size: 18px;
    }
}
```

#### mixin을 사용하면 공통된 속성의 묶음을 재활용할 수 있다.
```scss
@mixin box-style {
    width: 100px;
    height: 50px;
    background-color: red;
}
.section {
    position: absolute;
    top: 0;
    .box {
        @include box-style;
    }
}
```

#### import 기능을 활용해 코드를 여러 파일로 나눌 수 있다.
```scss
// style.scss
@import 'header';
@import 'aside';
@import 'footer';
...
```

#### 조건문, 반복문을 사용할 수 있다.
```scss
// if
$num: two;
div {
  @if $num == one {
    color: blue;
  } @else if $num == two {
    color: red;
  } @else {
    color: black;
  }
}

// .css (..compile)
div{
    color: red;
}

// for
@for $i from 1 through 3 {
  .item-#{$i} { 
    width: 2em * $i; 
  }
}
```

### 단점
- 전처리기를 위한 도구가 필요하다.
- 컴파일 시간이 길어진다.

<br>

## styled-components
styled-components는 현존하는 리액트 css-in-js 라이브러리 중에서 가장 잘나가는 라이브러리이다. css-in-js는 자바스크립트 파일 내에서 스타일을 관리할 수 있도록 해준다.

### 장점
- 하나의 자바스크립트 파일 안에 스타일까지 작성할 수 있기 때문에 .css/.scss 파일 같은걸 만들 고민은 안해도 된다.
- 스타일링한 컴포넌트에 전달하는 props 값을 스타일쪽에서 그대로 사용할 수 있어 **props에 따라 조건부 스타일링이 가능**하다.
- **컴파일시 클래스명을 자동으로 생성**해주기 때문에 클래스명이 겹치는 문제가 발생하지 않는다. (클래스명에 대한 고민을 덜어줄 수 있다)
- **css를 컴포넌트화**할 수 있어 재사용성이 높아지고, 대규모 애플리케이션에서 css가 복잡해지는 문제를 해결할 수 있다.

<br>

## CSS 전처리기 vs styled-components
### 클래스명
css 전처리기는 nesting이 가능해 가독성과 디버깅이 용이하지만, 클래스명에 대한 고민을 해야한다.

하지만 css-in-js 방식은 컴파일시 클래스명을 자동으로 생성해주기 때문에 클래스명에 대한 고민을 하지 않아도 된다.

### 성능 차이
css 전처리기는 html 문서에서 이미 읽혀져 있는 상태이기 때문에 처음 스타일 정보를 가져오는 양이 많더라도 그 이후에 추가적인 렌더링은 상대적으로 적다.

하지만 css-in-js 방식은 해당 컴포넌트가 렌더링될 때에만 해당 스타일 정보를 일기 때문에 그 컴포넌트가 렌더링될 때마다 스타일 정보를 가져와야 한다. 따라서 동적인 이벤트가 많은 사이트라면 그만큼 컴포넌트의 리렌더링이 자주 발생해, 스타일 정보를 그때그때 다시 읽어와야 해서 성능 상의 이슈가 생길 수 있다.

<br>

## 참고
- [medium | SASS/SCSS (전처리기)](https://jinminkim-50502.medium.com/css-preprocessor-sass-scss-25dc8329f867)
- [velopert | 다양한 방식의 리액트 컴포넌트 스타일링 방식 CSS, Sass, CSS Module, styled-components](https://velog.io/@velopert/react-component-styling)