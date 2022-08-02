# JSX

## 1. JSX란?

자바스크립트의 확장 문법으로 XML과 유사한 구조이다.

**장점**

- 일반 자바스크립트로 작성한 코드에 비해 가독성이 높고 작성이 쉽다.
- HTML 코드를 사용할 수 있고, 컴포넌트도 HTML 처럼 사용할 수 있기 때문에 활용도가 높다.

---

## 2. JSX 문법

### 2.1 무조건 하나의 엘리먼트 반환하기

컴포넌트에 여러 요소가 존재한다면 반드시 하나의 부모 요소로 감싸야 한다.

```javascript
import React from "react";

function App() {
  return (
    <div className="App">
      <h1>Hello JavaScript!</h1>
      <h2>Hello React!</h2>
    </div>
  );
}

export default App;
```

HTML 요소로 감싸고 싶지 않은 경우 Fragment라는 기능을 사용한다.

```javascript
import React from "react";

function App() {
  return (
    <Fragment>
      <h1>Hello JavaScript!</h1>
      <h2>Hello React!</h2>
    </Fragment>
  );
}

// Fragment를 생략해 사용할 수도 있다.
function App() {
  return (
    <>
      <h1>Hello JavaScript!</h1>
      <h2>Hello React!</h2>
    </>
  );
}

export default App;
```

[Fragments](https://ko.reactjs.org/docs/fragments.html)

### 2.2 자바스크립트 표현식 사용

JSX 내부에서 자바스크립트 표현식을 사용하기 위해선 { }로 코드를 감싸준다.

```javascript
import React from "react";

function App() {
  const name = "홍성훈";

  return (
    <div className="App">
      <h1>Hello {name}!</h1>
      <h2>Hello React!</h2>
    </div>
  );
}

export default App;
```

### 2.3 조건부 연산자 사용

JSX 내부에서는 if 문을 사용할 수 없다. 하지만 조건에 따라 다른 내용을 랜더링해야 하는 경우 JSX 밖에서 if 문을 사용하여 사전에 값을 설정하거나, 조건부 연산자를 사용한다. 조건부 연산자는 자바스크립트의 삼항 연산자 형태로 사용된다.

```javascript
import React from "react";

function App() {
  const name = "레미";

  return (
    <div className="App">
      {name === "레미" ? (
        <h1>{name}는 고양이 입니다.</h1>
      ) : (
        <h1>{name}는 고양이가 아닙니다.</h1>
      )}
    </div>
  );
}

export default App;
```

### 2.4 AND 연산자를 사용한 조건부 렌더링

AND 연산자를 사용해 조건에 부합하면 내용을 보여주고 아니라면 아무것도 렌더링하지 않을 수 있다.

```javascript
import React from "react";

function App() {
  const name = "레미";

  return (
    <div className="App">
      {name === "레미" && <h1>{name}는 고양이 입니다.</h1>}
    </div>
  );
}

export default App;
```

### 2.5 OR 연산자를 사용한 조건부 렌더링

OR 연산자를 사용해 유효한 값이 아닐 때 렌더링할 요소를 지정할 수 있다.

```javascript
import React from "react";

function App() {
  const name = undefined;

  return <div className="App">{name || <h1>값이 존재하지 않습니다.</h1>}</div>;
}

export default App;
```

### 2.6 className 사용

JSX에서 class를 설정할 때는 class가 아닌 className을 통해 설정해야 한다.

```javascript
import React from "react";

function App() {
  return (
    <div className="App">
      <h1 className="heading">제목이다.</h1>
    </div>
  );
}

export default App;
```

### 2.7 태그는 꼭 닫아준다.

HTML5에서 빈 태그는 태그를 꼭 닫지 않아도 사용할 수 있었다.

```html
<input>
<br>
<img>
```

하지만 JSX에서는 태그를 닫지 않으면 오류가 발생한다.

```javascript
import React from 'react';

function App() {
    return (
        <div className="App">

            <h1 className="heading">제목이다.</h1>
            <input> {/* SyntaxError: Unterminated JSX contents */}

        </div>
    );
}

export default App;
```

닫는 태그를 달아주거나 <태그 /> 형태로 사용한다.

```javascript
import React from "react";

function App() {
  return (
    <div className="App">
      <h1 className="heading">제목이다.</h1>
      <input></input>
      <input />
    </div>
  );
}

export default App;
```

### 2.9 주석

JSX에서 주석을 사용할 때는 {/_ ... _/} 형태로 작성한다.

```javascript
import React from "react";

function App() {
  return (
    <div className="App">
      {/* 이건 주석 */}
      // 이건 렌더링 됨
      /* 이것도 */
    </div>
  );
}

export default App;
```
