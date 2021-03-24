# React Hooks
Hooks는 리액트 v16.8에 새로 도입된 기능으로서, 함수형 컴포넌트에서도 상태 관리를 할 수 있는 useState, 그리고 렌더링 직후 작업을 설정하는 useEffect 등의 기능 등을 제공하여 기존의 함수형 컴포넌트에서 할 수 없었던 다양한 작업을 할 수 있게 해준다.

<br>

## useState
함수형 컴포넌트에서 상태를 관리해주는 hook이다. useState를 사용할때는 상태의 기본값을 파라미터로 넣어서 호출해준다.

이 함수를 호출하면 배열이 반환되는데, 여기서 첫번째 원소는 현재 상태, 두번째 원소는 setter 함수이다. setter 함수를 사용할때는 업데이트 하고 싶은 새로운 값을 파라미터로 넣어주면 된다.

<br>

## useEffect
useEffect hook을 사용하면 다음과 같은 상황에서 특정 작업을 처리할 수 있다.

- 컴포넌트가 처음 나타났을 때 (마운트)
- 컴포넌트가 사라질 때 (언마운트)
- 컴포넌트가 업데이트될 때 (특정 props가 바뀔 때 등)

useEffect의 첫번째 파라미터는 함수, 두번째 파라미터에는 의존값이 들어있는 배열(deps)을 넣는다. 만약 두번째 파라미터에 빈배열을 넣는다면 컴포넌트가 처음 나타날때에만 함수가 실행된다.

### useEffect의 cleanup 함수
useEffect에서는 함수를 반환할 수 있는데, 이 함수를 cleanup 함수라고 한다. useEffect에 대한 뒷정리를 해준다고 할 수 있다. cleanup 함수의 두번째 파라미터가 비어있다면 컴포넌트가 사라질 때 cleanup 함수가 호출된다. 반대로 두번째 파라미터가 비어있지 않다면 cleanup 함수는 언마운트 시에도 호출되고, 값이 바뀔때에도 호출된다.

### 컴포넌트가 마운트될 때 주로 하는 작업
- 외부 API 요청 (REST API 등)
- `setInterval`을 통한 반복 작업 혹은 `setTimeout`을 통한 작업 예약
- 라이브러리 사용 (D3, Video.js 등)

### 컴포넌트가 언마운트될 때 주로 하는 작업
- `setInterval`, `setTimeout`을 사용하여 등록한 작업들 clear 하기
(clearInterval, clearTimeout)
- 라이브러리 인스턴스 제거

<br>

## useReducer
리액트에서 useState hook 말고도 상태를 관리해줄 수 있는 hook이다. **useReducer를 사용하면 상태관리 로직을 컴포넌트에서 분리시킬 수 있다.**

useReducer의 첫번째 인자로 reducer 함수를 넣고, 두번째 인자로 초기 상태값을 넣는데, reducer 함수는 상태와 액션 타입을 받아 액션에 따라 변화된 상태값을 리턴해준다. useReducer는 상태값인 `state`와 액션을 발생시키는 함수인 `dispatch`를 리턴해주는데, 리턴된 `state`와 `dispatch`를 필요한 컴포넌트에서 가져다 사용할 수 있다.

> 💡 reducer 함수에서는 새로운 상태를 만들 때 불변성을 지켜줘야하기 때문에 spread 연산자를 사용한다.

### 언제 useState를 사용하고 언제 useReducer를 사용하지?
컴포넌트에서 관리하는 값이 하나이거나 그 값이 단순한 숫자, 문자열 또는 boolean 값이면 `useState`로 관리하는 것이 편할 것이다. 하지만 컴포넌트에서 관리하는 값이 여러 개가 되어 상태의 구조가 복잡해진다면 `useReducer`로 관리하는 것이 편해질 수도 있다.

예를 들어 setter를 한 함수에서 여러번 사용해야 하는 일이 발생한다면 useReducer를 사용해 상태 관리 로직을 컴포넌트 밖으로 빼는 것이 가독성도 좋아지고 값만 넘기면 되기 때문에 편리하다.

결론은 useReducer를 썼을 때 편할 것 같으면 useReducer를 사용하고, 그렇지 않다면 useState를 사용하면 된다.

<br>

## useRef
JavaScript를 사용할때는 특정 돔을 선택해야하는 상황에서 querySelector와 같은 DOM selector 함수를 사용해 돔을 선택한다. 리액트에서 **특정 돔을 선택**해야하는 상황이 발생하면 useRef hook을 사용한다.

### 리액트에서 돔을 직접 선택해야하는 상황
- 특정 엘리먼트의 크기를 가져오는 경우
- 스크롤바의 위치를 가져오거나 설정하는 경우
- 포커스를 설정하는 경우

#### 사용 예시
```jsx
const nameInput = useRef();

const onReset = () => {
	nameInput.current.focus();
}

return <input ref={nameInput} />
```

<br>

## useMemo
성능 최적화를 위해 useMemo hook을 사용해 **연산된 값을 재사용**할 수 있다.

useMemo의 첫번째 파라미터에는 어떻게 연산할지 정의하는 함수를 넣어주고, 두번째 파라미터에는 deps(의존값이 들어있는) 배열을 넣어준다. 이 배열 안에 넣은 내용이 바뀌면 함수가 실행되고, 내용이 바뀌지 않았다면 이전에 연산한 값을 재사용하게 된다.

<br>

## useCallback
useMemo는 특정 결과값을 재사용할 때 사용하는 반면, useCallback은 **특정 함수를 새로 만들지 않고 재사용**하고 싶을 때 사용한다.

useCallback의 첫번째 파라미터에는 재사용할 함수를 넣어주고 두번째 파라미터에는 함수 안에서 사용하는 상태 혹은 props를 넣어준다.

<br>

## 커스텀 hook
컴포넌트를 만들다보면 반복되는 로직이 많이 발생한다. 예를 들어 input을 관리하는 코드는 관리할 때마다 비슷한 코드가 반복된다. 이러한 상황에 커스텀 훅을 만들어 반복되는 로직을 쉽게 재사용할 수 있다.


<br>

## 참고
- [velopert | react-hooks](https://velog.io/@velopert/react-hooks#1-usestate)