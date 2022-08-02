# 리덕스 (Redux)

리액트 상태 관리 라이브러리이다. 리덕스 사용 시 컴포넌트의 상태 업데이트 관련 로직을 다른 파일로 분리시켜서 효율적으로 관리 가능하고, 컴포넌트끼리 같은 상태를 공유해야 할 때 여러 컴포넌트를 거치지 않고 쉽게 상태 값을 전달하거나 업데이트할 수 있다.

## 1. 용어 정리

### 1.1 액션

상태에 어떠한 변화가 필요할 때 액션이 발생한다. 하나의 객체로 구성된다.

```javascript
{
  type: 'UPDATE';
}
```

액션 객체는 반드시 type을 가지고 있어야 한다. 이 값을 액션의 이름이라 생각하면 된다. type 이외의 값은 나중에 상태 업데이트 시 참고해야 할 값이며, 작성자 마음대로 넣을 수 있다.

```javascript
{
    type: "TASK",
    data: {
        id: 1,
        content: "모던 자바스크립트 DEEP DIVE 정독하기"
    }
}
```

### 1.2 액션 생성 함수

액션 객체를 만들어 주는 함수이다.

```javascript
function addTask(data) {
  return {
    type: 'TASK',
    data,
  };
}

const addTask = (data) => ({
  type: 'TASK',
  data,
});
```

어떤 변화를 일으켜야 할 때마다 액션 객체를 만들어야 하는데 매번 액션 객체를 직접 작성하기 번거롭고 실수가 발생할 수 있기 때문에 함수로 만들어서 관리한다.

### 1.3 리듀서

변화를 일으키는 함수이다. 액션을 만들어서 발생시키면 리듀서가 현재 상태와 전달받은 액션 객체를 파라미터로 받아오고 두 값을 참조해 새로운 상태를 만들어서 반환해준다.

```javascript
const initialState = {
  data: {
    id: 1,
    content: '모던 자바스크립트 DEEP DIVE 정독하기',
  },
};

function reducer(state = initialState, action) {
  switch (action.type) {
    case TASK:
      return {
        data: {
          ...state.data,
          id: state.data.id + 1,
          content: '공부하기',
        },
      };

    default:
      return state;
  }
}
```

### 1.4 스토어

프로젝트에 리덕스를 적용하기 위해 생성한다. 한 개의 프로젝트는 하나의 스토어만 가질 수 있다. 스토어 안에는 현재 애플리케이션 상태와 리듀서, 내장 함수가 포함되어 있다.

### 1.5 디스패치

스토어 내장 함수 중 하나이다. 액션을 발생시키는 역할을 한다. 이 함수는 dispatch(action);과 같은 형태로 액션 객체를 파라미터로 넣어서 호출한다.

디스패치 함수가 호출되면 스토어는 리듀서 함수를 실행해 새로운 상태를 만들어준다.

### 1.6 구독

스토어 내장 함수 중 하나, subscribe 함수 안에 리스너 함수를 파라미터로 넣어서 호출해 주면, 이 함수가 액션이 디스패치되어 상태가 업데이트될 때마다 호출된다.

```javascript
const listener = () => {
  console.log('Update!!');
};

const unsubscribe = store.subscribe(listener);

unsubscribe(); // 구독을 해제할 때 호출
```

---

## 2. 미들웨어

액션을 디스패치했을 때 리듀서에서 작업을 처리하기 전 사전 작업들을 실행하기 위해 사용한다.

> 액션 -> 미들웨어 -> 리듀서 -> 스토어

미들웨어가 할 수 있는 작업

- 액션을 콘솔에 기록
- 액션을 취소하거나 다른 종류의 액션을 추가로 디스패치

### 2.1 redux-logger

redux의 store가 바뀔 때마다 콘솔에 log를 남겨주는 미들웨어이다.

**설치**

```
$ yarn add redux-logger
```

**사용하기**

```javascript
import { createLogger } from 'redux-logger';

const logger = createLogger();
const store = createStore(rootReducer, applyMiddleware(logger));
```

### 2.2 redux-thunk

리덕스를 사용하는 프로젝트에서 비동기 작업을 처리할 때 가장 기본적으로 사용하는 미들웨어이다. 함수 형태의 액션을 디스패치할 수 있게 해준다.

**Thunk**

Thunk는 특정 작업을 나중에 할 수 있도록 미루기 위해 함수 형태로 감싼 것을 의미한다.

**설치**

```
$ yarn add redux-thunk
```

**사용하기**

```javascript
import { createLogger } from 'redux-logger';
import thunk from 'redux-thunk';

const logger = createLogger();
const store = createStore(
  rootReducer,
  applyMiddleware(thunk.withExtraArgument({ history: history }))
);
```

**withExtraArgument**

thunk 함수에서 사전에 정해준 값들을 참조할 수 있다.

[redux-thunk](https://velog.io/@mokyoungg/Redux-Redux-thunk)

---

## 3. Redux DevTools

리덕스 개발자 도구이며, 크롬 확장 프로그램으로 설치할 수 있다.

```javascript
const composeEnhancers =
  (typeof window !== 'undefined' && window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__) || compose;
```

패키지를 설치하여 적용하면 더 간단하게 쓸 수도 있다.

**설치**

```
$ yarn add redux-devtools-extension
```

```javascript
import { composeWithDevTools } from 'redux-devtools-extension';

const store = createStore(rootReducer, composeWithDevTools());
```

[Redux DevTools](https://github.com/zalmoxisus/redux-devtools-extension)

---

## 4. connected-react-router

리덕스에서 주소를 변경 및 확인하기 위해 history객체를 관리하며 필요에 의해 꺼내쓸 수 있는 라이브러리이다.

**설치**

```
$ yarn add connected-react-router
```

**사용법**

```javascript
import { connectRouter } from 'connected-react-router';

const rootReducer = combineReducers({
  user: User,
  router: connectRouter(history),
});
```

여기서 주의할 점은 router의 리듀서 명은 반드시 router로 고정해야 한다.

[connected-react-router](https://hokeydokey.tistory.com/74)

---

## 5. redux-actions

액션 크리에이터 함수와 리듀서를 더 간단하게 만들 수 있게 도와준다.

**설치**

```
$ yarn add redux-acitons
```

**사용하기**

```javascript
import { createAction, handleActions } from 'redux-actions';

// action
const LOG_IN = 'LOG_IN';
const LOG_OUT = 'LOG_OUT';
const GET_USER = 'GET_USER';

// action creater
const logIn = createAction(LOG_IN, (user) => ({ user }));
const logOut = createAction(LOG_OUT, (user) => ({ user }));
const getUser = createAction(GET_USER, (user) => ({ user }));

// reducer
export default handleActions(
  {
    [LOG_IN]: (state, action) => ({
        setCookie('is_login', 'success');
        draft.user = action.payload.user;
        draft.is_login = true;
      }),
    [LOG_OUT]: (state, action) => ({
        deleteCookie('is_login');
        draft.user = null;
        draft.is_login = false;
      }),
  },
  initialState
);
```
