# OAuth 
OAuth란 **자신의 앱에서 사용자 인증을 하기 위해 다른 어플의 사용자 인증방식을 사용하도록 인가하는 것**을 말한다. 서비스마다 제각각인 인증방식을 표준화한 인증방식으로 사용자 인증방식 중 토큰 인증 방식을 사용한다.

## 장점
구글, 페북 같은 많은 사람들이 이용하는 웹 서비스의 계정을 내 애플리케이션에서도 사용할 수 있다.
구글, 페북에서 이미 사용자 인증을 수행했기 때문에
나의 애플리케이션에서는 그 회사로부터 로그인 권한을 부여받기만 하면 되는 것이다.

<br>

## 과정
1. 사용자 인증 방식이 잘 구현된 어떤 서비스에 인증을 인가
2. 인증 절차 수행
3. 인증이 되었다는 토큰을 받아 나의 앱에 권한을 부여

다음은 **생활코딩 홈페이지에서 Github 로그인하는 과정**이라고 가정한다.

1. 사용자가 생활코딩 홈페이지에서 Github 로그인 버튼을 누른다.
2. 브라우저는 생활코딩 서버에 `로그인 URL`을 요청한다.
3. 생활코딩 서버에서 `로그인 URL`을 브라우저에 전달한다.
4. 브라우저는 서버에서 받은 `로그인 URL`로 리다이렉트한다.
5. 브라우저에 Github 로그인 화면이 뜬다.
6. 사용자는 생활코딩이 요청한 정보(scope) 제공 요청을 승인하고, 자신의 Github 아이디와 비밀번호를 입력한다.
7. Github 인증 서버(Auth Server)에서 사용자의 아이디와 비밀번호, 제공할 정보 범위(scope)를 확인한다.
8. 인증이 완료되면 `Authorization Code`를 `redirect_url`에 붙여 보낸다.

    `ex) https://redirect_url?code=199b7af5ea11078ee507`

9. 생활코딩 서버에서는 `Authorization Code`를 받아 `Client ID, Client Secret, Authorization Code` 를 Github OAuth 서버에 보낸다. (redirect_url은 optional)
10. Github 서버는 `Client ID, Client Secret, Authorization Code` 가 모두 일치하는지 확인하고, 모두 일치하면 `AccessToken`을 생활코딩 서버에 보낸다.
11. 생활코딩 서버는 `AccessToken`을 이용해 Github의 Resource Server로부터 사용자 정보를 받아온다.

<br>

## 참고
- [OAuth 인증 방식 | victory](https://victorydntmd.tistory.com/4)
- [OAuth 인증 | velog](https://velog.io/@sonypark/OAuth2-%EC%9D%B8%EC%A6%9D)