# Kotlin

## Basic Syntax

### 패키지 정의

- 패키지 정의는 파일 최상단에 위치
- 디렉터리와ㅏ 패키지를 일치시키지 않아도 됨



### 함수 정의

- 함수는 `fun` 키워드로 정의

 ```kotlin
 fun sum(a: Int, b: Int): Int {
 	return a + b
}
 ```

- 함수 몸체가 식(Expression)인 경우 `return` 생략 가능
- 이런 경우 `return type`이 추론됨

 ```kotlin
fun sum(a: Int, b: Int) = a + b
 ```

- 리턴 할 값이 없는 경우 `Unit(Object)`으로 리턴 함
- Unit은 Java에서 void 리턴 역할

 ```kotlin
 fun printKotlin(): Unit {
 	println("Hello, Kotlin")
}
 ```

- Unit은 생략 가능

 ```kotlin
fun printKotlin() {
    println("Hello, Kotlin")
}
 ```



### 지역 변수 정의

- `val`: 읽기 전용 변수

  - 값의 할당이 1회만 가능

    - Java의 `final`과 유사

    ```kotlin
    val a: Int = 1 // 즉시 할당
    val b = 2 // 'Int' type 추론
    val c: Int // 컴파일 오류, 초기화가 필요
    c = 3 // 컴파일 오류, 읽기 전용
    ```

- var: Mutable 변수

  ```kotlin
  var x = 5
  x += 1
  ```



### 주석

- Java와 동일함

  ```kotlin
  // 한 줄 주석
  
  /*
  여러 줄 주석
  */
  ```

### 문자열 템플릿

- String Interpolation

  ```kotlin
  var a = 1
  val s1 = "a is $a"
  
  a = 2
  val s2 = "$(s1.replace("is", "was")), but now is $a"
  ```



### 조건문

```kotlin
fun maxOf(a: Int, b: Int): Int {
  if (a > b) {
    return a
  } else {
    return b
  }
}

fun maxOf(a: Int, b: Int) = if (a > b) a else b
```



### Nullable

- 값이 `null`일 수 있는 경우에 타입에 nullable을 명시 해야 함

  ```kotlin
  fun parseInt(str: String): Int? {
    // 정수가 아닌 경우 null을 리턴
  }
  ```

- nullable 타입의 변수를 접근 할 때는 반드시 `null` 체크를 해야 함

  ```kotlin
  fun printProduct(arg1: String, arg2: String) {
    val x: Int? = parseInt(arg1)
    val y: Int? = parseInt(arg2)
    
    if (x != null && y != null) {
      println(x * y)
    } else {
      println("either '$arg1' or '$arg2' is not a number")
    }
  }
  ```



### 자동 타입 변환

- 타입 체크만 해도 자동으로 타입이 변환 됨

  ```kotlin
  fun getStringLength(obj: Any): Int? {
    if (obj is String) {
      return obj.length
    }
    return null
  }
  ```



### When Expression

```kotlin
fun describe(obj: Any): String =
	when (obj) {
    1 -> "One"
    "Hello" -> "Greeting"
    is Long -> "Long"
    !is String -> "Not a string"
    else -> "Unknown"
  }
```



### Range

- `in` 연산자를 이용해서 숫자 범위 체크 가능

  ```kotlin
  val x = 3
  
  if (x in 1..10) {
    println("fits in range")
  }
  ```

- range를 이용한 `for` loop

  ```kotlin
  for (x in 1..5) {
    print(x)
  }
  ```

  

### Collections

- 컬렉션도 `in`으로 loop 가능

  ```kotlin
  val items = listOf("apple", "banana", "kiwi")
  
  for (item in items) {
    println(item)
  }
  ```

- `in` 으로 해당 값이 컬렉션에 포함되는지 체크 가능

  ```kotlin
  val items = setOf("apple", "banana", "kiwi")
  
  when {
    "orange" in items -> println("juicy")
    "apple" in items -> println("apple is fine too")
  }
  ```

- 람다식을 이용해서 컬렉션에 `filter`, `map` 등의 연산 가능

  ```kotlin
  val items = listOf("apple", "banana", "kiwi")
  
  fruits
  	.filter { it.startsWith("a") }
  	.sortedBy { it }
  	.map { it.toUpperCase() }
  	.forEach { println(it) }
  ```

  



## Basic Types

### 기본 타입

- 코틀린에서는 모든 것이 객체
- 모든 것에 멤버 함수나 프로퍼티 호출 가능



### 숫자

- Java의 숫자형과 거의 비슷하게 처리
- Kotlin에서 Number는 클래스임
- Java의 primitive type에 직접 접근할 수 없음
- Java에서 숫자형이던 `char`가 kotlin에서는 숫자 형이 아님



### 리터럴

- 10진수: 123 (`Int`, `Short`)
- `Long`: 123L
- `Double`: 123.5, 123.5e10
- `Float`: 123.5f
- 2진수: 0b00001011
- 8진수: 미지원
- 16진수: 0X0F



### Underscores in numeric literals (since 1.1)

```kotlin
val oneMillion = 1_000_000
val creditCardNumber = 1234_5678_9012_3456L
val bytes = 0b11010010_01101001_10010100_10010010
```



### Representation

- Java에서 숫자형은 JVM primitive type으로 저장됨

- Nullable이나 제네릭의 경우에는 박싱됨

- 박싱된 경우 identity를 유지하지 않음

  ```kotlin
  val a: Int = 100
  print(a === a) // true
  
  val boxedA: Int? = a
  val anotherBoxedA: Int? = a
  println(boxedA == anotherBoxedA) // true
  println(boxedA === anotherBoxedA) // true
  ```



### Explicit Conversions

- 작은 타입은 큰 타입이 하위 타입이 아님

- 즉, 작은 타입에서 큰 타입으로 대입 불가

- `toXXX`로 명시적 형변환을 해주어야 함

  ```kotlin
  val a: Int = 1
  val b: Long = a.toLong()
  ```

  

### 문자

- `Char`은 숫자로 취급 되지 않음

  ```kotlin
  fun check(c: Char) {
    if (c == 1) { /*...*/ } // ERROR
  }
  
  fun check(c: Char) {
    if (c == 'a') { /*...*/ } // OK
  }
  
  print('0'.toInt()) // print 48
  ```



### 배열

- 배열은 `Array` 클래스로 표현됨

- `get`, `set` (`[]` 연산자 오버로딩 됨)

- `size` 등 유용한 멤버 함수 포함

  ```kotlin
  var array: Array<String> = arrayOf("kotlin", "Java")
  
  println(array.get(0))
  println(array[0])
  println(array.size)
  ```

- 생성

  - `Array`의 팩토리 함수 이용

    ```kotlin
    val array = arrayOf("0", "1", "2")
    ```

  - `arrayOf()` 등의 라이브러리 함수 이용

    ```kotlin
    val array = Array(3, { i -> i.toString() })
    ```

- 특별한 `Array` 클래스

  - Primitive 타입의 박싱 오버헤드를 없애기 위한 배열

    - `null`이 필요 없이 숫자만 필요한 경우 사용

  - `IntArray`, `ShortArray`, `IntArray`

  - `Array`를 상속한 클래스들은 아니지만, `Array`와 같은 메소드와 프로퍼티를 가짐

  - `size` 등 유용한 멤버 함수 포함

    ```kotlin
    val array: IntArray = intArrayOf(1, 2, 3)
    
    array[0] = 7
    
    println(array.get(0))
    println(array[0])
    println(array.size)
    ```

    

### 문자열

- 문자열은 `String` 클래스로 표현

- `String`은 `characters`로 구성

- `s[i]`와 같은 방식으로 접근 가능

  - immutable이므로 변경 불가

  ```kotlin
  var x: String = "Kotlin"
  
  println(x.get(0))
  println(x[0])
  println(x.length)
  
  for (c in x) {
    println(c)
  }
  ```

  

### 문자열 리터럴

- Escaped String (`"Kotlin"`)

  - Java의 `String`과 거의 비슷
  - Backslash를 사용하여 escaping 처리

- Raw String(`"""Kotlin"""`)

  - escaping 처리 필요 없음

  - 개행 등 어떠한 문자도 포함 가능

    ```kotlin
    val s = "Hello, world!₩n"
    
    val s = """
    	'This is Kotlin's Raw String'
    """
    ```

    

## Control Flow

### `if else` 문

- Java와 거의 유사함

  ```kotlin
  var max: Int
  
  if (a < b) {
    max = a
  } else {
    max = b
  }
  
  var max = a
  if (a < b) max = b
  ```

- `if`문이 식으로 사용되는 경우 값을 반환함

- `if`식의 경우 반드시 `else`를 동반해야 함

  ```kotlin
  val max = if (a < b) a else b
  ```

- `if`식의 branch들이 블럭을 가질 수 있음

  ```kotlin
  val max = if (a > b) {
    print("Choose a")
    a
  } else {
    print("Choose b")
    b
  }
  ```



