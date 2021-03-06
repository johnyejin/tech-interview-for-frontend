# 실행 컨텍스트 (Execution Context)
실행 컨텍스트는 **실행할 코드에 제공할 환경 정보들을 모아놓은 객체**이다.
동일한 환경에 있는 코드들을 실행할 때 필요한 환경 정보들을 모아 컨텍스트를 구성하고 이를 콜 스택에 쌓아올렸다가, 가장 위에 쌓여있는 컨텍스트와 관련 있는 코드들을 실행하는 식으로 전체 코드의 환경과 순서를 보장한다.

<br>

## 실행 컨텍스트 동작
자바스크립트는 어떤 실행 컨텍스트가 활성화되는 시점에
- 선언된 변수를 위로 끌어올리고(호이스팅)
- 외부 환경 정보를 구성하고
- this 값을 설정하는 

등의 동작을 수행한다.

<br>

## 실행 컨텍스트 구성 방법
- 전역 공간
- eval() 함수
- 함수
- 블록 {} -> ES6에서 추가됨

<br>

## 실행 컨텍스트 객체
어떤 실행 컨텍스트가 활성화될 때 자바스크립트 엔진은 해당 컨텍스트에 관련된 코드들을 실행하는 데 필요한 환경 정보들을 수집해 여기에 저장한다. (이 객체는 자바스크립트 엔진이 활용할 목적으로 생성할 뿐, 개발자가 코드를 통해 확인할 순 없다.)

<br>

## 실행 컨텍스트 구성요소
1. VariableEnvironment
   - 현재 컨텍스트 내의 식별자들에 대한 정보 + 외부 환경 정보
   - 선언 시점의 LexicalEnvironment의 스냅샷으로, 변경 사항은 반영되지 않음
2. LexicalEnvironment : 처음에는 VariableEnvironment와 같지만, 변경 사항이 실시간으로 반영됨
3. ThisBinding : this 식별자가 바라봐야 할 대상 객체

<br>

## 참고
- 코어 자바스크립트 (책)