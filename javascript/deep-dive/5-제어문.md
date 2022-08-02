# 제어문 (Control Flow Statement)

조건에 따라 코드 블록을 실행(조건문)하거나 반복 실행(반복문)할 때 사용한다. 일반적으로 코드는 위에서 아래로 순차적으로 실행하는데, 제어문을 사용하면 코드의 실행 흐름을 인위적으로 제어할 수 있다.

하지만 코드의 실행 순서가 변경되면 단순히 위에서부터 순차적으로 진행하는 직관적인 코드의 흐름을 혼란스럽게 만든다. 따라서 제어문은 코드의 흐름을 이해하기 어렵게 만들어 가독성을 해치는 단점이 있다.

***

## 1. 블록문

블록문은 0개 이상의 문을 중괄호로 묶은 것으로, 코드 블록 또는 블록이라고 부른다. 자바스크립트는 블록문을 하나의 실행 단위로 취급한다. 단독으로 사용하는 것도 가능하지만 일반적으로 제어문이나 함수 정의 시 사용한다.

```javascript
{
    var foo = 10;
}

var x = 1;
if (x < 10) {
    x++;
}

function sub(a, b) {
    return a - b;
}
```

***

## 2. 조건문

조건문은 주어진 조건식의 평가 결과에 따라 코드 블록의 실행을 결정한다. 조건식은 불리언 값으로 평가될 수 있는 표현식이다.

자바스크립트는 if ... else 문과 switch 문으로 두 가지 조건문을 제공한다.

### 2.1 if ... else 문

if ... else 문은 조건식의 평가 결과, 즉 논리적 참 거짓에 따라 실행할 코드 블록을 결정한다. 조건식의 평가 결과 true일 경우 if 문의 코드 블록이 실행되고, false일 경우 else문이 실행된다.

```javascript
if (조건식) {
    // 조건식이 참일 때 실행
} else {
    // 조건식이 거짓일 때 실행
}
```

if 문의 조건식은 불리언 값으로 평가되어야 한다. 만약 조건식이 불리언 값이 아닐 경우 불리언 타입으로 암묵적 타입 변환이 수행된다.

조건식을 추가하고 싶다면 else if 문을 사용한다.

```javascript
if (조건식1) {
    // 조건식1이 참일 때 실행
} else if (조건식2) {
    // 조건식1이 거짓이고 조건식2가 참일 때 실행
} else {
    // 조건식이 모두 거짓일 때 실행
}
```

else if 문과 else 문은 옵션으로 사용하지 않을 수 있다. else if 문의 경우 여러 번 사용이 가능하지만 if 문과 else 문의 경우 한 번만 사용해야 한다.

코드 블록 내의 문이 하나라면 중괄호를 생략할 수 있다.

```javascript
var age = 20;

if (age > 19) console.log('성인');
else if (age > 13) console.log('청소년');
else console.log('어린이');
```

## 2.2 switch 문

switch 문은 주어진 표현식을 평가하여 그 값과 일치하는 표현식을 갖는 case 문으로 실행 흐름을 옮긴다. case 문은 상황을 의미하는 표현식을 지정하고 콜론으로 마친다. 그리고 그 뒤에 실행할 문들을 위치시킨다.

switch 문의 표현식과 일치하는 case 문이 없다면 실행 순서는 default 문으로 이동한다. default 문은 선택사항으로, 사용하지 않을 수도 있다.

```javascript
switch (표현식) {
    case 표현식1:
        // switch 문의 표현식과 일치하면 실행
        break;
    case 표현식2:
        // switch 문의 표현식과 일치하면 실행
        break;
    default:
        // switch 문의 표현식과 일치하는 case 문이 없을 때 실행
}
```

if ... else 문의 조건식은 불리언 값으로 평가되어야 하지만 switch 문의 경우 불리언 값보단 문자열이나 숫자 값인 경우가 많다. 즉 if ... else 문의 경우 논리적 참, 거짓으로 실행할 코드 블록을 결정할 때 사용하고, switch 문의 경우 다양한 상황(case)에 따라 실행할 코드 블록을 결정할 때 사용한다.

```javascript
var month = 11;
var monthName;

switch (month) {
    case 1: monthName = 'January';
    case 2: monthName = 'February';
    case 3: monthName = 'March';
    case 4: monthName = 'April';
    case 5: monthName = 'May';
    case 6: monthName = 'June';
    case 7: monthName = 'July';
    case 8: monthName = 'August';
    case 9: monthName = 'September';
    case 10: monthName = 'October';
    case 11: monthName = 'November';
    case 12: monthName = 'December';
    default: monthName = 'Invalid month';
}

console.log(monthName); // Invalid month
```

위 예제의 결과 November가 출력되지 않고 Invalid month가 출력된다. 이는 switch 문의 표현식의 결과와 일치하는 case 문으로 실행 흐름이 이동하여 문을 실행한 것은 맞지만 문을 실행한 후 switch 문을 탈출하지 않고 switch 문이 끝날 때까지 이후의 모든 case 문과 default 문을 수행했기 때문이다. 이를 **폴스루**라 한다. 다시 말해 monthName에 November가 할당된 것은 맞지만 이후 December, Invalid month가 재할당된 것이다.

올바른 switch 문은 case 문의 마지막에 break 문을 사용해 case 문의 표현식과 일치한 경우 코드 블록을 실행한 후 switch 문을 빠져나가게 구성해야 한다.

```javascript
var month = 11;
var monthName;

switch (month) {
    case 1:
        monthName = 'January';
        break;
    case 2:
        monthName = 'February';
        break;
    case 3:
        monthName = 'March';
        break;
    case 4:
        monthName = 'April';
        break;
    case 5:
        monthName = 'May';
        break;
    case 6:
        monthName = 'June';
        break;
    case 7:
        monthName = 'July';
        break;
    case 8:
        monthName = 'August';
        break;
    case 9:
        monthName = 'September';
        break;
    case 10:
        monthName = 'October';
        break;
    case 11:
        monthName = 'November';
        break;
    case 12:
        monthName = 'December';
        break;
    default: monthName = 'Invalid month';
}

console.log(monthName); // November
```

default 문은 switch 문의 마지막에 위치하므로 default 문의 실행이 종료되면 switch 문을 빠져나간다. 따라서 default 문에는 break 문을 생략한다.

switch 문은 폴스루가 발생하는 등 문법적으로 복잡하기 때문에 if ... else 문으로 해결이 가능한 경우 if ... else 문을 사용하는 것이 좋다. 하지만 평가해야 할 조건이 너무 많다면 switch 문을 사용하는 것이 가독성이 더 좋다.

***

## 3. 반복문

반복문은 조건식의 평가 결과가 거짓일 때 까지 코드 블록을 반복해서 수행한다.

자바스크립트는 for 문, while 문, do ... while 문의 반복문을 제공한다.

### 3.1 for 문

for 문은 조건식이 거짓으로 평가될 때까지 코드 블록을 반복 실행한다.

```javascript
for (변수 선언문; 조건식; 증감식) {
    // 조건식이 참일 경우 실행
}
```

```javascript
for (var i = 0; i < 2; i++) {
    console.log(i);
}
```

```
0
1
```

위 코드의 실행 순서는 다음과 같다.

> 1. for 문을 실행하면 변수 선언문 var i = 0이 실행된다. 변수 선언문은 단 한번만 실행된다.
> 2. 조건식이 실행된다. i는 0이므로 조건식 평가 결과 true이다.
> 3. 증감식이 실행되기 이전에 코드 블록이 실행된다.
> 4. 증감식이 실행되어 i는 1이 된다.
> 5. 조건식을 실행한다. i는 1이므로 조건식 평가 결과 true이다.
> 6. 코드 블록이 실행된다.
> 7. 증감식이 실행되어 i는 2가 된다.
> 8. 조건식 평가 결과 false 이므로 코드 블록을 실행하지 않고 for 문을 종료한다.

for 문의 변수 선언문, 조건식, 증감식은 모두 옵션으로 사용하지 않아도 된다. 하지만 어떤 식도 선언하지 않으면 무한히 반복되는 무한루프가 된다.

```javascript
for (;;) { ... }
```

for 문 내에 for 문을 중첩해 사용할 수 있다. 이를 중첩 for 문이라 한다.

```javascript
for (var i = 1; i <= 6; i++) {
    for (var j = 1; j <= 6; j++) {
        if (i + j === 6) console.log(i, j);
    }
}
```

```
1 5
2 4
3 3
4 2
5 1
```

### 3.2 while 문

while 문은 주어진 조건식의 평가 결과 참이면 코드 블록을 반복 실행한다. for 문은 반복 횟수가 명확할 때 주로 사용하고 while 문은 반복 횟수가 불명확할 때 주로 사용한다.

while 문은 조건문의 평가 결과가 거짓이면 코드 블록을 실행하지 않고 종료한다. 만약 조건식의 평가 결과 불리언 값이 아니라면 불리언 값으로 암묵적 타입 변환이 수행된다.

```javascript
var count = 0;

while (count < 3) {
    console.log(count); // 0, 1, 2
    count++;
}
```

조건식의 평가 결과 언제나 참이면 무한루프가 된다.

```javascript
while (true) { ... }
```

### 3.3 do ... while 문

do ... while 문은 코드 블록을 먼저 실행하고 조건식을 평가한다. 따라서 코드 블록이 무조건 한 번 이상 실행된다.

```javascript
var count = 0;

do {
    console.log(count); // 0, 1, 2
    count++;
} while (count < 3);
```

## 4. break 문

break 문은 코드 블록을 탈출한다. 좀 더 정확히 표현하면 코드 블록을 탈출하는 것이 아니라 레이블 문, 반복문 또는 switch 문의 코드 블록을 탈출한다. 레이블 문, 반복문, switch 문 코드 블록 이외에 break 문 사용 시 SyntaxError(문법 에러)가 발생한다.

```javascript
if (true) {
    break;  // Uncaught SyntaxError: Illegal break statement
}
```

레이블 문은 식별자가 붙은 문을 말한다.

```javascript
foo: console.log('foo');
```

레이블 문은 프로그램의 실행 순서를 제어하는 데 사용된다. switch 문의 case 문과 default 문도 레이블 문이다. 레이블 문을 탈출하기 위해선 break 문에 레이블 식별자를 지정한다.

```javascript
foo: {
    console.log(1);
    break foo;
    console.log(2);
}

console.log('Done!');
```

중첩된 for 문의 내부 for 문에서 break 실행 시 내부 for 문을 탈출하여 외부 for 문으로 진입하게 된다. 이때 내부 for 문이 아닌 외부 for 문을 탈출하려면 레이블 문을 사용한다.

```javascript
outer: for (var i = 0; i < 3; i++) {
    for (var j = 0; j < 3; j++) {
        if (i + j == 3) break outer;
        console.log(i, j);
    }
}
```

레이블 문을 사용하면 프로그램의 흐름이 복잡해져 가독성이 나빠지고 오류를 발생시킬 가능성이 높다. 따라서 레이블 문은 중첩 for문을 빠져나가는 용도 외에는 사용하지 않는 것이 좋다.

break 문을 레이블 문 이외의 반복문, switch 문에서 사용 시 break 뒤에 식별자를 지정하지 않는다.

## 5. continue 문

continue 문은 반복문의 코드 블록 실행을 현 지점에서 중단하고 반복문 증감식으로 실행 흐름을 이동시킨다. break 문처럼 반복문을 탈출하지는 않는다.

```javascript
var string = 'Hello World';
var search = 'l';
var count = 0;

for (var i = 0; i < string.length; i++) {
    if (string[i] !== search) continue;
    count++;
}
```

위 코드는 다음 코드와 동일하게 동작한다.

```javascript
var string = 'Hello World';
var search = 'l';
var count = 0;

for (var i = 0; i < string.length; i++) {
    if (string[i] === search) count++;
}
```

위와 같이 if 문 내의 코드가 한 줄이라면 continue 문보다 if 문을 사용했을 때 더 간편하고 가독성도 좋다. 하지만 if 문 내의 코드가 길다면 들여쓰기가 한 단계 더 깊어지므로 continue 문을 사용하는 편이 가독성이 더 좋다.

```javascript
var string = 'Hello World';
var search = 'l';
var count = 0;

for (var i = 0; i < string.length; i++) {
    if (string[i] === search) {
        count++;
        // 코드
        // 코드
        // 코드
        // 코드
    }
}

for (var i = 0; i < string.length; i++) {
    if (string[i] !== search) continue;

    count++;
    // 코드
    // 코드
    // 코드
    // 코드
}
```
