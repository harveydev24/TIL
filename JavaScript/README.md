# JavaScripit

## JavaScrpit의 필요성

- 브라우저 화면을 '동적'으로 만들기 위함
- 브라우저를 조작하는 유일한 언어



## 브라우저에서 할 수 있는 일

- DOM (Document Object Model) 조작

  - DOM

    ![](README.assets/220px-DOM-model.svg.png)

    - HTML, XML과 같은 문서를 다루기 위한 프로그래밍 인터페이스
    - 문서를 구조화하고, 구조화된 구성 요소를 하나의 객체로 취급하여 다루는 논리적 트리 모델
    - 문서가 객체로 구조화되어 있으며, key로 접근 가능
    - 단순한 속성 접근, 메서드 활용뿐만 아니라 프로그래밍 언어적 특성을 활용한 조작 가능
    - 파싱 (Parsing)
      - 구문 분석, 해석
      - 브라우저가 문자열을 해석하여 DOM Tree로 만드는 과정

- BOM (Browser Object Model) 조작

  - BOM
    - 자바스크립트가 브라우저와 소통하기 위한 모델
    - 브라우저의 창이나 프레임을 추상화해서 프로그래밍적으로 제어할 수 있도록 제공하는 수단
      - 버튼, URL 입력창, 타이틀 바 등 브라우저 윈도우 및 웹 페이지 일부분을 제어 가능

- JavaScrpit Core (ECMAScript)
  - 브라우저 (BOM & DOM)을 조작하기 위한 명령어 약속(언어)
  - ECMA (ECMA International)
    - 정보 통신에 대한 표준을 제정하는 비영리 표준화 기구
    - ECMAScript는 ECMA에서 ECMA-262 규격에 따라 정의한 언어
    - ES6 (ECMAScript6)는 ECMA에서 제안하는 6번째 표준 명세를 의미



## 세미 콜론 (semicolon)

```javascript
const greeting = 'Hello, world!';
const greeting = 'Hello, world!'
```

- JS는 세미콜론을 선택적으로 사용 가능
  - 세미콜론이 없으면 ASI (Automatic Semicolon Insertion)에 의해 자동으로 세미콜론이 삽입됨



## 변수와 식별자

### 식별자의 정의와 특징

- 식별자(idenfier)는 변수를 구분할 수 있는 변수명을 의미
- 식별자는 반드시 문자, 달러($) 또는 밑줄(_)로 시작
- 대소문자를 구분하며, 클래스명 외에는 모두 소문자로 시작
- 예약어 사용 불가능
  - `for, if, function` 등



### 식별자 작성 스타일

- 카멜 케이스(camelCase, lower-camel-case)

  - 변수, 객체, 함수에 사용

    ```javascript
    const userInfo = { name: 'Tom', age: 20 }
    function getName() {}
    ```

- 파스칼 케이스(PascalCase, upper-camel-case)

  - 클래스, 생성자에 사용

    ```javascript
    class User {
        constructor(options) {
            this.name = options.name
        }
    }
    ```

- 대문자 스네이크 케이스(SNAKE_CASE)

  -  상수(constants)에 사용

    ```javascript
    const PI = Math.PI
    ```

    - 개발자의 의도와 상관없이 변경될 가능성이 없는 값



### 선언, 할당, 초기화

- 선언 (Declaration)
  - 변수를 생성하는 행위 또는 시점
- 할당 (Assignment)
  - 선언된 변수에 값을 저장하는 행위 또는 시점
- 초기화 (Initialization)
  - 선언된 변수에 처음으로 값을 저장하는 행위 또는 시점



### 변수 선언 키워드

- `let`
  - 재할당 할 예정인 변수 선언 시 사용
  - 변수 재선언 불가능
  - 블록 스코프
    - `it, for`이나 함수 등의 중괄호 내부
    - 블록 스코프를 가지는 변수는 블록 바깥에서 접근 불가능
- `const`
  - 재할당 할 예정이 없는 변수 선언 시 사용
  - 변수 재선언 불가능
  - 블록 스코프
- `var`
  - 재선언 및 재할당 모두 가능
  - ES6 이전에 주로 사용
  - 호이스팅되는 특성으로 인해 문제 발생 가능
    - 변수를 선언 이전에 참조할 수 있는 현상
    - 변수 선언 이전의 위치에서 접근 시 `undefined` 반환
  - 함수 스코프
  - `const`와 `let` 사용 권장



## 데이터 타입

- JS의 모든 값은 특정한 데이터 타입을 가짐



### 원시 타입 (Primitive type)

- 객체가 아닌 기본 타입

- 변수에 해당 타입의 값이 담김

- 다른 변수에 복사할 때, 실제 값이 복사됨

  ```javascript
  let msg = 'Hello'
  let msg2 = msg
  console.log(msg2) // Hello
  msg = 'Hi'
  console.log(msg2) // Hello
  ```

- 숫자 (Number) 타입

  - 정수, 실수 구분 없는 하나의 숫자 타입

  - 부동소수점 형식을 따름

    ```javascript
    const a = 1
    const b = -5
    const c = 3.14
    const d = Infinity
    const e = NaN
    ```

    - NaN (Not-A-Number)

      - 계산이 불가능한 경우 반환되는 값

        ```javascript
        console.log('a'/2) // Nan
        ```

- 문자열 (String) 타입

  - 텍스트 데이터를 나타내는 타입

  - 16비트 유니코드 문자의 집합

  - 작은따옴표, 큰따옴표 모두 사용 가능

    ```javascript
    const firstName = 'Harvey'
    const lastName = 'Kim'
    ```

  - 템플릿 리터럴 (Template Literal)

    - ES6부터 지원

    - 따옴표 대신 `(backtick)으로 표현

    - `${ expression }` 형태로 표현식 삽입

      ```javascript
      const fullName = `${firstName} ${lastName}`
      ```

- `undefined`

  - 변수의 값이 없음을 나타내는 데이터 타입

  - 변수 선언 이후 직접 값을 할당하지 않으면, 자동으로 `undefined`가 할당됨

    ```javascript
    let firstName
    console.log(firstName) // undefined
    ```

- `null`

  - 변수의 값이 없음을 의도적으로 표현할 때 사용하는 데이터 타입

    ```javascript
    let firstName = null
    console.log(firstName) // null
    ```

  - `null` 타입은 ECMA 명세의 원시타입의 정의에 따라 원시 타입에 속하지만, `typeof` 연산자의 결과는 객체로 표현됨

    ```javascript
    typeof null // object
    ```

- Boolean
  - 논리적 참 또는 거짓을 나타내는 타입
  - `true` 또는 `false`로 표현
  - 조건문 또는 반복문에서 유용하게 사용
    - 조건문 또는 반복문에서 boolean이 아닌 데이터 타입은 자동 형변환 규칙에 따라 `true` 또는 `false`로 변환됨



### 참조 타입 (Reference type)

- 객체 타입의 자료형

- 변수에 해당 객체의 참조 값이 담김

- 다른 변수에 복사할 때, 참조 값이 복사됨

  ```javascript
  const msg = ['Hello']
  let msg2 = msg
  console.log(msg2) // ['Hello']
  msg[0] = 'Hi'
  console.log(msg2) // ['Hi']
  ```

- 함수 (Functions)
- 배열 (Arrays)
- 객체 (Objects)



## 연산자

### 할당 연산자

- 오른쪽에 있는 피연산자의 평가 결과를 왼쪽 피연산자에 할당하는 연산자

- 다양한 연산에 대한 단축 연산자 지원

  ```javascript
  let x = 0
  x += 1
  x -= 1
  x *= 1
  x /= 1
  x++
  x--
  ```



### 비교 연산자

- 피연산자들 (숫자, 문자, Boolean 등)을 비교하고 결과값을 boolean으로 반환하는 연산자

- 문자열은 유니코드 값을 사용하며 표준 사전 순서를 기반으로 비교

  ```javascript
  const num = 1
  const num2 = 100
  console.log(num<num2) // true
  
  const char = 'a'
  const char2 = 'b'
  console.log(char>char2) // false
  ```



### 동등 비교 연산자 (==)

- 두 피연산자가 같은 값으로 평가되는지 비교 후 boolean 값을 반환

- 비교할 때, 암묵적 타입 변환을 통해 타입을 일치시킨 후 같은 값인지 비교

- 두 피연산자가 모두 객체일 경우 메모리의 같은 객체를 바라보는지 판별

- 예상치 못한 결과가 발생할 수 있으므로 특별한 경우를 제외하고 사용하지 않음

  ```javascript
  const a = 1
  const b = '1'
  console.log(a==b) // true
  
  const c = 1
  const d = true
  console.log(c==d) // true
  
  console.log(a+b) // 11
  console.log(c+d) // 2
  ```



### 일치 비교 연산자 (===)

- 두 피연산자가 같은 값으로 평가되는지 비교 후 boolean 값을 반환

- 두 비교 대상의 타입과 값이 모두 같은지 비교하는 엄격한 비교가 이뤄지며, 암묵적 타입 변환이 발생하지 않음

- 두 피연산자가 모두 객체일 경우 메모리의 같은 객체를 바라보는지 판별

  ```javascript
  const a = 1
  const b = '1'
  console.log(a===b) // false
  
  const c = 1
  const d = true
  console.log(c===d) // false
  
  ```



### 논리 연산자

- 세 가지 논리 연산자 ```&&, ||, !```로 구성

  ```javascript
  console.log(true && false) // false
  console.log(true || false) // true
  console.log(!true) // false
  ```



### 삼항 연산자 (Ternary Operator)

- 세 개의 피연산자를 사용하여 조건에 따라 값을 반환하는 연산자

- 가장 왼쪽 조건식이 참이면 콜론 앞의 값을 사용하고 그렇지 않으면 콜론 뒤의 값을 사용

- 삼항 연산자의 결과 값이기 때문에 변수에 할당 가능

  ```javascript
  console.log(true ? 1 : 2) // 1
  console.log(false ? 1 : 2) // 2
  
  const res = Math.PI > 4 ? 'Y' : 'N'
  console.log(res) // N
  ```















