# 라우트 (Route)

브라우저 주소에 따라 다른 화면을 보여주는 것을 라우팅이라고 한다. 리액트 라이브러리 자체에 이 기능이 내장되어 있지 않기 때문에 별도의 라이브러리를 사용해 작업을 수행한다.

## 1. 라이브러리 설치

리액트 라우터를 설치해 사용한다.

```
$ yarn add react-router-dom
```

---

## 2. 프로젝트에 적용

src/index.js 파일에서 react-router-dom에 내장되어 있는 BrowserRouter 컴포넌트를 사용하여 감싸준다.

```javascript
import React from "react";
import ReactDOM from "react-dom";
import "./index.css";
import App from "./App";
import reportWebVitals from "./reportWebVitals";
import { BrowserRouter } from "react-router-dom";

ReactDOM.render(
  <React.StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </React.StrictMode>,
  document.getElementById("root")
);

reportWebVitals();
```

---

## 3. Route 컴포넌트로 특정 주소에 컴포넌트 연결

Route 컴포넌트를 사용해 현재 경로에 따라 다른 컴포넌트를 보여줄 수 있다.

```javascript
<Route path="주소" component={보여줄 컴포넌트} />
```

```javascript
import React from "react";
import { Route } from "react-route-dom";
import Home from "./Home";
import RoutePrac from "./RoutePrac";

const App = () => {
  return (
    <>
      <Route path="/" component={Home} />
      <Route path="/route" component={RoutePrac} />
    </>
  );
};

export default App;
```

이때 /route 페이지로 이동하여도 Home 컴포넌트와 Route 컴포넌트 모두 화면에 렌더링되는 것을 알 수 있다. /route의 경로가 / 와도 일치하기 때문이다. 이를 수정하기 위해서는 exact라는 속성을 true로 설정하면 된다.

```javascript
<Route path="/" component={Home} exact={true} />
```

---

## 4. Link 컴포넌트 사용하여 다른 주소로 이동하기

Link 컴포넌트는 클릭하면 다른 주소로 이동시켜 주는 컴포넌트이다. 일반 웹 애플리케이션에서 a 태그와 그 역할이 같다.

```javascript
<Link to="주소">내용</Link>
```

```javascript
import React from "react";
import { Route, Link } from "react-route-dom";
import Home from "./Home";
import RoutePrac from "./RoutePrac";

const App = () => {
  return (
    <>
      <ul>
        <li>
          <Link to="/">홈</Link>
        </li>
        <li>
          <Link to="/route">라우트</Link>
        </li>
      </ul>

      <Route path="/" component={Home} />
      <Route path="/route" component={RoutePrac} />
    </>
  );
};

export default App;
```

***

## 5. URL 파라미터와 쿼리

페이지 전환 시 값을 전달해야 하는 경우도 존재한다. 값을 전달하는 방법으로 파라미터와 쿼리가 나눠진다.

- 파라미터: /route/prac
- 쿼리: /route?query=react

값을 전달하는 규칙으로 무조건 따라야 하는 규칙은 없다. 하지만 일반적으로 파라미터는 어떠한 아이디 혹은 이름을 사용하여 조회할 때 사용하고 쿼리의 경우 검색어나 페이지에 필요한 옵션을 전달할 때 사용한다.

[React Router](https://reactrouter.com/web/guides/quick-start)
