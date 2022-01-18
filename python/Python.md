# Python

*Life Is Short. You Need Python.*

---

## 특징

- 인터프리터 언어
  * 소스코드를 기계어로 변환하는 컴파일 과정 없이 바로 실행 가능
  * 코드를 대화하듯 한 줄 입력하고 실행 후, 바로 확인 가능

- 객체 지향 프로그래밍(OOP)

  * 모든 것이 **객체**로 구현되어 있음
  * **객체**란 숫자, 문자, 클래스 등 값을 가지고 있는 모든 것
  * **객체**를 이용하면 코드의 재사용성 증가
  * 그러나 설계가 힘듦
  * 객체 지향 외에는 절차 지향, 함수형이 있음

- Easy to learn

  - 다른 언어보다 문법이 간결
    - 예시: 변수에 별도의 타입 지정 필요 없음
    - 예시: 문장을 구분할 때, 들여쓰기 사용

- 크로스 플랫폼 언어

  - 윈도우, macOS, 리눅스, 유닉스 등 다양한 운영체제에서 실행가능

    

## 개발환경의 종류

- 대화형 환경
  - 파이썬 기본 Interpreter
    - IDLE
    - 디버깅이 매우 불편
  - Jupyter Notebook
    - 웹 브라우저 환경에서 코드를 작성할 수 잇는 오픈소스
    - 브라우저에서 셀 단위로 코드를 실행하고 바로 확인 가능
    - 마크다운 지원

- 스크립트 실행

  - Pycharm, VsCode 등의 IDE

  - .py 작성 후 `python ~.py` 로 실행

    

## 코드 스타일 가이드

- 파이썬에서 제안하는 스타일 가이드
  - PEP8

- 기업, 오픈소스 등에서 사용되는 스타일 가이드
  - Google Style guide

---

# 기초 문법



## 변수(Variable)

- 변수란 컴퓨터 메모리 어딘가에 저장되어 있는 객체를 참조하기 위해 사용되는 이름
- 동일 변수에 다른 객체를 언제든 할당할 수 있다. 즉, 참조하는 객체가 바뀔 수 있다.
- 할당 연산자 `=`를 통해 값을 할당(assignment)
- `type() #변수에 할당된 값의 타입` 
- `id() #객체의 고유값(레퍼런스, 메모리 주소) 반환` 

- 변수 할당

  ```python
  x = 1
  print(x)
  # 1
  
  x = y = 1
  print(x, y)
  # 1, 1
  
  x, y = 1, 2
  print(x, y)
  # 1, 2
  ```

- 변수 연산

  ```python
  x, y = 1, 2
  x + y
  # 3
  
  s = 'Python'
  s + ' is fun'
  # 'Python is fun'
  ```

  

## 식별자(Identifiers)

- 객체(변수, 함수, 모듈, 클래스 등)를 식별하는데 사용하는 이름

- 규칙

  - 식별자의 이름은 영문 알파벳, 언더스코어(_), 숫자로 구성

  - 첫 글자에 숫자가 올 수 ㅇ벗음

  - 길이 제한이 없고, 대소문자 구분

  - 다음의 키워드(keywords)는 예약어(reserved words)이므로 사용할 수 없음

    ```python
    False, None, True, and, as, assert, async, await, break, class, continue, def, del, elif, else, except, finally, for, from, global, if, import, in, is, lambda, nonlocal, not, or, pass, raise, return, try, while, with, yield
    ```

  - 내장함수나 모듈 등의 이름도 사용 불가

    ```python
    print = 'hi'
    # TypeError
    ```



## 사용자 입력

- `input([prompt])` 

  - 사용자로부터 값을 입력 받는 내장함수

  - 반환값은 항상 문자열

    ```python
    name = input('name: ')
    print(name)
    # name: harvey
    # harvey
    
    type(name)
    # str
    ```

    

## 주석

- 한 줄 주석 `#`

  ```python
  # print name
  print('harvey')
  ```

- 여러줄 주석 `'''` 또는 `"""` 

  ```python
  '''
  This is a comment
  '''
  ```



## 자료형

- 불린(Boolean Type)

  - `True / False` 값을 가진 타입은 `bool` 

  - 비교/논리 연산을 수행

  - 다음은 모두 False

    ```python
    0, 0.0, (), [], {}, '', None
    ```

  - bool() 함수

    ```python
    bool(0)
    # False
    
    bool(-1)
    # True
    ```

    

- 수치형(Numeric Type)

  - 정수(Int)

    - 모든 정수는 `int`

      ```python
      print(type(1))
      # <class 'int'>
      ```

    - 파이썬에서는 임의 정밀도 산술(Arbitrary precision arithmetic)을 이용하여 고정된 형태의 메모리가 아닌 가용 메모리들을 활용하여 수 표현을 하므로 매우 큰 수를 나타낼 때 오버플로우가 발생하지 않음

      ```python
      import sys
      sys.maxsize
      # 9223372036854775807
      
      2 ** 63 - 1
      # # 9223372036854775807
      ```

      - 진수 표현

        ```python
        # 2진수
        0b10
        # 2
        
        # 8진수
        0o30
        # 24
        
        # 16진수
        0x10
        # 16
        ```

  - 실수(Float)

    - 정수가 아닌 모든 실수는 `float` 타입

      ```python
      print(type(1.1))
      # <class 'float'>
      ```

    - 지수 표기법 사용

      ```python
      1/-10**100
      #-1e-100
      ```

    - 부동소수점

      - 컴퓨터가 실수를 표현하는 방법

      - 2진수(비트)로 숫자를 표현

      - 이 과정에서 floating point rounding error가 발생함

        ```python
        0.1 * 3 == 0.3
        # False
        ```

      - 이를 해결하기 위한 방법

        ```python
        a, b = 0.1 * 3, 0.3
        
        # 1. 임의의 작은 수
        abs(a - b) <= 1e-10
        # True
        
        # 2. system상의 machine epsilon
        import sys
        print(abs(a - b) <= sys.float_info.epsilon)
        # True
        
        # 3. Python 3.5 이상
        import math
        math.isclose(a, b)
        # True
        ```

- 문자열(String Type)

  - 모든 문자는 `str` 타입

    ```python
    print(type('hello'))
    # <class 'str'>
    ```

  - `'` 또는 `"` 를 이용하여 표기

  - Immutable

    ```python
    a = 'string'
    a[-1] = 'z'
    # TypeError
    ```

  - Iterable

    ```python
    a = '123'
    for char in a:
        print(char)
    '''
    1
    2
    3
    '''
    ```

  - 중첩따옴표

    ```python
    print('문자열 안에 "큰 따옴표" 사용')
    # 문자열 안에 "큰 따옴표" 사용
    
    print("문자열 안에 '작은 따옴표' 사용")
    # 문자열 안에 '작은 따옴표' 사용
    ```

  - 삼중따옴표

    ```python
    print('''문자열 안에 '작은 따옴표'나 "큰 따옴표" 사용''')
    # 문자열 안에 '작은 따옴표'나 "큰 따옴표" 사용
    ```

  - Escape sequence

    - 문자열 내에서 특정 문자나 조작을 위해서 역슬래쉬 `\` 를 이용

      | 예약 문자 | 내용(의미) |
      | --------- | ---------- |
      | \n        | 줄 바꿈    |
      | \t        | 탭         |
      | \r        | 캐리지리턴 |
      | \0        | 널(Null)   |
      | \\        | \          |
      | \\'       | '          |
      | \\"       | "          |

      ```python
      print('철수 \'안녕\'')
      # 철수 '안녕'
      ```

  - String Interpolation

    - 문자열을 변수를 활용하여 만드는 법

      ```python
      # 1. % formatting
      name = 'Kim'
      print('Hi, %s' % name)
      # Hi, Kim
      
      # 2. str.formt()
      print('Hi, {}'.format(name))
      # Hi, Kim
      
      # 3. f-string (Python 3.6+)
      print(f'Hi, {name}')
      # Hi, Kim
      pi = 3.141592
      print(f'원주율은 {pi:.3}, 반지름이 2일 때 원의 넓이는 {pi*2*2}')
      # 원주율은 3.14, 반지름이 2일 때 원의 넓이는 12.566368
      ```

- None

  - 값이 없음을 표현하기 위한 타입

    ```python
    print(type(None))
    # <class 'NoneType'>
    ```





