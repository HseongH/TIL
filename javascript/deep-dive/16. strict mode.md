# Strict mode

## Strict mode란?

문법적 오류뿐만 아니라 잠재적 오류까지 찾아내어 에러를 발생시킨다. 이를 통해 잠재적인 오류를 억제하는 개발 환경을 만들 수 있다.

***

## stict mode의 적용

전역의 선두나 함수의 선두에 'use strict'; 를 추가한다.

***

## 전역에 strict mode를 적용하는 것은 피하자

전역에 사용하기 보단 코드를 즉시 실행 함수로 감싸고 즉시 실행 함수의 선두에 strict mode를 적용하자

***

## 함수 단위로 strict mode를 적용하는 것도 피하자

하나의 스크립트 내부에서 어떤 함수는 strict mode를 적용하고 어떤 함수는 strict mode를 적용하지 않는 것은 바람직하지 않다. 그렇다고 모든 함수에 일일히 strict mode를 적용하는 것은 번거로운 일이다. 함수 단위로 strict mode를 적용하기보단 즉시 실행 함수의 선두에 strict mode를 적용하자.

***

## strict mode가 발생시키는 에러

## strict mode 적용에 의한 변화

### 일반 함수의 this

생성자 함수로 호출하지 않은 일반 함수의 this에는 undefined가 바인딩된다. 생성자 함수가 아닌 일반 함수 내부에서는 this를 사용할 필요가 없기 때문이다.
