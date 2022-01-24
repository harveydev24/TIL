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



## 조건문

- `True / False` 를 판단할 수 있는 조건식과 함께 사용

- expression에는 `True / False` 에 대한 조건식

  - 조건이 `True` 인 경우 이후 들여쓰기 되어 있는 코드 블럭 실행

  - 조건이 여러개인 경우 `elif` 사용

  - 이외의 경우 `else` 이후 들여쓰기 되어 있는 코드 블럭을 실행

    ```python
    if <expression>:
        # Code block
    elif <expression>:
        # Code block
    else:
        # Code block
    ```

- 조건문은 중첩 가능

  ```python
  if <expression>:
      # Code block
      if <expression>:
          # Code block
      else:
          # Code block
  ```

- 조건 표현식

  - 조건 표현식을 일반적으로 조건에 따라 값을 정할 때 활용

  - 삼항 연산자로 부르기도 함

    ```python
    <True인 경우 값> if <expression> else <False인 경우 값>
    
    # 다음의 코드를
    num = 2
    if num % 2:
        result = '홀수'
    else:
        result = '짝수'
    print(result)
    
    # 다음과 같이 간단하게 바꿀 수 있다.
    result = '홀수' if num % 2 else '짝수'
    print(result)
    ```



## 반복문

- 특정 조건을 도달할 때 까지, 계속 반복되는 일련의 문장

- `while` 문

  - 조건이 참인 경우 들여쓰기 되어 있는 코드 블록 실행

  - 이후 다시 조건식을 검사하며 반복적으로 실행

  - 무한 루프를 방지하기 위해 종료 조건 반드시 필요

    ```python
    while <expression>:
        # Code block
    ```

- `for` 문

  - 시퀀스를 포함한 순회 가능한 객체 요소를 모두 순회함

    - `string, list, tuple, dict, range, enumerate`

  - 처음부터 끝까지 모두 순회하므로 별도의 종료 조건 필요 없음

    ```python
    for <변수명> in <iterable>:
        # Code block
    else: # else는 선택사항
        # Code block
    ```

    - 딕셔너리는 기본적으로 key를 순회함

      ```python
      grades = {'john': 80, 'eric': 90}
      for student in grades:
          print(student)
      '''
      john
      eric
      '''
      
      print(grades.keys())
      # dict_keys(['john', 'eric'])
      
      print(greades.values())
      # dict_keys([80, 90])
      
      print(grades.items())
      # dict_items([('john', 80), ('eric', 90)])
      ```

  - `enumerate` 순회

    - 인덱스와 객체를 쌍으로 담은, (index, value) 형태의 tuple로 구성된 객체 열거형(enumerate) 객체 반환

    ```python
    members = ['민수', '영희', '철수']
    for idx, member in enumerate(members):
        print(idx, member)
    '''
    0 민수
    1 영희
    2 철수
    '''
    
    # 시작값 지정 가능
    for idx, member in enumerate(members, start = 1):
        print(idx, member)
    '''
    1 민수
    2 영희
    3 철수
    '''
    ```

    

  - List Comprehension

    - 표현식과 제어문을 통해 특정한 값을 가진 리스트를 간결하게 생성

      ```python
      [<expression> for <변수> in <iterable>]
      [<expression> for <변수> in <iterable> if <조건식>]
      
      # 1~3의 세제곱 리스트
      cubic_list = []
      for number in range(1, 4):
          cubic_list.append(number ** 3)
      cubic_list
      # [1, 8, 27]
      
      [number ** 3 for number in range(1, 4)]
      # [1, 8, 27]
      ```

  - Dictionary Comprehension

    - 표현식과 제어문을 통해 특정한 값을 가진 딕셔너리를 간결하게 생성

      ```python
      {key: value for <변수> in <iterable>}
      {key: value for <변수> in <iterable> if <조건식>}
      
      # 1~3의 세제곱 딕셔너리
      cubic_dict = {}
      for number in range(1, 4):
          cubic_dict[number] = number ** 3
      cubic_dict
      # {1: 1, 2: 8, 3: 27}
      
      cubic_dict = {key: number ** 3 for number in range(1, 4)}
      ```

 - 반복문 제어

   - `break`

     - 반복문을 종료

       ```python
       n = 0
       while True:
           if n == 3:
               break
           print(n)
           n += 1
       '''
       0
       1
       2
       '''
       ```

   - `continue`

     - 이후의 코드 블록은 실행하지 않고, 다음 반복 수행

       ```python
       for i in range(6):
           if i % 2 == 0:
               continue
           print(i)
       '''
       1
       3
       5
       '''
       ```

   - `pass`

     - 아무것도 하지 않음

     - 특별히 할 일 없을 때 자리를 채우는 용도

     - 반복문 아니여도 사용 가능

       ```python
       for i in range(5):
           if i == 3:
               pass
           print(i)
       ```

   - `else`

     - 끝까지 반복문을 실행한 이후에 `else`문 실행

       ```python
       for char in 'apple':
           if char == 'b':
               print('b')
               break
       else:
           print('b가 없습니다.')
       # b가 없습니다.
       ```

       


## 함수(Function)

### 함수의 정의

- 특정한 기능을 하는 코드의 조각(묶음)

- 특정 명령을 수행하는 코드를 매번 다시 작성하지 않고, 필요 시에만 호출하여 간편하게 사용

- **재사용성, 가독성,** 그리고 **생산성**

- 파이썬에는 기본적으로 내장 함수가 존재

  ```python
  print(), sum(), max(), min(), len(), ...
  ```

- 구현되어 있는 함수가 없는 경우, 직접 함수 작성

  ```python
  def function_name(parameter):
      # Code block
      return returning_value
  ```



### 선언과 호출

- 함수의 선언은 `def` 키워드 이용

- 들여쓰기를 통해 Function body(Code block) 작성

- 함수는 parameter를 넘겨줄 수 있음

- 동작 후에 `return` 을 통해 결과를 전달

- 함수는 함수명()으로 호출

  - parameter가 있는 경우, 함수명(값1, 값2, ...)로 호출

    ```python
    # foo()로 호출
    def foo():
        return True
    
    # add(x, y)로 호출
    def add(x, y):
        return x, y
    ```



### 함수의 결과값(Output)

- 결과값에 따른 함수의 종류

  - Void function

    - 명시적인 `return` 값이 없는 경우, `None` 을 반환하고 종료

      ```python
      print('hello')
      # hello
      ```

  - Value returning function

    - 함수 실행 후, `return` 문을 통해 값 반환

    - `return` 을 통해 값 반환 후 함수가 바로 종료됨

      ```python
      float('3.14')
      ```

- 결과값을 여러개 반환하고 싶을 경우, 튜플을 사용

  ```python
  def minus_and_product(x, y):
      return x - y, x * y
  
  result = minus_and_product(4, 5)
  result
  # (-1, 20)
  ```



### 함수의 입력(Input)

- Parameter

  - 함수를 실행할 때, 함수 내부에서 사용되는 식별자

    ```python
    def function_name(parameter):
        return parameter
    ```

    

- Argument

  - 함수를 호출 할 때, 함수의 parameter를 통해 전달되는 값

    ```python
    function_name('argument')
    ```

  - 필수 Argument

    - 반드시 전달되어야 하는 argument

  - 선택 Argument

    - 값을 전달하지 않아도 되는 경우 기본 값이 전달

  - Positional Argument

    - 기본적으로 함수 호출 시, argument는 위치에 따라 함수 내에 전달됨

      ```python
      def add(x, y):
          return x + y
      add(2, 3)
      '''
      def add(x, y):
      	x, y = 2, 3
      	return x + y
      '''
      ```

  - Keyword Arguments

    - 변수의 이름으로 특정 argument를 전달할 수 있음

    - Keyword argument 다음에 positional argument를 활용할 수 없음

      ```python
      def add(x, y):
          return x + y
      
      add(x=2, y=5)
      # 7
      
      add(2, y=5)
      # 7
      
      add(y=5, 2)
      # SyntaxError
      ```

  - Default Arguments Values

    - 기본값을 지정하여 함수 호출 시 argument 값을 설정하지 않도록 함

      - 정의된 것 보다 더 적은 개수의 argument들로 호출 될 수 있음

        ```python
        def add(x, y=0):
        	return x + y
        
        add(2)
        '''
        def add(x, y=0):
        	x, y = 2, 0
        	return x + y
        '''
        ```

      - 다음과 같이 함수를 정의할 수 없음

        ```python
        def add(x=0, y):
            return x + y
        ```

  - Positional Arguments Packing/Unpacking

    - 연산자 `*`

      - 여러 개의 positional argument를 하나의 필수 parameter로 받아서 사용

      - 몇 개의 positional argument를 받을지 모르는 함수를 정의할 때 유용

        ```python
        def add(*args):
            sum = 0
            for arg in args:
                sum += arg
            print(sum)
        
        add(2)
        # 2
        
        add(2, 3, 4, 5)
        # 14
        ```

   - Keyword Arguments Packing/Unpacking

     - 연산자 `**`

       - 여러개의 keyword argument를 하나의 필수 parameter로 받아서 사용

       - Argument들은 딕셔너리로 묶여 처리됨

         ```python
         def family(**kwargs):
             for key, value in kwargs.items():
                 print(key, ":", value)
         
         family(father='John', mother='Jane', me='John Jr.')
         ```



### 함수의 범위(Scope)

- 함수는 코드 내부에 local scope를 생성하며, 그 외 공간인 global scope로 구분

- scope

  - built-in scope
    - 정의된 variable이 파이썬이 실행된 이후부터 영원히 유지
  - global scope
    - 코드 어디에서든 참조할 수 있는 공간
    - global variable 정의
      - 모듈이 호출된 시점 이후 혹은 인터프리터가 끝날 때까지 유지

  - local scope

    - 함수가 만든 scope이며 함수 내부에서만 참조 가능

    - local variable 정의

      - 함수가 호출될 때 생성되고, 함수가 종료될 때까지 유지

        ```python
        def func():
            a = 20
            print(a)
            
        func()
        print(a)
        # NameError
        ```

- 이름 검색 규칙(Name Resolution)

  - 파이썬에서 사용되는 이름(식별자)들은 이름공간(namespace)에 저장되어 있음

  - 다음의 순서로 이름을 찾아 나감(LEGB Rule)

    1. Local scope

       - 함수

    2. Enclosed scope

       - 특정 함수의 상위 함수

    3. Global scope

       - 함수 밖의 변수, Import 모듈

    4. Built-in scope

       - 파이썬 안에 내장되어 있는 함수 또는 속성

         ```python
         a = 0
         b = 1
         
         def enclosed():
             a = 10
             c = 3
             def local(c):
                 print(a, b, c)
             local(300)
             print(a, b, c)
         enclosed()
         print(a, b)
         
         '''
         10 1 300
         10 1 3
         0 1
         '''
         
         print(sum)
         print(sum(range(2)))
         sum = 5
         print(sum)
         print(sum(range(2)))
         
         '''
         <built-in function sum>
         1
         5
         TypeError
         global scope의 sum 변수에 5가 할당되었고, 이것이 built-in scope의 내장 함수 sum 보다 먼저 탐색됨
         '''
         ```

  - 함수 내에서는 바깥 scope의 변수에 접근은 가능하나, 기본적으로 수정은 불가
    - 값을 할당하면 해당 scope의 namespace에 변수가 새롭게 생성되기 때문
    - 수정을 위해서는 `global`, `nonlocal` 이용
      - 코드가 복잡해지면 변수의 변경을 추적하기 어렵고 오류 발생하기 쉬움
      - 가급적 사용하지 않는 것이 좋으며, 함수로 값을 바꾸고자 한다면 argument로 넘기고 리턴 값을 사용

  

- `global` 문

  - 현재 코드 블록 전체에 적용되며, 나열된 식별자(이름)이 global variable임을 나타냄

    ```python
    a = 0
    
    def func()
    	global a
        a = 3
    
    func()
    print(a)
    # 3
    ```

  - `global` 에 나열된 이름은 같은 코드 블록에서 `global` 앞에 등장할 수 없음

    ```python
    a = 10
    
    def func():
        print(a)
        global a
        a = 3
        
    print(a)
    func()
    print(a)
    # SyntaxError
    ```

  - `global` 에 나열된 이름은 parameter, `for` 루프 대상, 클래스, 함수 등으로 정의되지 않아야 함

    ```python
    a = 10
    
    def func(a):
        global a
        a = 3
    
    print(a)
    func()
    print(a)
    # SyntaxError
    ```

- `nonlocal` 문

  - `global` 을 제외하고 가장 가까운(둘러 싸고 있는) scope의 변수를 연결

  - `nonlocal` 에 나열된 이름은 같은 코드 블록에서 `nonlocal` 앞에 등장할 수 없음

  - `nonlocal` 에 나열된 이름은 parameter, `for` 루프 대상, 클래스, 함수 등으로 정의되지 않아야 함

  - `global` 과 달리 이미 존재하는 이름과의 연결만 가능

    ```python
    def func():
        global out
        out = 3
        
    func()
    print(out)
    # 3
    
    def func():
        def func2():
            nonlocal y
            y = 2
        func2()
        print(y)
    
    func()
    # SyntaxError
    ```

- 범위 확인하기
  - `globals()`
    - global, local, built-in 정보 모두 dict 형태로 리턴
  - `locals()`
    - 실행되어지는 함수 내의 local namespace를 dict 형태로 리턴



### 함수의 문서화(Doc-String)

- 함수나 클래스의 설명

  ```python
  def foo():
      """
      이 함수는 foo입니다.
      """
  ```


- `help(function_name)` 으로 함수의 설명을 출력할 수 있음

- Naming Convention

  - 좋은 함수와 parameter 이름을 짓는 방법

    - 상수 이름은 영문 전체를 대문자
    - 클래스 및 예외의 이름은 각 단어의 첫 글자만 영문 대문자
    - 이 외 나머지는 소문자 또는 밑줄로 구분한 소문자 사용
    - 스스로를 설명
    
      - 함수 이름만으로 역할을 파악 가능
    
      - 어떤 기능을 수행하는 지, 결과 값으로 무엇을 반환 하는 지
    - 약어 사용 지양



### 함수 응용

- 내장 함수(Built-in Functions)

  - 파이썬에는 항상 사용할 수 있는 많은 함수와 형(type)이 내장되어 있음

  - `map(function, iterable)`

    - 순회 가능한 데이터의 모든 요소에 함수를 적용하고 그 결과를 map object로 반환

      ```python
      numbers = [1, 2, 3]
      result = map(str, nubmers)
      print(result, type(result))
      # <map object at 0x~~~> <class 'map'>
      
      list(result)
      # ['1', '2', '3']
      ```

  - `filter(function, iterable)`

    - 순회 가능한 데이터의 모든 요소에 함수를 적용하고 그 결과가 `True`인 것들을 filter object로 반환

      ```python
      def odd(n):
          return n % 2
      
      numbers = [1, 2, 3]
      result = filter(odd, numbers)
      print(result, type(result))
      # <filter object at 0x~~~> <class 'filter'>
      
      list(result)
      # [1, 3]
      ```

  - `zip(*iterables)`

    - 복수의 iterable을 모아 튜플을 원소로 하는 zip object 반환

      ```python
      girls = ['jane', 'ashley']
      boys = ['justin', 'eric']
      pair = zip(girls, boys)
      print(pair, type(pari))
      # <zip object at 0x~~~> <class 'zip'>
      
      list(pair)
      # [('jane', 'justin'), ('ashley', 'eric')]
      ```

  - `lambda`

    - 표현식을 계산한 결과값을 반환하는 함수로, 이름이 없는 함수여서 익명함수라고도 불림

      ```python
      def triangle(b, h):
          return 0.5 * b * h
      triangle(5, 6)
      # 15.0
      
      triangle = lambda b, h: 0.5 * b * h
      triangle(5, 6)
      # 15.0
      ```

    - 특징

      - `return` 문을 가질 수 없음
      - 간편 조건문 외의 조건문이나 반복문을 가질 수 없음

    - 장점

      - 함수를 정의해서 사용하는 것 보다 간결
      - `def` 를 사용할 수 없는 곳에서도 사용 가능

- 재귀 함수(Recursive Function)

  - 자기 자신을 호출하는 함수

    ```python
    def factorial(n):
        if n == 0 or n == 1:
            return 1
        else:
            return n * factorial(n-1)
    
    factorial(4)
    # 24
    ```

    

  - 무한한 호출을 목표로 하는 것이 아니며, 알고리즘 설계 및 구현에서 유용하게 활용

    - 알고리즘 중 점화식과 같이 재귀 함수로 로직을 표현하기 쉬운 경우가 있음
    - 변수의 사용이 줄어들며, 코드의 가독성이 높아짐

  - 1개 이상의 base case(종료되는 상황)가 존재하고, 수렴하도록 작성

  - 주의 사항

    - 재귀 함수는 base case에 도달할 때 까지 함수를 호출함

    - 메모리 스택이 넘치게 되면(stack overflow) 프로그램이 동작하지 않게 됨

    - 파이썬에서는 최대 재귀 깊이(maximum recursion depth)가 1,000번으로, 호출 횟수가 이를 넘어가게 되면 RecursionError 발생

      - 다음의 코드로 최대 재귀 깊이 제한을 늘릴 수 있음

        ```python
        import sys
        limit_number = 15000
        sys.setrecursionlimit(limit_number)
        ```

    - 입력 값이 커질 수록 연산 속도가 오래 걸림



## 메소드(Method)

### 문자열(String Type)

| 문법          | 설명                                                         |
| ------------- | ------------------------------------------------------------ |
| `s.find(x)`   | x의 첫 번째 위치를 반환. 없으면 -1 반환                      |
| `s.index(x)`  | x의 첫 번째 위치를 반환. 없으면 오류 발생                    |
| `s.isalpha()` | 알파벳 문자 여부. 단순 알파벳 뿐만 아니라 유니코드 상 Letter(한국어 포함) |
| `s.isupper()` | 대문자 여부                                                  |
| `s.islover()` | 소문자 여부                                                  |
| `s.istitle()` | 타이틀 형식 여부                                             |



### 문자열 변경

| 문법                             | 설명                                                         |
| -------------------------------- | ------------------------------------------------------------ |
| `s.replace(od, new[, count])`    | 바꿀 대상 글자를 새로운 글자로 바꿔서 반환                   |
| `s.strip([chars])`               | 공백이나 특정 문자를 제거                                    |
| `s.split(sep=None, maxsplit=-1)` | 공백이나 특정 문자를 기준으로 분리                           |
| `'seperate'.join([iterable])`    | iterable한 컨테이너 요소들을 separator(구분자)로 합쳐 문자열 반환<br />iterable에 문자열이 아닌 값이 있으면 TypeError 발생 |
| `s.capitalize()`                 | 문자열의 첫 글자를 대문자로 변경                             |
| `s.title()`                      | 문자열 각 단어의 첫 글자와 어퍼스트로피 뒤의 문자를 대문자로 변경 |
| `s.upper()`                      | 문자열을 대문자로 변경                                       |
| `s.lower()`                      | 문자열을 소문자로 변경                                       |
| `s.swapcase()`                   | 문자열의 대문자와 소문자를 서로 변경                         |



## 리스트(List)

| 문법                   | 설명                                                         |
| ---------------------- | ------------------------------------------------------------ |
| `lst.append(x)`        | 리스트 마지막에 항목 x를 추가                                |
| `lst.extend(iterable)` | 리스트에 iterable의 항목을 추가함                            |
| `lst.insert(i, x)`     | 정해진 위치 i에 값을 추가함                                  |
| `lst.remove(x)`        | 리스트에서 값 x 삭제                                         |
| `lst.pop(i)`           | 정해진 위치 i에 있는 값을 삭제하고, 그 항목 반환<br />i가 지정되지 않으면, 마지막 항목 삭제 후 반환 |
| `lst.clear()`          | 모든 항목을 삭제함                                           |
| `lst.index(x)`         | x 값을 찾아 해당 index 값 반환                               |
| `lst.count(x)`         | 원하는 값의 개수를 반환함                                    |
| `lst.sort()`           | 원본 리스트를 정렬함. `None` 을 반환                         |
| `lst.reverse()`        | 순서를 반대로 뒤집음                                         |



## 튜플(Tuple)

- 튜플은 immutable 하기 때문에 값에 영향을 미치지 않는 메소드만 지원
- 리스트 메소드 중 항목을 변경하는 메소드들을 제외하고 대부분 동일



## 집합(Set)

| 문법                | 설명                                            |
| ------------------- | ----------------------------------------------- |
| `st.add(x)`         | 셋에 값을 추가                                  |
| `st.update(*other)` | 여러 값을 추가                                  |
| `st.remove(x)`      | 셋에서 값을 삭제하고, 없으면 KeyError           |
| `st.discard(x)`     | 셋에서 값을 삭제하고, 없어도 에러 발생하지 않음 |
| `st.pop()`          | 임의의 원소를 제거해 반환                       |



## 딕셔너리(Dictionary)

| 문법                    | 설명                                                         |
| ----------------------- | ------------------------------------------------------------ |
| `d.clear()`             | 모든 항목을 제거                                             |
| `d.get(key[, default])` | key를 통해 value를 가져옴<br />key가 없어도 에러 발생하지 않음 |
| `d.pop(key[, default])` | key가 딕셔너리에 잇으면 제거하고 해당 값을 반환<br />그렇지 않으면 default를 반환<br />default 값이 없으면 KeyError |
| `d.update()`            | 값을 제공하는 key, value로 덮어씀                            |
| `d.copy()`              | 얕은 복사본을 반환                                           |
| `d.keys()`              | 모든 key를 담은 뷰를 반환                                    |
| `d.value()`             | 모든 value를 담은 뷰를 반환                                  |
| `d.item()`              | key와 value를 반환                                           |



## 얕은 복사와 깊은 복사(Shallow Copy & Deep Copy)

### 얕은 복사

```python
a = [1,2,3,4]
b = a

b[0] = 5

print(a)
# [5, 2, 3, 4]
print(b)
# [5, 2, 3, 4]

a = [1, 2, 3, 4]
b = a[:]

print(a)
# [1, 2, 3, 4]
print(b)
# [5, 2, 3, 4]

```



### 깊은 복사

```python
a = [1, 2, ['a','b']]
b = a[:]

b[2][0] = 3

print(a)
# [1, 2, [3, 'b']]
print(b)
# [1, 2, [3, 'b']]

import copy
a = [1, 2, ['a','b']]
b = copy.deepcopy(a)

b[2][0] = 3

print(a)
# [1, 2, ['a', 'b']]
print(b)
# [1, 2, [3, 'b']]
```



