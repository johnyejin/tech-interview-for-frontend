# CSR vs SSR
## SPA와 MPA
#### SPA (Single Page Application)
하나의 HTML 파일을 기반으로 자바스크립트를 이용해 동적으로 화면의 컨텐츠를 바꾸는 방식의 웹 어플리케이션이다.

#### MPA (Multiple Page Application)
사용자가 페이지를 요청할 때마다, 웹 서버가 요청한 UI와 필요한 데이터를 HTML로 파싱해서 보여주는 방식의 웹 어플리케이션이다.
<br>
전통적인 방식을 이용한다면, SPA가 사용하는 렌더링 방식은 CSR이고, MPA가 사용하는 렌더링 방식은 SSR이다. 각 방식의 동작방식과 장단점을 알아보자.

<br>

## CSR (Client Side Rendering)
CSR은 최초 한 번 페이지 전체를 로딩한 이후부터는 데이터만 변경하여 사용하는 방식이다. 서버는 단지 JSON 파일만 보내주는 역할을 하고, HTML을 그리는 역할은 클라이언트 측에서 자바스크립트가 수행하는 것이다.

![CSR](https://user-images.githubusercontent.com/26537048/111436328-31077e80-8745-11eb-804e-52be17d6013f.png)

### 👍 장점
- 첫 로딩만 기다리면, 동적으로 빠르게 렌더링되기 때문에 사용자 경험(UX)가 좋아진다.
- 서버에 요청하는 횟수가 훨씬 적기 때문에 서버의 부담이 덜하다.

### 👎 단점
- 모든 스크립트 파일이 로드될 때까지 기다려야 하기 때문에 **초기 구동 속도가 느리다.**
- 검색엔진의 검색 봇이 크롤링을 하는데 어려움을 겪기 때문에 **검색엔진 최적화의 문제가 있다.**
  <!-- - Chrome에서 React로 만든 웹앱 소스를 확인하면 내용이 비어있는데, 이처럼 검색엔진 크롤러가 데이터를 수집하는데 어려움이 있을 수 있다. -->
  - 구글 검색엔진은 자바스크립트 엔진이 내장되어 있지만, 네이버나 다음 등 대부분의 웹 크롤러들은 자바스크립트 파일을 실행시키지 못한다. 때문에 HTML에서만 콘텐츠를 수집하게 되고 CSR되는 페이지를 빈 페이지로 인식하게 된다.

<br>

## SSR (Server Side Rendering)
브라우저가 페이지를 요청할 때마다 해당 페이지에 관련된 HTML, CSS, JavaScript 파일 및 데이터를 받아와 렌더링하는 방식이다.

![SSR](https://user-images.githubusercontent.com/26537048/111436424-4f6d7a00-8745-11eb-80c2-87347e57922d.png)

### 👍 장점
- 자바스크립트를 이용한 렌더링이 아니기 때문에 검색엔진 최적화가 가능하다.
- 초기 로딩 속도를 줄일 수 있다.

### 👎 단점
- 매번 페이지를 요청할 때마다 새로고침되기 때문에 사용자 경험이 SPA에 비해 좋지 않다.
- 서버에 매번 요청을 하기 때문에 서버의 부하가 커진다.

<br>

## 참고
- [Tistory | SSR 그리고 CSR](https://asfirstalways.tistory.com/244)
- [Medium | The Benefits of Server Side Rendering Over Client Side Rendering](https://medium.com/walmartglobaltech/the-benefits-of-server-side-rendering-over-client-side-rendering-5d07ff2cefe8)
