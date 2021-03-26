# REST API
REST API에 대해 알기 전, REST와 API에 대해 먼저 알아보자.

## REST란?
REpresentational State Transfer의 약자로 전반적인 웹 어플리케이션에서 상호작용하는데 사용되는 웹 아키텍쳐 모델이다. 즉, **자원을 주고받는 웹 상에서의 통신 체계에 있어 범용적인 스타일을 규정한 아키텍쳐**라고 할 수 있다.

## API란?
Application Programming Interface의 약자로 구글 맵 API, 카카오 Vision API 등 **기존에 있는 응용 프로그램을 통해서 데이터를 제공받거나 기능을 사용하고자 할 때 사용하는 인터페이스 및 규격**을 말한다. API는 프로그래밍 언어, 운영체제 등에서도 사용되는 범용적인 용어이다.

## REST API란?
따라서, REST API라는 것은 **REST 원칙을 적용하여 서비스 API를 설계한 것**을 말하며 대부분의 서비스가 REST API를 제공한다.

<br>

## REST 특징

### 균등한 인터페이스 (Uniform Interface)

REST가 HTTP의 표준만 따른다면 어떠한 기술이던지 접목하여 사용할 수 있기 때문에 플랫폼이나 언어의 제약에 구애받지 않는다. 요즘은 REST API를 정의할 때 JSON(JavaScript Object Notation) 방식을 가장 많이 사용하지만 XML(eXtensible Markup Language)도 적용할 수 있다.

### 무상태성 (Stateless)

서버는 클라이언트의 상황을 고려하지 않고 API 요청에 대해서만 처리하기 때문에 이를 **"상태가 없다"** 라고 표현한다. 이렇게 되면 클라이언트를 고려하지 않아도 되기 때문에 구현이 간결해진다.

### 캐싱 가능 (Cacheable)

REST는 HTTP 표준을 기반으로 만들어졌기 때문에 HTTP의 특징인 캐싱을 사용할 수 있다. REST API를 활용하여 `GET` 메소드를 `Last-Modified` 값과 함께 보낼 경우, 컨텐츠의 변화가 없을 때 캐시된 값을 사용하게 된다. 이렇게 되면 네트워크 응답시간 뿐만 아니라 API 서버에 요청을 발생시키지 않기 때문에 부담이 덜 하다는 장점 또한 가지게 된다.

### 자체 표현성 (Self-Descriptiveness)

REST API의 자원명시 규칙 및 메소드는 그 자체로 의미를 지니기 때문에 어떠한 요청에 있어서 그 요청 자체로 어떤 것을 표현하는지 알아보기 쉽다. 물론 API를 규정한 각 서비스들이 문서를 제공하지만 이 특성에 따라서 요청하는 방식만으로 어떠한 의미인지 알 수 있어야 좋은 REST API라고 할 수 있다.

### 클라이언트-서버 구조 (Client-Server Architecture)

REST 서버가 API를 제공하는 방식이기 때문에 클라이언트에서 처리하는 부분과 독립적으로 동작한다. 따라서, 서로간의 의존성이 줄어들고 클라이언트와 서버를 최대한 독립적으로 개발할 수 있도록 도와준다.

### 계층형 구조 (Layered System)

클라이언트는 계층형 구조가 불가능하지만 REST 서버의 경우, 보안/로드 밸런싱/암호화 등을 추가할 수 있고 Proxy 및 게이트웨이 등의 중간매체를 사용할 수 있다.

<br>

## REST 구성요소
1. 자원 : URI
2. 행위 : HTTP Method (GET, POST, PUT, DELETE, HEAD)
3. 표현 : JSON, XML, Text, RSS 등

<br>

## REST API 디자인 가이드

### URI는 정보의 자원을 표현해야 한다.
- 리소스 명은 동사가 아닌 명사를 사용해야 한다.
- 리소스는 Collection과 Document로 표현할 수 있다. (Collection은 복수를 사용한다)

```
/locations/seoul/schools/3
```
여기서 `locations`은 Collection을 `Seoul`은 Document를 표현한다.

### 자원에 대한 행위는 HTTP Method로 표현한다.
URI는 자원을 표현하는 데에 집중하고 행위에 대한 정의는 HTTP Method를 통해 하는 것이 REST한 API를 설계하는 중심 규칙이다.

### 리소스에 대한 정확한 응답(상태코드)을 내어줘야 한다.
잘 설계된 REST API는 URI만 잘 설계된 것이 아닌 그 리소스에 대한 응답을 잘 내어주는 것까지 포함되어야 한다. 정확한 응답의 상태코드만으로도 많은 정보를 전달할 수 있기 때문에 응답의 상태코드 값을 명확히 돌려주는 것은 중요하다.

<br>

## 결론
REST API는 정해진 명확한 표준이 없기 때문에 REST API를 사용함에 있어 '무엇이 옳고 그른지'가 아닌 개발하는 서비스의 특징과 개발 집단의 환경과 성향 등이 충분히 고려되어 설계되어야 한다.

<br>

## 참고
- [REST API 제대로 알고 사용하기 | NHN Cloud Meetup](https://meetup.toast.com/posts/92)
- [REST API | Github]](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/network/rest-api.md)