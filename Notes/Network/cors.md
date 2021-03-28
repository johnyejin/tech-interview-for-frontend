# CORS (Cross Origin Resource Sharing)
CORS에 대해 알아보기 전에 먼저 동일 출처 정책에 대해 알아보자.

## 동일 출처 정책(Same-Origin Policy) 이란?
동일 출처 정책이란 **어떠한 문서나 스크립트가 다른 프로토콜/호스트/포트에 있는 리소스를 사용하는 것을 제한하는 정책**이다. 프로토콜/호스트/포트 중 하나라도 다르면 동일 출처 정책이 적용돼 요청에 실패한다.

### 동일 출처 정책을 해결하기 위한 방법
- CORS
- Proxy 서버
- document.domain
- window.postMessage
- JSONP (JSON with Padding)

<br>

## CORS란?
CORS란 **타 도메인 간 자원 공유를 가능하게 해주는 매커니즘**이다. 다른 출처(프로토콜/호스트/포트)의 자원 및 리소스를 요청할 때 Cross-Origin HTTP 요청을 실행한다.

### CORS가 필요한 이유
만약 내가 서비스하고 있지 않은 사이트에서 세션을 요청해 세션을 획득할 수 있다면, 해당 사이트는 악의적으로 내 세션을 탈취하거나 다른 행동을 취할 수 있다. 이러한 것을 막고 내가 허용한 origin들만 요청할 수 있도록 하기 위해 필요하다.

### CORS 과정
1. CORS 요청시에는 미리 options 주소로 서버가 CORS를 허용하는지 물어본다.
2. 이때 `Access-Control-Request-Method`로 실제로 보내고자 하는 메서드를 알리고
3. `Access-Control-Request-Header`로 실제로 보내고자 하는 헤더들을 알린다.
4. allow 항목들은 request와 대응되는 것으로, 서버가 허용하는 메서드와 헤더를 응답하는데 사용된다.
5. request와 allow가 일치하면 CORS 요청이 이루어진다.

### CORS 에러 해결 방법
다음은 서버에서 Cross-Origin HTTP 요청을 허가해주는 방식이다.

1. `Access-Control-Allow-Header` 헤더에 요청을 허가할 origin 주소를 넣어준다.
2. CORS 라이브러리를 설치해 사용한다.
   - 옵션값을 넣어주지 않으면 모든 origin에 대한 요청을 허가하기 때문에 보안상 좋지 않아 옵션값에 요청을 허용할 origin을 넣어줘야 한다.