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
    False, None, True, and, as, assert, async, await, break, 
    class, continue, def, del, elif, else, except, finally, 
    for, from, global, if, import, in, is, lambda, nonlocal, 
    not, or, pass, raise, return, try, while, with, yield
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



## 컨테이너(Container)

- 여러개의 값을 담을 수 있는 객체

- 서로 다른 자료형을 저장할 수 있음

- 시퀀스형

  1. 리스트

     - 순서를 가지는 0개 이상의 객체를 참조하는 자료형

       ```python
       myList = []
       print(type(myList))
       # <class 'list'>
       ```

     - Mutable

       ```python
       myList = [1, 2]
       myList[0] = 0
       print(myList)
       # [0, 2]
       ```

     - 항상 대괄호 형태로 출력

     - `[]` 또는 `list()` 를 통해 생성

     - 인덱스로 접근

  2. 튜플

     - 순서를 가지는 0개 이상의 객체를 참조하는 자료형

       ```python
       myTuple = (1,2)
       print(type(myTuple))
       # <class 'tuple'>
       ```

     - Immutable

       ```python
       myTuple = (1,2)
       myTuple[0] = 0
       # TypeError
       ```

     - 항상 소괄호 형태로 출력

     - `()` 또는 `tuple()` 을 통해 생성

     - 인덱스로 접근

     - 튜플 생성시 주의사항

       ```python
       # 단일 항목의 경우 쉼표 붙여야함
       a = 1,
       print(a)
       # (1, )
       ```

  3. 레인지

     - 숫자의 시퀀스를 나타내기 위해 사용하는 자료형

       ```python
       print(type(range(4)))
       # <class 'range'>
       
       # 기본형
       for i in range(4):
           print(i)
       '''
       0
       1
       2
       3
       '''
       
       # 범위 지정
       for i in range(1, 4):
           print(i)
       '''
       1
       2
       3
       '''
       
       # 범위 및 스텝 지정
       for i in range(1, 4, 2):
           print(i)
       '''
       1
       3
       '''
       ```

  - 패킹/언패킹 연산자

    - 모든 시퀀스형은 패킹/언패킹 연산자 *를 사용하여 객체의 패킹 또는 언패킹이 가능

    - 패킹

      - 대입문의 좌변에 위치

      - 우변의 객체 수가 좌변의 변수 수보다 많을 경우 객체를 순서대로 대입

      - 나머지 항목들은 모두 별 기호로 표시된 변수에 리스트로 대입

        ```python
        x, *y = 1, 2, 3, 4
        print(x)
        # 1
        print(y)
        # [2, 3, 4]
        ```

    - 언패킹

      - argument 이름이 *로 시작하는 경우, argument unpacking이라 함

      - \* 패킹의 경우, 리스트로 대입

      - \* 언패킹의 경우 튜플 형태로 대입

        ```python
        def multiply(x, y, z):
            return x * y * z
        
        numbers = [1, 2, 3]
        multiply(*numbers)
        # 6
        ```

        

- 비시퀀스형

  1. 세트

     - 중복과 순서 없이 0개 이상의 해시 가능한 객체를 참조하는 자료형

       ```python
       print(type(set([])))
       # <class 'set'>
       
       myList = [1, 1, 2]
       mySet = set(myList)
       print(mySet)
       # {1, 2}
       ```

     - 해시 가능한 객체(immutable)만 담을 수 있음

     - Mutable

     - `set()` 으로 생성

  2. 딕셔너리

     - 순서 없이 키-값(key-value) 쌍으로 이루어진 객체를 참조하는 자료형

       ```python
       myDict = dict()
       print(type(myDict))
       # <class 'dict'>
       ```

     - 키는 해시 가능한 불변 자료형만 가능

       - string, integer, float, boolean, tuple, range

     - 값은 어떠한 형태든 상관 없음

     - `{}` 또는 `dict()` 를 통해 생성

     - 키를 통해 값에 접근

       ```python
       myDict = {'a': 'apple', 'b': 'banana'}
       print(myDict['a'])
       # apple
       ```



## 형 변환(Typecasting)

- 파이썬의 데이터 형태는 서로 변환할 수 있음

  - 암시적 형 변환(Implicit)

    - 사용자가 의도하지 않고, 파이썬 내부적으로 자료형을 변환

      ```python
      # bool
      True + 3
      # 4
      
      # Numeric Type(int, float, complex)
      3 + 5.0
      # 8.0
      
      3 + 4j + 5
      # (8 + 4j)
      ```

  - 명시적 형 변환(Explicit)

    - 사용자가 특정 함수를 활용하여 의도적으로 자료형을 변환 하는 경우

      ```python
      # str, float -> int
      int('3') + 1
      # 4
      
      int('3.3') + 1
      # ValueError
      
      int(3.9) + 1
      # 4
      
      # str, int -> float
      float(3) + 1
      # 4.0
      
      float('3.0') + 1
      # 4.0
      
      float('3/4')
      # ValueError
      ```

      

## 연산자(Operator)

- 기본 사칙연산 및 수식 계산

  | 연산자 | 내용     |
  | ------ | -------- |
  | +      | 덧셈     |
  | -      | 뺄셈     |
  | *      | 곱셈     |
  | /      | 나눗셈   |
  | //     | 몫       |
  | **     | 거듭제곱 |

- 비교 연산자

  - 값을 비교하여 `True / False` 값을 리턴함

  | 연산자 | 내용                        |
  | ------ | --------------------------- |
  | <      | 미만                        |
  | <=     | 이하                        |
  | >      | 초과                        |
  | >=     | 이상                        |
  | ==     | 같음                        |
  | !=     | 같지않음                    |
  | is     | 객체 아이덴티티(OOP)        |
  | is not | 객체 아이덴티티가 아닌 경우 |

- 논리 연산자

  - 일반적으로 비교연산자와 함께 사용됨

  | 연산자  | 내용                                |
  | ------- | ----------------------------------- |
  | A and B | A와 B 모두 True이면 True 리턴       |
  | A or B  | A와 B 모두 False이면 False 리턴     |
  | Not     | True를 False로, False를 True로 바꿈 |

    - 결과가 확실한 경우 두 번째 값은 확인하지 않음

      - and 연산에서 첫번째 값이 `False` 인 경우 무조건 `False` -> 첫번째 값 반환
      - or 연산에서 첫번째 값이 `True` 인 경우 무조건 `True` -> 첫번째 값 반환

      ```python
      a = 5 and 4
      print(a)
      # 4
      
      b = 5 or 3
      print(b)
      # 5
      
      c = 0 and 5
      print(c)
      # 0
      
      d = 5 or 0
      print(b)
      # 5
      ```

- 복합 연산자

  - 연산과 대입이 함께 이루어짐

    ```python
    cnt = 0
    cnt += 1
    print(cnt)
    # 1
    ```

- 식별 연산자

  - `is` 연산자를 통해 동일한 객체인지 확인 가능함

    ````python
    a = 3
    b = 3
    print(a is b)
    # True
    ````

- 멤버십 연산자

  - 시퀀스 포함 여부 확인

    ```python
    # in
    1 in [2, 3]
    # False
    
    4 in (1, 2, 'hi')
    # False
    
    -3 in range(3)
    # False
    
    'a' in 'apple'
    # True
    
    # not in
    'b' not in 'apple'
    # True
    ```

- 시퀀스형 연산자

  - 시퀀스 간의 concatenation

    ```python
    # 산술연산자 +
    [1, 2] + ['a']
    # [1, 2, 'a']
    
    (1, 2) + ('a', )
    # (1, 2, 'a')
    
    range(2) + range(2, 5)
    # TypeError
    
    '12' + 'b'
    # '12b'
    
    # 반복연산자 *
    [0] * 3
    # [0, 0, 0]
    
    (1, 2) * 2
    # (1, 2, 1, 2)
    
    range(1) * 3
    # TypeError
    
    'hi' * 2
    # 'hihi'
    ```

- 기타

  - 인덱싱

    - 시퀀스의 특정 인덱스 값에 접근

    - 해당 인덱스가 없는 경우 *IndexError*

      ```python
      [1, 2, 3][0]
      # 1
      
      (1, 2, 3)[0]
      # 1
      
      range(3)[2]
      # 2
      
      'abc'[0]
      # 'a'
      
      [1, 2, 3][4]
      # IndexError
      ```

  - 슬라이싱

    - 시퀀스를 특정 단위로 슬라이싱

      ```python
      [1, 2, 3][0:2]
      # [1, 2]
      
      (1, 2, 3)[0:2]
      # (1, 2)
      
      range(3)[0:2]
      # range(0, 2)
      
      'abc'[0:2]
      # 'ab'
      
      [1, 2, 3, 5][0:4:2]
      # [1, 3]
      
      s = 'abc'
      s[::-1]
      # 'cba'
      ```

  - set 연산자

    ```python
    A = {1, 2, 3}
    B = {2, 3, 4}
    
    A | B
    # {1, 2, 3, 4}
    
    A & B
    # {2, 3}
    
    A - B
    # {1}
    
    A ^ B
    # {1, 4}
    ```

- 연산자 우선 순위
  1. `()`
  2. 슬라이싱
  3. 인덱싱
  4. `**`
  5. `+, - # 단항연산자`
  6.  `*, /, %`
  7.  `+, - # 산술연산자`
  8. `in, is`
  9. not
  10. and
  11. or



## 파이썬 프로그램 구성 단위

- 식별자(Identifier)

  - 변수, 함수, 클래스 등 프로그램이 실행되는 동안 다양한 값을 가질 수 있는 이름
  - 예약어
    - 파이썬 키워드 (명령어)

  - 리터럴(Literal)

    - 읽혀지는 대로 쓰여 있는 값 그 자체

      ```python
      #name은 식별자, 'harvey'는 리터럴
      name = 'harvey'
      ```

- 표현식(Expression)
  - 새로운 데이터 값을 생성하거나 계산하는 코드 조각

- 문장(Statement)
  - 특정한 작업을 수행하는 코드 전체
  - 파이썬이 실행 가능한 최소한의 코드 단위
  - 표현식은 값을 생성하는 일부분이고, 문장은 특정작업을 수행하는 코드 전체
    - 모든 표현식은 문장이다.

- 함수(Function)

  - 특정 명령을 수행하는 함수 묶음

    ```python
    def multiply(x, y):
        return x * y
    ```

- 모듈(Module)
  - 함수/클래스의 모음 또는 하나의 프로그램을 구성하는 단위

- 패키지(Package)
  - 프로그램과 모듈 묶음
    - 프로그램은 실행하기 위한 것
    - 모듈은 다른 프로그램에서 불러와 사용하기 위한 것

- 라이브러리
  - 패키지 모음







