# 컴포넌트 스타일링

## 1. SCSS

CSS 전처리기로 복잡한 작업을 쉽게 할 수 있도록 해 주고, 스타일 코드의 재사용성을 높여줄 뿐만 아니라 코드의 가독성을 높여 유지 보수를 더욱 쉽게 해준다.

[scss 기본 문법](https://heropy.blog/2018/01/31/sass/)

### 1.1 SCSS 사용

**node-scss 라이브러리 설치하기**

```
$ yarn add node-scss
```

**컴파일 하기**

```
$ node-sass [옵션] <입력파일경로> [출력파일경로]
```

```
$ node-sass scss/style.scss css/main.css
```

웹 브라우저에서는 표준 CSS 만이 동작하기 때문에 SCSS 파일을 CSS 파일로 컴파일하는 작업을 수행해야 한다.

옵션으로 --watch 또는 -w 입력 시 런타임 중 파일을 감시하여, 저장 시 자동으로 변경 사항을 컴파일한다.

```
$ node-sass --watch scss/style.scss css/main.css
```

---

## 2. styled-components

자바스크립트 파일 안에 스타일을 선언해 사용하게 해주는 라이브러리 중 하나이다.

**설치하기**

```
$ yarn add styled-components
```

**사용방법**

```javascript
import React from "react";
import styled from "styled-components";

function App() {
  return (
    <div className="App">
      <MyStyled bgColor={"red"}>hello React!</MyStyled>
    </div>
  );
}

const MyStyled = styled.div`
  width: 50vw;
  min-height: 150px;
  padding: 10px;
  border-radius: 15px;
  color: #fff;
  background-color: ${(props) => props.bgColor || "purple"};

  &:hover {
    background-color: #ddd;
  }
`;

export default App;
```

### 2.1 Tagged 템플릿 리터럴

위 코드를 보면 스타일 작성 시 ``(백틱)내에 스타일 정보를 넣어주는 것을 알 수 있다. 이것을 Tagged 템플릿 리터럴이라고 부른다.

Tagged 템플릿 리터럴 사용 시 템플릿 사이사이에 들어가는 자바스크립트 객체나 함수의 원본을 그대로 추출할 수 있다.

### 2.2 스타일링된 요소 만들기

파일 상단에 styled를 불러오고 styled.태그명을 사용하여 구현한다.

```javascript
import styled from "styled-components";

const MyStyled = styled.div`
  color: #333;
`;
```

Tagged 템플릿 리터럴 문법을 통해 스타일을 넣어 주면 해당 스타일이 적용된 HTML 요소가 만들어 진다.

### 2.3 스타일에서 props 사용하기

컴포넌트에서 전달된 props 값을 참조하여 스타일할 수 있다.

```javascript
const Contents = styled.div`
  background: ${(props) => props.bgColor || "green"};
`;
```
