# 객체 리터럴 (Object Literal)

## 1. 객체란?

자바스크립트는 객체 기반의 프로그래밍 언어이며, 자바스크립트를 구성하는 거의 모든 것이 객체이다. 원시 값을 제외한 나머지 값은 모두 객체이다.

원시 타입은 하나의 값만 나타내지만 객체 타입은 다양한 타입의 값(원시 값 또는 다른 객체)을 하나의 단위로 구성한 복합적인 자료구조다. 또한 **원시 타입의 값, 즉 원시 값은 변경 불가능한 값이지만 객체 타입의 값, 즉 객체는 변경 가능한 값**이다.

객체는 0개 이상의 프로퍼티로 구성된 집합이며, 프로퍼티는 키와 값으로 구성된다.

자바스크립트에서 사용할 수 있는 모든 값은 프로퍼티 값이 될 수 있다. 자바스크립트의 함수는 일급 객체이므로 값으로 취급할 수 있다. 따라서 함수도 프로퍼티 값으로 사용할 수 있다. 프로퍼티 값이 함수일 경우 일반 함수와 구분하기 위해 메서드라 부른다.

이처럼 객체는 프로퍼티와 메서드로 구성된 집합체다.

> - 프로퍼티: 객체의 상태를 나다타내는 값
> - 메서드: 프로퍼티(상태 데이터)를 참조하고 조작할 수 있는 동작

이처럼 객체는 객체의 상태를 나타내는 값(프로퍼티)과 프로퍼티를 참조하고 조작할 수 있는 동작(메서드)을 모두 포함할 수 있기 때문에 상태와 동작을 하나의 단위로 구조화할 수 있어 유용하다.

***

## 2. 객체 리터럴에 의한 객체 생성

C++나 자바 같은 클래스 기반 객체지향 언어는 클래스를 사전에 정의하고 필요한 시점에 new 연산자와 함께 생성자를 호출하여 인스턴스를 생성하는 방식으로 객체를 생성한다.

자바스크립트는 프로토타입 객체 지향 언어로서 다양한 객체 생성 방법을 지원한다.

- 객체 리터럴
- Object 생성자 함수
- 생성자 함수
- Object.create 메서드
- 클래스 (ES6)

이러한 방법 중 가장 일반적이고 간단한 방법은 객체 리터럴을 사용하는 방법이다. 리터럴은 사람이 이해할 수 있는 문자나 약속된 기호를 사용해 값을 생성하는 표기법이다. 객체 리터럴은 객체를 생성하기 위한 표기법이다.

객체 리터럴은 중괄호 ({ ... }) 내에 0개 이상의 프로퍼티를 정의한다. 변수에 할당되는 시점에 자바스크립트 엔진은 객체 리터럴을 해석해 객체를 생성한다.

```javascript
var person ={
    name: 'Hong',
    sayHello: function() {
        console.log(`Hello ${this.name}.`);
    }
};

console.log(person);    // {name: "Hong", sayHello: ƒ}
```

중괄호 내에 프로퍼티를 정의하지 않으면 빈 객체가 생성된다.

```javascript
var empty = {};
console.log(empty); // {}
```

객체 리터럴의 중괄호는 코드 블록을 의미하지 않는 데에 주의하자 코드 블록의 닫는 중괄호 뒤에는 세미콜론을 붙이지 않는다. 하지만 객체 리터럴은 값으로 평가되는 표현식이다. 따라서 객체 리터럴의 닫는 중괄호 뒤에는 세미콜론을 붙인다.

객체 리터럴은 자바스크립트의 유연함과 강력함을 대표하는 객체 생성 방식이다. 객체를 생성하기 위해 클래스를 먼저 정의하고 new 연산자와 함께 생성자를 호출할 필요가 없다. 숫자 값이나 문자열을 만드는 것과 유사하게 리터럴로 객체를 생성한다. 객체 리터럴에 프로퍼티를 포함시켜 객체를 생성함과 동시에 프로퍼티를 만들 수도 있고, 객체를 생성한 이후에 프로퍼티를 동적으로 추가할 수도 있다.

객체 리터럴 외의 객체 생성 방식은 모두 함수롤 사용해 객체를 생성한다.

***

## 3. 프로퍼티

**객체는 프로퍼티의 집합이며, 프로퍼티는 키와 값으로 구성된다.**

```javascript
var person = {
    name: 'Hong',
    age: 23
};
```

프로퍼티를 나열할 때는 쉼표(,)로 구분한다. 일반적으로 마지막 프로퍼티 뒤에는 쉼표를 사용하지 않으나 사용해도 좋다.

- 프로퍼티 키: 빈 문자열을 포함하는 모든 문자열 또는 심벌 값
- 프로퍼티 값: 자바스크립트에서 사용할 수 있는 모든 값

프로퍼티 키는 프로퍼티 값에 접근할 수 있는 이름으로서 식별자 역할을 한다. 하지만 반드시 식별자 네이밍 규칙을 따라야 하는 것은 아니다. 단, 식별자 네이밍 규칙을 준수하는 프로퍼티 키와 그렇지 않은 프로퍼티 키는 미묘한 차이가 있다.

심벌 값도 프로퍼티 키로 사용할 수 있지만 일반적으로 문자열을 사용한다. 이때 프로퍼티 키는 문자열이므로 따옴표 (" ... ", ' ... ')로 묶어야 한다. 하지만 식별자 네이밍 규칙을 준수하는 이름은 따옴표를 생략할 수 있다. 반대로 말하면 **식별자 네이밍 규칙을 준수하지 않는 이름에는 반드시 따옴표를 사용해야 한다.**

식별자 네이밍 규칙을 따르지 않는 프로퍼티 키를 사용하면 번거로운 일이 발생한다. 따라서 가급적 식별자 네이밍 규칙을 준수하는 프로퍼티 키를 사용할 것을 권장한다.

```javascript
var person = {
    firstName: 'seonghun',
    'last-name': 'Hong'
};

console.log(person);    // {firstName: "seonghun", last-name: "Hong"}
```

식별자 네이밍을 준수하지 않은 이름 last-name은 따옴표를 생략하는 경우 last - name, - 연산자가 있는 표현식으로 해석한다.

```javascript
var person = {
    firstName: 'seonghun',
    last-name: 'Hong'
};  // Uncaught SyntaxError: Unexpected token '-'
```

문자열 또는 문자열로 평가되는 표현식을 사용해 프로퍼티 키를 동적으로 생성할 수도 있다. 이 경우에는 프로퍼티로 사용할 표현식을 대괄호([ ... ])로 묶어야 한다.

```javascript
var obj = {};
var key = 'Hello';

// ES5
obj[key] = 'world';
// ES6: 계산된 프로퍼티 이름
// var obj = { [key]: 'world' };

console.log(obj);   // {Hello: "world"}
```

빈 문자열을 프로퍼티 키로 사용할 수 있지만, 키로서의 의미를 갖지 못하므로 권장하지 않는다.

프로퍼티 키에 문자열이나 심벌 값 외의 값을 사용하면 암묵적 타입 변환을 통해 문자열이 된다. 예를 들어, 숫자 리터럴을 사용하면 따옴표는 붙지 않지만 내부적으로는 문자열로 변환된다.

```javascript
var foo = {
    0: 1,
    1: 2,
    2: 3
};
```

예약어를 프로퍼티 키로 사용할 수 있지만 예상치 못한 에러가 발생할 수 있으므로 권장하지 않는다.

이미 존재하는 프로퍼티 키를 중복으로 선언 시 나중에 선언된 프로퍼티가 먼저 선언한 프로퍼티를 덮어쓴다.

```javascript
var foo = {
    name: 'Hong',
    name: 'seonghun'
};

console.log(foo);   // {name: "seonghun"}
```

***

## 4. 메서드

자바스크립트에서 사용할 수 있는 모든 값은 프로퍼티 값으로 사용할 수 있다고 했다. 함수는 객체(일급 객체)다. 따라서 함수는 값으로 취급할 수 있기 때문에 프로퍼티 값으로 사용할 수 있다.

프로퍼티 값이 함수일 경우 일반 함수와 구분하기 위해서 메서드라 부른다. 즉 메서드는 객체에 묶여 있는 함수를 의미한다.

```javascript
var circle = {
    radius: 5,
    getDiameter: function() {
        return 2 * this.radius;
    }
};
```

메서드 내부에서 사용한 this 키워드는 객체 자신을 가리키는 참조변수다.

***

## 5. 프로퍼티 접근

프로퍼티에 접근하는 방법은 다음과 같다.

- 마침표 프로퍼티 접근 연산자(.)를 사용하는 마침표 표기법
- 대괄호 프로퍼티 접근 연산자([ ... ])를 사용하는 대괄호 표기법

프로퍼티 키가 식별자 네이밍을 준수하는 이름, 즉 자바스크립트에서 사용 가능한 유효한 이름이면 마침표 표기법과 대괄호 표기법을 모두 사용할 수 있다.

마침표 프로퍼티 접근 연산자 또는 대괄호 프로퍼티 접근 연산자의 좌측에는 객체로 평가되는 표현식을 기술하고, 마침표 표기법 우측 또는 대괄호 표기법의 대괄호 안쪽에는 프로퍼티 키를 기술한다.

```javascript
var person = {
    name: 'Hong'
};

console.log(person.name);   // Hong
console.log(person['name']);    // Hong
```

대괄호 표기법을 사용하는 경우 **대괄호 프로퍼티 접근 연산자 내부에 지정하는 프로퍼티 키는 반드시 따옴표로 감싼 문자열**이어야 한다. 대괄호 프로퍼티 접근 연산자 내에 따옴표로 감싸지 않은 이름을 프로퍼티 키로 사용하면 자바스크립트 엔진은 식별자로 해석한다.

```javascript
var person = {
    name: 'Hong'
};

console.log(person[name]);  // ReferenceError: name is not defined
```

위 예제에서 참조 에러가 발생한 이유는 대괄호 연산자 내의 따옴표로 감싸지 않은 이름, 즉 식별자 name을 평가하기 위해 선언된 name을 찾았지만 찾지 못했기 때문이다.

**객체에 존재하지 않는 프로퍼티에 접근하면 undefined를 반환한다.**

```javascript
var person = {
    name: 'Hong'
};

console.log(person.age);    // undefined
```

프로퍼티 키가 네이밍 규칙을 준수하지 않는 이름인 경우 반드시 대괄호 표기법을 사용해야 한다. 단 프로퍼티 키가 숫자로 이루어진 문자열인 경우 따옴표를 생략할 수 있다.

```javascript
var person = {
    'last-name': 'Hong',
    1: 10
};

person.'last-name'; // SyntaxError: Unexpected string
person.last-name;   // 브라우저: NaN
                    // node.js: ReferenceError
person[last-name];  // ReferenceError: last is not defined
person['last-name'];// Hong

person.1;    // SyntaxError: Unexpected number
person.'1';  // SyntaxError: Unexpected string
person[1];   // 10: person[1] -> person['1']
person['1']; // 10
```

위 코드에서 person.last-name의 실행 결과가 node.js 환경과 브라우저 환경이 서로 다르다.

person.last-name을 평가할 때 자바스크립트 엔진은 person.last를 평가한다. person 객체 내에 last라는 프로퍼티가 없으므로 undefined로 평가된다. 이후 name이라는 식별자를 찾는다. 이때 name은 식별자로 해석된다.

현재 name이라는 식별자는 존재하지 않기 때문에 ReferenceError: last is not defined가 발생한다. 그런데 브라우저 환경에서는 name이라는 전역 변수(전역 객체 window의 프로퍼티)가 암묵적으로 존재한다. 전역 변수 name은 window의 이름을 가리키며 기본값은 빈 문자열이다. 따라서 undefined - ''의 연산 결과인 NaN을 반환하게 된다.

***

## 6. 프로퍼티 값 갱신

이미 존재하는 프로퍼티에 값을 할당하면 프로퍼티 값이 갱신된다.

```javascript
var person = {
    name: 'Hong'
};

person.name = 'Kim';

console.log(person.name);   // Kim
```

***

## 7. 프로퍼티 동적 생성

존재하지 않는 프로퍼티에 값을 할당하면 프로퍼티가 동적으로 생성되어 프로퍼티 값이 할당된다.

```javascript
var person = {
    name: 'Hong'
};

person.age = 23;

console.log(person);    // {name: "Hong", age: 23}
```

***
 
## 8. 프로퍼티 삭제

delete 연산자는 프로퍼티를 삭제한다. 이때 delete 연산자의 피연산자는 프로퍼티 값에 접근할 수 있는 표현식이어야 한다. 만약 존재하지 않는 프로퍼티를 삭제하면 아무런 에러 없이 무시된다.

```javascript
var person = {
    name: 'Hong',
    age: 23
};

delete person.age;

delete person.address;

console.log(person);    // {name: "Hong"}
```

***

## 9. ES6에서 추가된 객체 리터럴의 확장 기능

### 9.1 프로퍼티 축약 표현

객체 리터럴의 프로퍼티는 프로퍼티 키와 값으로 구성된다. 프로퍼티 값은 변수에 할당된 값, 즉 식별자 표현식일 수도 있다.

```javascript
// ES5
var x = 1, y = 2;

var obj = {
    x: x,
    y: y
};

console.log(obj);   // {x: 1, y: 2}
```

ES6에서는 프로퍼티 값으로 변수를 사용하는 경우 변수 이름과 프로퍼티 키가 동일한 이름일 때 프로퍼티 키를 생략할 수 있다. 이때 프로퍼티 키는 변수 이름으로 자동 생성된다.

```javascript
// ES6
var x = 1, y = 2;

var obj = { x, y };

console.log(obj);   // {x: 1, y: 2}
```

### 9.2 계산된 프로퍼티 이름

문자열 또는 문자열로 타입 변환할 수 있는 값으로 평가되는 표현식을 사용해 프로퍼티 키를 동적으로 생성할 수도 있다. 단, 프로퍼티 키로 사용할 표현식을 대괄호로 묶어야 한다. 이를 계산된 프로퍼티 이름이라 한다.

ES5에서 계산된 프로퍼티 이름으로 프로퍼티 키를 동적 생성하려면 객체 리터럴 외부에서 대괄호 표기법을 사용해야 한다.

```javascript
// ES5
var prefix = 'prop';
var i = 0;

var obj = {};

obj[prefix + '-' + ++i] = i;
obj[prefix + '-' + ++i] = i;
obj[prefix + '-' + ++i] = i;

console.log(obj);   // {prop-1: 1, prop-2: 2, prop-3: 3}
```

ES6에서는 객체 리터럴 내부에서도 계산된 프로퍼티 이름으로 프로퍼티 키를 동적 생성할 수 있다.

```javascript
// ES6
const prefix = 'prop';
let i = 0;

const obj = {
    [`${prefix}-${++i}`]: i,
    [`${prefix}-${++i}`]: i,
    [`${prefix}-${++i}`]: i
};

console.log(obj);   // {prop-1: 1, prop-2: 2, prop-3: 3}
```

### 9.3 메서드 축약 표현

ES5에서 메서드를 정의하려면 프로퍼티 값으로 함수를 할당한다.

```javascript
// ES5
var obj = {
    name: 'Hong',
    sayHi: function() {
        console.log('Hi ' + this.name);
    }
};

obj.sayHi();  // Hi Hong
```

ES6에서는 메서드를 정의할 때 function 키워드를 생략한 축약 표현을 사용할 수 있다.

```javascript
// ES6
const obj = {
    name: 'Hong',
    sayHi() {
        console.log(`Hi ${this.name}`);
    }
};

obj.sayHi();  // Hi Hong
```
