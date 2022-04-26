# Java

## 변수와 타입

### JVM

- 자바 바이트코드를 실행할 수 있는 주체
- 자바 바이트 코드는 플랫폼에 독립적이며, 모든 JVM은 규격에 정의된 대로 자바 바이트코드를 실행



### 메인 메서드

```java
public static void main(String[] args){}
```

- 실행 명령인 `java`를 실행 시 가장 먼저 호출 되는 부분
- Application에 `main()` 메서드가 없다면 절대로 실행 될 수 없음
  - Application의 시작 = 특정 클래스의 `main()` 실행



### 변수

- 정의
  - 데이터를 저장할 메모리의 위치를 나타내는 이름
    - 메모리의 단위
      - 0과 1을 표현하는 bit
        - 8bit = 1byte
  - 메모리 상에 데이터를 보관할 수 잇는 공간을 확보
  - 적절한 메모리 공간을 확보하기 위해서 변수의 타입 등장
  - `=`를 통해서 CPU에게 연산작업을 의뢰

- 선언

  - 자료형 변수명

    ```java
    int age;
    ```

- 초기화

  - 변수형 = 저장할 값

    ```java
    age = 30;
    ```

- 선언과 초기화를 동시에

  ```java
  int age = 30;
  ```

- 대소문자를 구분함
- 공백 허용X
- 숫자로 시작할 수 없음
- $와 _를 변수이름에 사용할 수 있음
  - 이외의 특수문자는 허용X
- 예약어 사용X
  - 자바 문법을 위해서 미리 지정되어있는 단어
  - `abstract, if, final` 등



### 자료형

- 기본 자료형

  - `boolean`

    - 1byte
    - 기본값 `false`

  - `char`

    - 2byte
    - `null`

  - 정수형

    - `byte`
      - 1byte
      - (byte)0
    - `short`
      - 2byte
      - (short)0
    - `int`
      - 4byte
      - 0
    - `long`
      - 8byte
      - 0L

  - 실수형

    - `float`
      - 4byte
      - 0.0f
    - `double`
      - 8byte
      - 0.0d

  - 데이터의 형변환

    - 묵시적 형변환

      - 범위가 넓 데이터 형에 좁은 데이터 형을 대입하는 것

        ```java
        byte b = 100;
        int i = b;
        ```

    - 명시적 형변환

      - 범위가 좁은 데이터 형에 넓은 데이터 형을 대입하는 것

        ```java
        int i = 100;
        byte b = (byte)i;
        ```

- 참조 자료형



### 연산자

- 3항 연산자

  ```java
  int a = 10;
  int b = 5;
  
  int max = (a>b) ? a : b;
  ```

- 산술 연산자
  - `+, -, *, /`
- 증감 연산자
  - `++, --`
- 비교 연산자
  - `>, >=, <, <=, ==, !=, instanceof`
- 조건 연산자
  - `&&, ||, |`
- 배정 연산자
  - `+=, -=, *=, /=`



### 조건문

- `if`

  ```java
  if (condition) {
      // do something
  } else if (condition) {
      // do something
  } else {
      // do something
  }
  ```

- `switch`

  ```java
  switch (value) {
      case value1:
          // do something
          break;
      case value2:
          // do something
          break;
      default:
          //do something
  }
  ```



### 반복문

- `for`

  ```java
  for (초기값; 조건; 증감) {
      // do something
  }
  ```

- `while`

  ```java
  while (조건) {
      // do something
  }
  ```

- `do ~ while`

  ```java
  do {
      // do something
  } while (조건)
  ```

  - `while`이 무조건 한 번은 실행됨

- `break`
  - `switch`문, 반복문을 벗어나는데 사용

- `continue`
  - 반복문의 특정지점에서 제어를 반복문의 처음으로 보냄



### 배열

- 같은 종류의 데이터를 저장하기 위한 자료구조

- 크기가 고정되어 있어 한 번 생성된 배열은 크기를 바꿀 수 없음

- 배열을 객체로 취급

- int 유형의 정수값인 index로 참조

- 배열이 생성되면 배열 요소는 자동적으로 기본값으로 초기화

  ```java
  // 1차원 배열
  int[] prime = new int [10];
  System.out.println(prime.length) // 10
      
  // 2차원 배열
  int[][] prime = new int [3][2];
  ```

- `for-each`

  - 배열 및 Collections에서 사용

  - index 대신 직접 요소에 접근하는 변수를 제공

    ```java
    int intArray [] = { 1, 3, 5, 7, 9 }
    
    for (int x: intArray) {
        System.out.println(x)
    }
    ```



## 클래스

- 관련 있는 변수와 함수를 묶어서 만든 사용자 정의 자료형
- 모든 객체들의 생산처
  - 객체를 생성하는 틀
  - 각 객체의 속성과 동작을 결정



### 객체의 구성

```java
class TV {
    // 속성 (Attribute)
    int channel;
    int volumn;
    
    // 동작 (Method)
    public void channelUp() {
    }
    public void channelDown() {
    }
}

TV tv = new TV();
tv.channelDown();
```



### 메서드

- 객체가 할 수 있는 행동을 정의

- 메서드명은 소문자로 시작

  ```java
  class TV {
  	...
      public void channelUp() {   
      }
  }
  ```

- `static`으로 선언된 경우에는 클래스이름.메서드명 으로 호출



### 생성자

- 클래스 명과 이름이 동일
- 반환타입이 없음
- 디폴트 생성자
  - 클래스 내에 생성자가 하나도 정의되어 있지 않으면, JVM이 자동으로 제공하는 생성자
- 오버로딩 지원
- 객체를 생성할 때 속성의 초기화 담당



