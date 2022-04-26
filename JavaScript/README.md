# JavaScripit

## JavaScrpit의 필요성

- 브라우저 화면을 '동적'으로 만들기 위함
- 브라우저를 조작하는 유일한 언어

<br>

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



<br>

## 세미 콜론 (semicolon)

```javascript
const greeting = 'Hello, world!';
const greeting = 'Hello, world!'
```

- JS는 세미콜론을 선택적으로 사용 가능
  - 세미콜론이 없으면 ASI (Automatic Semicolon Insertion)에 의해 자동으로 세미콜론이 삽입됨



<br>

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



<br>

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



<br>

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





<br>

## 조건문

### `if`

- 조건식 표현식의 결과값을 boolean 타입으로 변환 후 참/거짓을 판단

- 소괄호 안에 조건 작성

- 중괄호 안에 실행할 코드 작성

- 브록 스코프 생성

  ```javascript
  if (condition) {
      // do something
  } else if (condition) {
      // do something
  } else {
      // do something
  }
  ```

  



### `switch`

- 조건 표현식의 결과값이 어느 값(case)에 해당하는지 판별

- 주로 특정 변수 값에 따라 조건을 분기할 때 사용

  - 조건이 많아질 경우 `if`문보다 가독성이 나음

- `break` 및 `defaul`문은 선택적으로 사용 가능

  - `break`문이 없는 경우 `break`문을 만나거나 `default`문을 실행할 때 까지 다음 조건문 실행

- 블록 스코프 생성

  ```javascript
  switch(expression) {
      case 'first value': {
          // do something
          break
      }
      case 'second value' {
          // do something
          break
  	}
  	default: {
      	// do something
  	}
  }
  ```



<br>

## 반복문

### `while`

- 조건문이 `true`인 동안 반복 시행

- 조건은 소괄호 안에 작성

- 실행할 코드는 중괄호 안에 작성

- 블록 스코프 생성

  ```javascript
  let i = 0
  
  while (i<6) {
      console.log(i)
      i += 1
  }
  ```

  



### `for`

- 세미콜론으로 구분되는 세 부분으로 구성

- initialization

  - 최초 반복문 진입 시 1회만 실행되는 부분

- condition

  - 매 반복 시행 전 평가되는 부분

- expression

  - 매 반복 시행 이후 평가되는 부분

- 블록 스코프 생성

  ```javascript
  for (let i = 0; i < 6; i ++) {
      console.log(i)
  }
  ```

  

### ```for ... in ```

- 객체(object)의 속성(key)들을 순회할 때 사용

  - JS에서 객체는 Python의 딕셔너리와 같음

- 배열도 순회 가능하지만 권장하지 않음

- 실행할 코드는 중괄호 안에 작성

- 블록 스코프 생성

  ```javascript
  const capitals = {
      korea: 'seoul',
      france: 'paris',
      USA: 'washington D.C.'
  }
  
  for (let capital in cpaitals) {
      console.log(capital)
  }
  ```





### `for ... of`

- 반복 가능한 객체를 순회하며 값을 꺼낼 때 사용

- 실행할 코드는 중괄호 안에 작성

- 블록 스코프 생성

  ```javascript
  const fruits = ['strawberry', 'melon', 'banana']
  
  // fruit 재할당 가능
  for (let fruit of fruits) {
      fruit = fruit + '!'
      console.log(fruit)
  }
  
  // fruit 재할당 불가
  for (const fruit of fruits) {
      console.log(fruit)
  }
  ```


<br>

## 함수

- 참조 타입 중 하나로써 `function` 타입에 속함

- JS의 함수는 일급 객체에 해당

  - 변수에 할당 가능
  - 함수의 매개 변수로 전달 가능
  - 함수의 반환 값으로 사용 가능

- 함수 선언식

  - 함수의 이름과 함께 정의하는 방식

    ```javascript
    function name(args) {
        // do something
    }
    
    // 기본 인자
    function name(args="default") {
        // do something
    }
    ```

  - 함수 선언식으로 선언한 함수는 `var`로 정의한 변수처럼 hoisting 발생

  - 함수 호출 이후에 선언 해도 동작

    ```javascript
    add(2,6)
    
    function add (a, b) {
        return a + b
    }
    ```

    

- 함수 표현식

  - 함수를 표현식 내에서 정의하는 방식
  - 함수 표현식으로 선언한 함수는 함수 정의 전에 호출 시 에러 발생
    - 함수 표현식으로 정의된 함수는 변수로 평가되어 변수의 scope 규칙을 따름

  - 함수의 이름을 생략하고 익명 함수로 정의 가능

    ```javascript
    const name = function (args) {
        // do something
    }
    
    // 기본 인자
    const name = function (args="default") {
        // do something
    }
    ```

  - 매개 변수와 인자의 개수 불일치 허용

    ```javascript
    const twoArgs = function (a, b) {
        return [a,b]
    }
    
    twoArgs(1,2,3) // [1,2]
    twoArgs(1) // [1, undefined]
    ```

  - `...`을 통해 정해지지 않은 수의 매개변수를 인자로 받을 수 있음

    ```javascript
    const restOpr = function (a, b, ...restArgs) {
        return [a, b, restArgs]
    }
    
    restArgs(1,2,3,4,5) // [1,2,[3,4,5]]
    restArgs(1,2) // [1,2,[]]
    ```

  - `...`을 통해 배열 인자를 전개하여 전달 가능

    ```javascript
    const spreadOpr = function (a, b) {
        return a + b
    }
    
    const numbers = [1,2]
    spreadOpr(...numbers) // 3
    ```

<br>



## Arrow Function

- 함수를 비교적 간결하게 정의할 수 있는 문법

  ```javascript
  const arrow1 = function (name) {
      return 'hi, ${name}'
  }
  
  // function 키워드 생략 가능
  const arrow2 = (name) => {
      return 'hi, ${name}'
  }
  
  // 매개변수가 1개일 경우에만 소괄호 생략 가능
  const arrow3 = name => {
      return 'hi, ${name}'
  }
  
  // 함수 바디가 return을 포함한 표현식 1개일 경우에 중괄호와 return 생략 가능
  const arrow4 = name => 'hi, ${name}'
  ```

<br>



## 문자열 (String)

- 문자열 관련 주요 메서드

  ```javascript
  const str = 'a santa at nasa'
  
  str.includes('santa') // true
  str.includes('asan') // false
  
  const str = 'a cup'
  str.split() // ['a cup']
  str.split('') // ['a', ' ', 'c', 'u', 'p']
  str.split(' ') // ['a', 'cup']
  
  const str = 'a b c d'
  str.replace(' ', '-') // 'a-b c d'
  str.replaceAll(' ', '-') // 'a-b-c-d'
  
  const str = '   hello   '
  str.trim() // 'hello'
  str.trimStart() // 'hello   '
  str.trimEnd() // '   hello'
  ```

  

<br>



## 배열 (Arrays)

- 키와 속성들을 담고 있는 참조 타입의 객체 (object)

- 순서를 보장

- 대괄호를 이용하여 생성하고, 인덱스로 접근

  ```javascript
  const numbers = [1,2,3,4,5]
  console.log(numbers[0]) // 1
  console.log(numbers[-1]) // undefined
  console.log(numbers.length) // 5
  ```

- 배열 관련 주요 메서드

  ```javascript
  const numbers = [1,2,3,4,5]
  
  number.reverse()
  console.log(numbers) // [5,4,3,2,1]
  
  number.push(100)
  console.log(numbers) // [1,2,3,4,5,100]
  
  number.pop()
  console.log(numbers) // [1,2,3,4,5]
  
  number.unshift(100)
  console.log(numbers) // [100,1,2,3,4,5]
  
  number.shift()
  console.log(numbers) // [1,2,3,4,5]
  
  console.log(numbers.includes(1)) // true
  console.log(numbers.includes(100)) // false
  
  console.log(numbers.indexOf(3)) // 2
  console.log(numbers.indexOf(100)) // -1
  
  console.log(numbers.join()) // 1,2,3,4,5
  console.log(numbers.join('')) // 12345
  console.log(numbers.join('-')) // 1-2-3-4-5
  
  const array = [1,2,3]
  const newArray = [0, ..., 4]
  console.log(newArray) // [0,1,2,3,4]
  
  
  const array = ['a','b','c','d']
  // index 생략 가능
  array.forEach((element, index) => {
      console.log(element, index)
      // a 0
      // b 1
      // c 2
      // d 3
  })
  
  const newArray = array.map((element) => {
      return element + '1'
  })
  console.log(newArray) // ['a!', 'b!', 'c!', 'd!']
  
  const newArray = array.filter((element) => {
      return element === 'a'
  })
  console.log(newArray) // ['a']
  
  const result = array.reduce((acc, element) => {
      return acc + element
  }, '')
  console.log(result) // abcd
  
  const result = array.find((element) => {
      return element === 'b'
  })
  console.log(result) // b
  
  const numbers = [1,3,5]
  
  const hasEvenNumber = numbers.some((num) => {
      return num%2 === 0
  })
  console.log(hasEvenNumber) // false
  
  const hasOddNumber = numbers.some((num) => {
      return num%2
  })
  console.log(hasOddNumber) // true
  
  const isEveryNumberEven = numbers.every((num) => {
      return num%2 === 0
  })
  console.log(isEveryNumberEven) // false
  
  const isEveryNumberOdd = numbers.every((num) => {
      return num%2
  })
  console.log(isEveryNumberOdd) // true
  ```

<br>



## 객체 (Objects)

### 객체의 정의와 특징

- 객체는 속성(property)의 집합이며, 중괄호 내부에 key와 value의 쌍으로 표현

  ```javascript
  const me = {
      name: 'harvey',
      age: 25,
      'apple products' : {
          phone: 'iphone cs',
          laptop: 'macbook'
      }
  }
  ```

  - key는 문자열 타입만 가능
    - key 이름에 띄어쓰기 등의 구분자가 있으면, 따옴표로 묶어서 푷션
  - value는 모든 타입 가능
  - 객체 요소 접근은 점 또는 대괄호로 가능
    - key 이름에 띄어쓰기 등의 구분자가 있으면, 대괄호 접근만 가능

### 객체와 메서드

- 메서드는 어떤 객체의 속성을 참조하는 함수

- 객체.메서드명()으로 호출

- 메서드 내부에서는 `this` 키워드가 객체를 의미함

  ```javascript
  const me = {
      firstName: 'harvey',
      lastName: 'kim',
      fullName: this.firstName + this.lastName, // NaN
      
      getFullName: function () {
          return this.firstName + this.lastName
      }
  }
  ```



### 객체 관련 ES6 문법

- 속성명 축약

  - 객체를 정의할 때 key와 할당하는 변수의 이름이 같으면 예시와 같이 축약 가능

    ```javascript
    const marvleHeros = ['ironman', 'spiderman']
    const dcHeros = ['batman']
    
    const heroMovie = {
        marvelHeros,
        dcHeros,
    }
    ```

- 메서드명 축약

  - 메서드 선언 시 `function` 키워드 생략 가능

    ```javascript
    const obj = {
        greeting() {
            console.log('hi')
        }
    }
    ```

- 계산된 속성명 사용하기

  - 객체를 정의할 때 key의 이름을 표현식을 이용하여 동적으로 생성 가능

    ```javascript
    const key = 'fruits'
    const value = ['banana', 'apple', 'melon']
    
    const food = {
        [key]: value,
    }
    
    console.log(food) // {'fruits': Array(3)}
    console.log(food.fruits) // ['banana', 'apple', 'melon']
    ```

- 구조 분해 할당

  - 배열 또는 객체를 분해하여 속성을 변수에 쉽게 할당

    ```javascript
    const userInfo = {
        name: 'kim',
        userId: 'harveydev24',
        email: 'harveydev24@gmail.com'
    }
    
    const name = userInfo.name
    const { name } = userInfo
    const { name, userId } = userInfo
    ```

- 객체 전개 구문 (Spread Operator)

  - `...`을 이용하여 객체 내부에서 객체 전개 가능

    ```javascript
    const obj = {b:2, c:3}
    const newOjb = {a:1, ...obj, d:4}
    console.log(newOjb) // {a:1, b:2, c:3, d:4}
    ```



### JSON (JavaScript Object Notation)

- key-value 쌍의 형태로 데이터를 표기하는 언어 독립적 표준 포맷

- JS의 객체와 유사하게 생겼으나 실제로는 문자열 타입

  - 따라서 JS의 객체로써 조작하기 위해서는 parsing이 필수

  - JS에서는 JSON을 조작하기 위한 두 가지 내장 메서드를 제공

    ```javascript
    // Object => JSON
    const jsonData = JSON.stringify({
        coffee: 'Americano',
        iceCream: 'Cookie and cream'
    })
    console.log(typeof jsonData) // string
    
    // JSON => Object
    const parsedData = JSON.parse(jsonData)
    console.log(typeof parsedData) // object
    ```



<br>

## this

- JS의 `this`는 실행 문맥에 따라 다른 대상을 가리킴

  ```javascript
  function getFullName() {
      return this.firstName + this.lastName
  }
  
  const me = {
      firstName: 'Harvey',
      lastName: 'Kim',
      getFullName: getFullName,
  }
  
  const you = {
      firstName: 'Jack',
      lastName: 'Lee',
      getFullName: getFullName,
  }
  
  me.getFullName() // HarveyKim (this === me)
  you.getFullName() // JackLee (this === you)
  getFullName() // NaN (this === window)
  ```

  - `class` 내부의 생성자 (`constructor`) 함수
    - `this`는 생성되는 객체를 가리킴
  - 메서드(객체,메서드명()으로 호출 가능한 함수)
    - `this`는 해당 메서드가 소속된 객체를 가리킴
  - 위의 두 가지 경우를 제외하면 모두 최상위 객체인 `window`를 가리킴

### function 키워드와 화살표 함수 차이

```javascript
const obj = {
    PI = 3.14,
    radiuses: [1,2,3,4,5],
    printArea: function () {
        this.radiuses.forEach(function (r) {
            console.log(this.PI * r * r)
        }.bind(this))
    },
}
```

- `this.radiuses`는 메서드 소속이기 때문에 정상적으로 접근 가능

- `forEach`의 콜백함수의 경우 메서드가 아님

  - 때문에 콜백함수 내부의 `this`는 `window`가 되어 `this.PI`에 접근 불가능

  - 이 콜백함수 내부에서 `this.PI`에 접근하기 위해서 `.bind(this)` 메서드 사용

  - 화살표 함수를 이용하여 위의 번거로운 과정 생략 가능

    ```javascript
    const obj = {
        PI = 3.14,
        radiuses: [1,2,3,4,5],
        printArea: function() {
            this.radiuses.forEach((r) => {
                console.log(this.PI * r * r)
            })
        }
    }
    ```

    

<br>

## lodash

- 모듈성, 성능 및 추가 기능을 제공하는 JS 유틸리티 라이브러리
- `array, object` 등 자료구조를 다룰 때 사용하는 유용하고 간편한 유틸리티 함수들을 제공









