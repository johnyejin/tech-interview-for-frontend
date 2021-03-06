# JWT (JSON Web Token)

JSON으로 된 Token을 사용한다. 즉, OAuth와 같이 토큰 기반의 인증 방식이다.

JWT는 **토큰 자체가 의미를 갖는 Claim 기반의 토큰** 방식이다. Claim(권한)은 사용자에 대한 프로퍼티나 속성을 의미한다. 즉, JWT는 OAuth처럼 아무 의미없는 문자열로 된 토큰이 아니라는 것이다.

<br>

## 동작 과정

1. JSON 객체에 요구사항을 작성
2. 특정 암호화 방식을 사용해 문자열로 인코딩
3. HTTP header에 추가함으로써 사용자 인증을 요청
4. 서버에서는 Header에 추가된 토큰을 디코딩하여 사용자를 인증

<br>

## 특징

- JWT는 그 자체가 암호회된 문자열 데이터다.
- 토큰은 HTTP header에 추가되기 때문에 서버에 따로 보관할 필요가 없으므로 서버에 부하를 일으키지 않는다.
- 토큰을 생성할 때 암호화 과정을 거치므로 보안적으로 안전하다.

그렇다고 JWT가 보안에 완벽한 것은 아니다. 누군가가 토큰을 탈취한다면, 그 토큰을 이용해 권한을 수행할 수 있다.

그래서 토큰을 서버에 저장하는 것이 아니기 때문에 **토큰에 유효시간을 설정**해야 하며, 탈취될 가능성을 줄이기 위해 **유효시간을 짧게 해주는 것이 좋다.**

<br>

## JWT의 데이터 무결성, HMAC(Hash-based Message Authentication)

JWT는 토큰이 탈취 당하더라도 위변조의 위험을 벗어날 수 있도록 무결성을 보장하는 몇 가지 방법이 있다.

그 방법 중 하나는 **데이터를 암호화하고 해싱**하는 HMAC 기법을 사용하는 것이다.

**해싱**은 원문을 일정 길이의 byte로 변환하는데 그 결과가 유일하다는 특징이 있다. 즉, 원문이 조금이라도 바뀌면 해싱의 결과는 완전히 달라진다.

그래서 **토큰을 탈취해서 데이터를 수정하게 되면, 해싱의 결과가 완전히 달라지므로 토큰이 위조되었다는 것을 알 수 있게 된다.**

<br>

## JWT 구조 및 생성

토큰은 아래와 같이 Header, Payload, Signature로 구성되어 있다.

![image](https://user-images.githubusercontent.com/26537048/113404825-c3fe1500-93e3-11eb-8c73-8bf153bd894f.png)

토큰의 구조

1. **헤더**
    - `typ` : 토큰의 타입을 명시한다.
    - `alg` : 해싱 알고리즘을 명시한다. 이 알고리즘은 서버에서 토큰을 검증할 때 signature에 사용된다.
2. **내용, Payload**

    내용에는 토큰에 대한 정보를 작성한다. 정보는 { 속성, 값 }으로 표현되며 이를 claim이라고 한다.

    claim은 `iss(토큰 발급자)`, `exp(토큰의 만료시간)`, `sub(토큰 제목)`, `aud(토큰 대상자)` 등의 정보로 구성되어 있다.

3. **서명, Signature**

    서명에는 헤더의 인코딩 값과 내용의 인코딩 값을 .으로 연결하여 합친 후 비밀키로 해싱한다. 일종의 암호화하는 작업이다.

위의 세가지 값들을 `.`으로 합치면 하나의 JWT가 생성된다. 이렇게 생성된 JWT를 HTTP header에 추가해 서버에 요청을 하면, 서버에서는 이를 디코딩하여 사용자 인증을 하게 된다.

<br>

## 결론

JWT는 자체적으로 정보를 갖고 있는 토큰이기 때문에 서버에 저장될 필요가 없다. 즉, 서버로부터 독립적이라고 할 수 있으며, 서버의 부담을 덜어줄 수 있다는 장점이 있다.

JWT는 브라우저의 쿠키, local storage, session storage에 저장할 수 있지만, **HTTP Only 옵션의 쿠키에 저장하는 것이 좋다.**

<br>

## 참고
- [JWT (JSON Web Token) | victory](https://victorydntmd.tistory.com/115)