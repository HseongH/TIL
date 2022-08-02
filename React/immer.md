# Immer

리액트에서 배열이나 객체를 업데이트 할 때는 직접 수정하면 안되고 불변성을 유지해주면서 수정해야한다.

```javascript
// object
const object = {
  a: 1,
  b: 2,
};

const nextObject = {
  ...object,
  b: 3,
};

// array
const array = [1, 2];

const nextArray = [...array, 3];
```

어려운 작업은 아니지만 크기가 커지거나 하나의 객체/배열에서 여러 가지 동작이 수행되는 경우 귀찮은 작업이 될 수 있다.

---

## 1. Immer 사용하기

Immer를 사용하면 불변성을 신경 쓰지 않는 것처럼 코드를 작성해도 불변성 관리를 할 수 있다.

**설치**

```
$ yarn add immer
```

**사용법**

```javascript
import produce from 'immer';

const state = {
  number: 1,
  dontChangeMe: 2,
};

const nextState = produce(state, (draft) => {
  draft.number += 1;
});

console.log(state); // {number: 1, dontChangeMe: 2}
console.log(nextState); // {number: 2, dontChangeMe: 2}
```

produce는 두 가지 파라미터를 받는다. 첫 번째 파라미터는 수정하고 싶은 상태, 두 번째 파라미터는 상태를 어떻게 업데이트할지 정의하는 함수이다.

두 번째 파라미터로 전달되는 함수 내부에서 원하는 값을 변경하면, produce 함수가 불변성 유지를 대신해 주면서 새로운 상태를 생성해 준다.

[Immer](https://react.vlpt.us/basic/23-immer.html)
