# 웹 브라우저 저장소
HTML5에는 웹의 데이터를 클라이언트에 저장할 수 있는 새로운 자료구조인 **Web Storage** 스펙이 포함되어 있다. **Web Storage**의 개념은 키/값 쌍으로 데이터를 저장하고 키를 기반으로 데이터를 조회하는 패턴이다. 그리고 **영구 저장소(LocalStorage)** 와 **임시 저장소(SessionStorage)** 를 따로 두어 데이터의 지속성을 구분할 수 있어 응용 환경에 맞는 선택이 가능하다.

Web Storage는 기존 웹 환경의 **쿠키(Cookie)** 와 매우 유사한 개념이다. 크게 차이는 없지만 몇 가지 쿠키의 단점을 극복하는 개선점이 도입되었다. 따라서, 각각의 특징과 차이점에 대해서 알아볼 것이다.

<br>

## Web Storage vs Cookie
#### 쿠키는 매번 서버로 전송된다.
웹사이트에서 쿠키를 설정하면 이후 모든 웹 요청은 쿠키 정보를 포함해 서버로 전송된다. Web Storage에 저장된 데이터는 클라이언트에 존재할 뿐 서버로 전송되지 않는다. 이는 네트워크 트래픽 비용을 줄여준다.

#### 용량 차이
쿠키의 용량은 4KB로 클라이언트에 최대 300개를 저장할 수 있으며, 하나의 사이트(도메인)에서는 최대 20개를 저장할 수 있다. 하지만 Web Storage는 5MB ~ 10MB로 용량 제한이 거의 없다고 보면 된다. 하지만 쿠키도 하위키를 이용하면 이러한 제한을 일부 해소할 수 있다.

#### 데이터 지속시간
쿠키는 만료일자를 지정하게 되어 있어 언젠간 제거된다. 반면 LocalStorage는 만료일자를 설정하는게 없어 사용자가 지우지 않는 이상 영구적으로 존재한다.

<br>

## LocalStorage vs SessionStorage
Web Storage는 LocalStorage와 SessionStorage라는 두 가지 용도의 저장소를 제공한다. 기본적으로 Web Storage는 쿠키와 마찬가지로 사이트의 도메인 단위로 접근이 제한된다. 그럼 LocalStorage와 SessionStorage의 차이점에 대해 알아볼 것이다.

### 데이터의 지속성
**LocalStorage**의 데이터는 사용자가 지우지 않는 이상 계속 브라우저에 남아있게 된다. 반면 **SessionStorage**의 데이터는 윈도우나 브라우저 탭을 닫을 경우 제거된다.

### 데이터의 범위
**LocalStorage**는 도메인만 같으면 전역적으로 데이터 공유가 가능한 반면, **SessionStorage**는 같은 도메인이라도 브라우저가 다르면 서로 다른 영역이 된다. 브라우저 컨텍스트가 다르기 때문이다. (새로운 브라우저에서 실행하거나 새탭에서 실행했을때 **SessionStorage**는 별개의 영역이 된다.)

> 💡 **브라우저 컨텍스트란?**<br>
> document를 표시하는 환경을 말한다. 즉, 브라우저가 불러온 웹페이지이다.

### 사용
지속적으로 필요한 데이터(자동 로그인)는 **LocalStorage**에 저장하고, 잠깐 동안 필요한 정보(일회성 로그인)는 **SessionStorage**에 저장한다. 하지만 비밀번호 같은 중요한 정보는 클라이언트에 저장하면 언제든 털릴 수 있기 때문에 저장하지 않는 것이 좋다.

<br>

## Web Storage를 사용할 때 주의해야할 점
### 데이터 수정 가능
클라이언트는 얼마든지 Web Storage에 저장된 값을 임의로 수정할 수 있다. 따라서 개발자는 사용자에 의한 임의 변경에 항상 예의주시하고 방어코드를 작성할 필요가 있다.

### 모델의 객체를 저장하는 경우의 문제점
storage에 단순히 하나의 문자열 값을 저장하기도 하지만, 대부분의 경우 실제 데이터 모델을 저장하는 경우가 많다. 모델을 JSON 형태의 string으로 변환하고 저장했을 때, 불러오는 경우 동일한 모델 형태가 보장되지 않는다.

즉, 모델을 그대로 저장하고 불러올 경우, 기존의 instance와 다른 모델이 되어버려 모델의 인스턴스를 잃어버린채 사용하거나 어디서 저장되고 불러와 사용되는지 관리되지 않는 경우가 생긴다.

해결방법은 기존의 usecase 모델에서 storage로 직접 접근하던 방식을 지양하고 프로젝트 상에 명확한 개념으로 존재하는 모델만으로 storage를 사용하도록 api를 제공하는 방식을 사용한다. 즉, storage에 접근하는 부분을 추상화시키는 것이다.

결과적으로 절대적인 코드량은 증가하지만, 확실한 관심사 분리로 storage 사용에 대한 안전성을 높일 수 있다.

<br>

## 참고
- [velog | LocalStorage, SessionStorage, Cookie의 차이점](https://velog.io/@ejchaid/localstorage-sessionstorage-cookie%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90)
- [뱅크샐러드 | Typescript로 Local Storage 안전하게 사용하기](https://blog.banksalad.com/tech/typescript-local-storage/?gclid=Cj0KCQiAv6yCBhCLARIsABqJTjbi195M5-IdHPW79fHun0ENuBsv6389fuKjyC5Qrdqew4TSGVtFEhEaAt20EALw_wcB)
