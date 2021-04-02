# GraphQL
> API를 위한 쿼리 언어이며 이미 존재하는 데이터로 쿼리를 수행하기 위한 런타임

### 특징
- SQL은 서버 측 요청인 반면, GraphQL은 클라이언트가 요청
- 타입 기반 API 스키마 작성

![image](https://user-images.githubusercontent.com/26537048/100116111-b45f4480-2eb6-11eb-8ba9-ec70f1c1c15d.png)

### 장점
1. REST API를 사용할 때 정의되던 각 CRUD에 요청이 GraphQL에서는 단 하나의 EndPoint에서 일어난다.
    - Query의 요청에 따라 결과가 달라진다.
    - API에 대한 version 관리가 필요없다.
2. 데이터 요청이 유연하다.
    - 필요한 데이터만 요청 가능하다.
4. REST API와 함께 사용할 수 있다.

### 단점
1. 병목현상과 재귀적 호출 등은 과도한 트래픽 유발 문제가 될 수 있다.
    - 재귀적 호출 문제를 해결하기 위해 depth를 지정해줄 수 있다.
2. REST API는 특정 url을 기준으로 쉽게 캐싱을 제공할 수 있는 반면, GraphQL은 한 가지의 EndPoint를 통해 요청 쿼리에 따라 다른 결과를 반환하여 캐싱이 복잡하다.
    - Apollo 등의 서비스를 이용해 해결할 수 있다.
3. Client 개발자가 직접 Query를 작성해야 하기 때문에 GraphQL 문법을 알아야 한다.

<br>

## GraphQL vs REST API
`GraphQL`과 `REST API`의 가장 큰 차이점은 다음과 같다.

1. `REST API`는 resource마다 하나의 endpoint를 가지는데, `GraphQL`은 전체 api를 위한 하나의 endpoint만을 사용한다.
2. `REST API`는 하나의 endpoint에서 돌려줄 수 있는 응답의 구조가 정해져있지만 `GraphQL`은 사용자가 응답의 구조을 원하는대로 바꿀 수 있다.

### 그럼 언제 어떤걸 선택해야 하는가?
#### GraphQL
- 서로 다른 모양의 다양한 요청들에 대해 응답할 수 있어야할때
- 대부분의 요청이 CRUD에 해당할 때

#### REST API
- http와 https에 의한 캐싱을 잘 사용하고 싶을 때
- file 전송 등 단순한 text로 처리되지 않는 요청들이 있을 때
- 고정된 요청과 응답만 있는 경우

각각의 차이점에 따른 장단점이 존재하기 때문에 상황에 맞게 사용하는 것이 중요하다.

<br>

# Prisma
> 데이터베이스를 쉽게 사용할 수 있게 도와주는 데이터베이스 툴킷. Prisma를 통해 ORM을 대체.

### 특징
- GraphQL 형식의 데이터모델만 작성하면, 사용하는 언어와 DBMS에 구애받지 않고 ORM 클라이언트와 모델 그리고 Data Schema가 자동으로 생성된다.
- GraphQL, REST API의 구현체(Resolvers)를 제공해준다.
- 자체 어드민 페이지를 제공하여 쉬운 데이터 운용이 가능하다.

### 동작방식
1. Scala로 작성된 Prisma의 서버가 DB 호스트를 앞단에서 관리한다.
2. GraphQL 형식의 DataModel을 정의하면
3. Prisma가 알아서 사용하고 있는 DBMS와 언어의 종류에 맞게 실제 DB 배포부터 클라이언트와 모델, 타입정의까지 자동으로 만들어 제공한다. (GraphQL의 구현체까지 모두 정의되어있다.)
4. 만들어진 클라이언트, 모델, 구현체 등을 바탕으로 실제 서버에 적용한다. (주로 `apollo-server`를 이용해 구현체(Resolvers)를 그대로 활용한다)

![](https://i.imgur.com/H2tN8FS.png)

### Support
- 언어: `JavaScript` `TypeScript` `Go`
- DBMS: `MySQL` `mongoDB` `Postgres`

<br>

# Apollo
> GraphQL 기반의 플랫폼

- 글로벌 저장소(global store)와 캐시 등을 제공하는 Apollo는 Apollo Client와 Apollo Server로 나뉘어 있다.
- Apollo Client는 React뿐만 아니라 Angular, Vue.js, iOS, Android 등 다양한 환경에서 사용할 수 있다.
- Apollo Server는 Node.js 기반의 HTTP 서버로 작동한다.
- Apollo Client와 Apollo Server를 사용해 GraphQL 기반의 데이터를 용이하게 관리할 수 있다.


# GraphQL, Prisma, Apollo 구성도
![](https://i.imgur.com/tZUKS7x.png)


## 참고
- [Prisma로 GraphQL을 쉽게 도입하기](https://medium.com/labelstore/prisma%EB%A1%9C-graphql%EC%9D%84-%EC%89%BD%EA%B2%8C-%EB%8F%84%EC%9E%85%ED%95%98%EA%B8%B0-fa64dcf63382)
- [GraphQL, Apollo, Prisma 간단 소개](https://medium.com/@yoohl/graphql-apollo-prisma-8d2eff3315e3)
- [Prisma 사용하기](https://gmyankee.tistory.com/264)
- [Prisma2 사용기](https://medium.com/wasd/prisma2-%EC%82%AC%EC%9A%A9%EA%B8%B0-70c8517539d)
- [React와 Apollo, Parcel 기반 서비스 개발](https://d2.naver.com/helloworld/2838729)