# ref

HTML에서 id를 사용해 DOM에 이름을 다는 것처럼 리액트 프로젝트 내부에서 DOM에 이름을 다는 방법이다.

**DOM을 직접적으로 건드려야 할 때** ref를 사용한다.

## 1. ref 사용하기

ref를 사용하는 방법은 두 가지가 있다.

### 1.1 콜백 함수를 통한 ref 설정

ref를 만드는 가장 기본적인 방법으로 ref를 달고자 하는 요소에 ref라는 콜백 함수를 props로 전달해주면 된다. 이 콜백 함수는 ref 값을 파라미터로 전달받고 함수 내부에서 파라미터로 받은 ref를 컴포넌트의 멤버 변수로 설정해준다.

```javascript
<input
  ref={(ref) => {
    this.input = ref;
  }}
/>
```

이렇게 하면 this.input은 input 요소의 DOM을 가리키게 된다. ref 이름은 원하는 대로 자유롭게 지정하여 사용할 수 있다.

### 1.2 createRef를 통한 ref 설정

리액트에 내장되어 있는 createRef 함수를 사용해 ref를 설정할 수 있다.

```javascript
import React from "react";

class RefPrac extends Component {
  constructor(props) {
    super(props);
    this.state = {};
    this.input = React.createRef();
  }

  render() {
    return <input ref={this.input} />;
  }
}

export default RefPrac;
```

ref를 설정한 뒤 DOM에 접근하려면 this.input.current를 조회하면 된다.
