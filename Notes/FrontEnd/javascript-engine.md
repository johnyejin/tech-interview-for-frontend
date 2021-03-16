# 자바스크립트 엔진
자바스크립트 엔진이란 자바스크립트 코드를 실행하는 프로그램 또는 인터프리터를 말한다.

<br>

## 자바스크립트 엔진의 종류
자바스크립트는 웹 브라우저 뿐만 아니라 Node.js, Electron, React Native 등의 프로젝트와 그 밖의 다양한 곳에서 동작한다.

### V8
C++로 작성되었으며, 구글이 개발한 오픈소스이다. Google Chrome, Electron, Node.js에서 사용한다.

![V8](https://user-images.githubusercontent.com/26537048/111327643-e76d5400-86b0-11eb-9a8b-b53e9256b4c8.png)


### SpiderMonkey
최초의 자바스크립트 엔진으로, 자바스크립트의 창시자인 브랜던 아이크가 넷스케이프 브라우저를 위해 개발했다. 지금은 Mozilla 재단에서 관리하며, FireFox에서 사용한다.

![SpiderMonkey](https://user-images.githubusercontent.com/26537048/111327704-f6540680-86b0-11eb-9694-467ee2b23580.png)

### Chakra
마이크로소프트가 개발한 엔진이며, Edge 브라우저에서 사용한다. Chakra 엔진의 중요 부분은 Chakra Core라는 오픈소스로 구성되어 있다.

![Chakra](https://user-images.githubusercontent.com/26537048/111327903-21d6f100-86b1-11eb-995c-50bef71538ac.png)

<br>

## 자바스크립트 엔진이 코드를 실행하는 과정
자바스크립트를 실행하기 위해선 자바스크립트 엔진이 필요하고 웹 브라우저는 자바스크립트 엔진을 내장하고 있다. 브라우저마다 엔진의 종류가 다르지만 코드를 실행하는 방식은 비슷하기 때문에 공통적으로 수행하는 과정을 알아둘 필요가 있다.

![pipeline](https://user-images.githubusercontent.com/26537048/111326965-54ccb500-86b0-11eb-9fb8-fed569b839d0.png)

자바스크립트 엔진들이 소스 코드를 기계어로 만들기까지 공통적으로 수행하는 과정은 다음과 같다.

1. 소스코드를 만나면 파싱하여 **AST(Abstract Syntax Tree)** 로 변환한다.
2. **인터프리터(Interpreter)** 는 AST를 기반으로 **바이트코드(Bytecode)를 생성**한다.
3. 인터프리터가 바이트코드를 실행할 때, 자주 사용되는 함수 및 타입 정보 등이 있는 **프로파일링 데이터(Profiling Data)** 를 바이트코드와 같이 **최적화 컴파일러(Optimizing compiler)** 에게 보낸다.
4. 최적화 컴파일러는 프로파일링 데이터를 기반으로 **최적화된 코드(Optimized code)를 생성**한다.
5. 프로파일링 데이터 중 잘못된 부분이 있으면 **최적화 해제(Deoptimize)** 를 하고 다시 바이트코드를 실행해 이전 동작을 반복한다.

<br>

## 참고
- [JavaScript 엔진 톺아보기](https://velog.io/@godori/JavaScript-engine-1)
