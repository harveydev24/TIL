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

- Java에 있는 삼항 연산자가 없음



### `when`

- `when`문은 C계열 언어의 `switch`문을 대체함

- `when`문은 각각의 branch의 조건문이 만족할 때까지 위에서부터 순차적으로 인자를 비교함

  ```kotlin
  when (x) {
    1 -> print("x == 1")
    2 -> print("x == 2")
    else -> {
      print("x is neither 1 nor 2")
    }
  }
  ```

- `when`문이 식으로 사용된 경우에는 조건을 만족하는 branch의 값이 전체 식의 결과 값이 됨

  ```kotlin
  var res = when (x) {
    100 -> "A"
    90 -> "B"
    80 -> "C"
    else -> "F"
  }
  ```

- `else`의 경우 다른 branch들의 조건이 만족되지 않을 때 수행됨

- `when`이 식으로 사용된 경우 `else`가 필수

- `when`이 식으로 사용된 경우 컴파일러가 `else`가 없어도 된다는 것을 입증할 수 있는 경우에는 `else` 생략 가능

  ```kotlin
  var res = when (x) {
    true -> "맞다"
    false -> "틀리다"
  }
  ```

- 여러 조건들이 같은 방식으로 처리될 수 있는 경우, branch의 조건문에 콤마를 사용하면 됨

  ```kotlin
  when (x) {
    0, 1 -> print("x == 0 or x == 1")
    else -> print("otherwise")
  }
  ```

- branch의 조문에 함수나 식을 사용할 수 있음

  ```kotlin
  when (x) {
    parseInt(x) -> print("s encodes x")
    1 + 3 -> print("4")
    else -> print("s does not encode x")
  }
  ```

- range나 collection에 `in`, `!in`으로 범위 등을 검사할 수 있음

  ```kotlin
  val validNumbers = listOf(3, 6, 9)
  when (x) {
    in validNumbers -> print("x is valid")
    in 1..10 -> print("x is in the range")
    in 10..20 -> print("x is outside the range")
    else -> print("none of the above")
  }
  ```

- `is`, `!is`를 이용하여 타입 검사 가능

  - 이 때 스마트 캐스트가 적용됨

  ```kotlin
  fun hasPrefix(x: Any) = when(x) {
    is String -> x.startsWith("prefix")
    else -> false
  }
  ```

- `when`은 `if-else` 체인을 대체할 수 있음

- `when`에 인자를 입력하지 않으면, 논리연산으로 처리됨

  ```kotlin
  when {
    x.isOdd() -> print("x is odd")
    x.isEven() -> print("x is even")
    else -> print("x is funny")
  }
  ```



### `For`

- `for`문은 iterator를 제공하는 모든 것을 반복할 수 있음

  ```kotlin
  var collection = listOf(1, 2, 3, 4, 5)
  
  for (item in collection) {
    print(item)
  }
  ```

- `for`문을 지원하는 iterator의 조건

  - 멤버함수나 확장함수 중에 `iterator()`, `next()`, `hasNext()`가 `operator`로 구현되어 있어야함

    ```kotlin
    fun main(args: Array<String>) {
      val myData = MyData()
      myData.iterator()
      for (item in myData) {
        print(item)
      }
    }
    
    class MyIterator {
      val data = listOf(1, 2, 3, 4, 5)
      var idx = 0
      
      operator fun hasNext() : Boolean {
        return data.size > idx
      }
      
      operator fun next() : Int {
        return data[idx++]
      }
    }
    
    class MyData {
      operator fun iterator(): MyIterator {
        return MyIterator()
      }
    }
    ```

- 배열이나 리스트를 반복할 때, index를 이용하고 싶다면, `indices`를 이용하면 됨

  ```kotlin
  val array = arrayOf("a", "b", "c")
  
  for (i in array.indices) {
    println("$i: ${array[i]}")
  }
  ```

- `withIndex()`를 사용할 수도 있음

  ```kotlin
  val array = arrayOf("a", "b", "c")
  
  for ((index, value) in array.withIndex()) {
    println("$index: ${value}")
  }
  ```



### `while`

- `while`, `do-while`문은 Java와 거의 같음

  ```kotlin
  while (x > 0) {
    x--
  }
  ```

- `do-while`문에서 body의 지역 변수를 `do-while`의 조건문이 참조할 수 있음

  ```kotlin
  do {
    val y = retrieveData()
  } while (y != null)
  ```

  

## Package

### 패키지

- 소스 파일은 패키지 선언으로 시작 됨
- 모든 콘텐츠(클래스, 함수, ...)는 패키지에 포함 됨
- 패키지를 명시하지 않으면 이름이 없는 기본 패키지에 포함됨



### 기본 패키지

- 기본으로 import 되는 패키지가 있음

  ```kotlin
  kotlin.*
  kotlin.annotation.*
  kotlin.collections.*
  kotlin.comparisons.*
  ...
  ```

- 플랫폼 별로 import 되는 패키지가 있음

  ```kotlin
  JVM:
  	java.lang.*
  	kotlin.jvm.*
  JS:
  	kotlin.js.*
  ```



### Imports

- 기본으로 포함되는 패키지 외에도, 필요한 패키지들을 직접 import할 수 있음

  ```kotlin
  import foo.Bar
  import foo.*
  
  // 이름 충돌 시 as로 로컬 리네임 가능
  import bar.Bar as bBar
  ```

  

## Return and Jumps

### 3가지  Jump 표현식

- `return`: 함수나 익명 함수에서 반환

  ```kotlin
  fun sum(a: Int, b: Int): Int {
    println("a: $a, b: $b")
    return a + b
  }
  ```

- `break`: 루프를 종료 시킴

  ```kotlin
  for (x in 1..10) {
    if (x > 2) {
      break
    }
    println("x: $x")
  }
  ```

- `continue`: 루프의 다음 단계로 진행

  ```kotlin
  for (x in 1..10) {
    if (x < 2) {
      continue
    }
    println("x: $x")
  }
  ```



### Label

- Label로 `break`, `continue` 가능

  ```kotlin
  loop@ for (i in 1..10) {
    for (j in 1..10) {
      println("j: $j")
      if (i + j > 12) {
        break@loop
      }
    }
  }
  
  loop@ for (i in 1..10) {
    for (j in 1..10) {
      if (j > 2) {
        continue@loop
      }
      println("j: $j")
    }
  }
  ```

- Lable로 `return`

  - 코틀린에서 중첩될 수 있는 요소들

    - 함수 리터럴
    - 지역함수
    - 객체 표현식
    - 함수

    ```kotlin
    fun foo() {
      var ints = listOf(0, 1, 2, 3)
      
      ints.forEach(
      fun(value: Int) {
        if (value == 1) return
        print(value)
      })
    }
    ```

 - 람다식 `return` 주의 사항

   - 람다식에서 `return`시 nearest enclosing 함수가  `return`됨

     ```kotlin
     fun foo() {
       var ints = listOf(0, 1, 2, 3)
       ints.forEach {
         if (it == 1) return
         print(it)
       }
       print("End")
     }
     // 0만 출력
     ```

   - 람다식에 대해서만  `return` 하려면, label을 이용해야 함

     ```kotlin
     fun foo() {
       var ints = listOf(0, 1, 2, 3)
       ints.forEach label@ {
         if (it == 1) return@label
         print(it)
       }
       print("End")
     }
     ```

     - 암시적 레이블 쓰면 더 편함

       ```kotlin
       fun foo() {
         var ints = listOf(0, 1, 2, 3)
         ints.forEach {
           if (it == 1) return@forEach
           print(it)
         }
         print("End")
       }
       ```

   - 레이블  `return`시 값을 반환할 경우

     ```kotlin
     fun foo(): List<String> {
       var ints = listOf(0, 1, 2, 3)
       var result = ints.map {
         if (it == 0) {
           return@map "zero"
         }
         "number $it"
       }
       return result
     }
     ```

     



## Classes and Inheritance

### 클래스

- 클래스는  `class` 키워드로 선언함

  ```kotlin
  class Invoice(data: Int) {
  }
  ```

- 헤더와 바디는 옵션이고, 바디가 없으면 중괄호 생략 가능

- 기본 생성자

  - 클래스 별로 1개만 가질 수 있음

  - 클래스 헤더의 일부

  - 클래스 이름 뒤에 작성

    ```kotlin
    class Person constructor(firstName: String) {
    }
    ```

  - 어노테이션이나 접근 지정자가 없을 때는, `constructor` 키워드 생략 가능

    ```kotlin
    class Person(firstName: String) {
    }
    ```

  - 기본 생성자는 코드를 가질 수 없음

    - 초기화는 `init` 블록 안에서 작성해야 함

  - 기본 생성자의 파라미터는  `init` 블록 내부에서 사용 가능함

    ```kotlin
    fun main(args: Array<String>) {
      val obj = Customer("kotlin")
      println(obj)
    }
    
    class Customer(name: String) {
      init {
        println("name: $name")
      }
    }
    ```

  - 기본 생성자의 파라미터는 프로퍼티 초기화 선언에도 사용 가능

    ```kotlin
    class Customer(name: String) {
      val customerKey = name.toUpperCase()
    }
    ```

  - 프로퍼티 선언 및 초기화는 기본 생성자에서 간결한 구문으로 사용 가능

    ```kotlin
    class Person(val firstname: String, val lastName: String)
    ```

  - 기본 생성자에 어노테이션 접근 지정자 등이 있는 경우 `constructor` 키워드가 필요함

    ```kotlin
    class Customer pulbic @Inject constructor(name: String) { ... }
    ```

- 보조 생성자

  - 클래스 별로 여러 개 가질 수 있음

  - `constructor` 키워드로 선언

    ```kotlin
    class Person {
      constructor(parent: Person) {
        parent.children.add(this)
      }
    }
    ```

  - 클래스가 기본 생성자를 가지고 있다면, 각각의 보조 생성자들은 기본 생성자를 직접적 or 간접적으로 위임해주어야 함

  - `this` 키워드 사용

    ```kotlin
    class Person(val name: String) {
      // 직접적 위임
      constructor(name: String, parent: Person): this(name) {
        /* ... */
      }
      
      // 간접적 위임
      constructor(): this("kotlin", Person()) {
        /* ... */
      }
    }
    ```

- 생성된(generated) 기본 생성자

  - 클래스에 기본 생성자나 보조 생자를 선언하지 않으면, 생성된 기본 생성자가 만들어짐

  - generated primary constructor

    - 매개 변수가 없음
    - 가시성이  `public`임

  - 만약 생성된 기본 생성자의 가시성이  `public`이 아니어야 한다면, 다른 가시성을 가진 빈 기본 생성자를 선언해야 함

    ```kotlin
    class DontCreateMe private constructor() {
    }
    ```

- 인스턴스 생성

  - kotlin에는 `new` 키워드가 없음

  - 객체를 생성하려면 생성자를 일반 함수처럼 호출하면 됨

    ```kotlin
    val invoice = Invoice()
    val customer = Customer("Joe Smith")
    ```

- 클래스 멤버
  - 클래스는 다음의 것들을 포함할 수 있음
    - Constructors and initializer blocks
    - Functions
    - Properties
    - Nested and Inner Classes
    - Object Declarations



### Inheritance

- 상속

  - 코틀린의 최상위 클래스는  `Any`

  - 클래스에 상위타입을 선언하지 않으면 `Any`가 상속됨

    ```kotlin
    class Example1 // 암시적인 Any 상속
    class Example2: Any // 명시적인 Any 상속
    ```

  - `Any`는 `java.lang.Object`와는 다른 클래스임

    - `equals()`, `hashCode()`, `toString`만 가지고 있음

  - 명시적으로 상위타입을 선언하려면 클래스 헤더의 콜론 뒤에 상위 타입을 선언하면 됨

    ```kotlin
    open class Base(p: Int)
    
    class Derived(p: Int): Base(p)
    ```

  - 파생 클래스에 기본 생성자가 있으면, 파생클래스의 기본 생성자에서 상위 타입의 생성자를 호출해서 초기화할 수 있음

  - 파생 클레스에 기본 생성자가 없으면, 각각의 보조 생성자에서 상위 타입을  `super` 키워드를 이용해서 초기화 해주거나 다른 생성자에게 상위 타입을 초기화할 수 있게 위임해주어야 함

    ```kotlin
    class MyView: View {
      constructor(): super(1)
      
      constructor(ctx: Int): this()
      
      constructor(ctx: Int, attrs: Int): super(ctx, attrs)
    }
    ```

  - `open` 어노테이션은 Java의 `final`과 반대임
  - `open class`는 다른 클래스가 상속할 수 있음
  - 기본적으로 kotlin의 모든  `class`는 `final`임

- 메서드 오버라이딩

  - 오버라이딩 될 메서드: `open` 어노테이션 필요

  - 오버라이딩 된 메서드: `override` 어노테이션 필요

    ```kotlin
    open class Base {
      open fun v() {}
      fun nv() {}
    }
    
    class Derived: Base {
      override fun v() {}
    }
    ```

- 프로퍼티 오버라이딩

  - 메서드 오버라이딩과 유사한 방식으로 오버라이딩 가능

    ```kotlin
    open class Foo {
      open val x: Int = ...
    }
    
    class Bar: Foo {
      override val x: Int = ...
    }
    ```

- 오버라이딩 규칙

  - 같은 멤버에 대한 중복된 구현을 상속 받은 경우, 상속 받은 클래스는 해당 멤버를 오버라이딩하고 자체 구현을 제공해야 함

  - `super` + <클래스명>을 통해서 상위 클래스를 호출할 수 있음

    ```kotlin
    open class AA() {
      open fun f() {
        println("A")
      }
    }
    
    interface BB {
      open fun f() {
        println("B")
      }
    }
    
    class CC: AA(), BB {
      ovveridde fun f() {
        super<AA>.f()
        super<BB>.f()
      }
    }
    ```

- 추상 클래스

  - `abstract` 멤버는 구현이 없음

  - `abstract` 클래스나 멤버는 `open`이 필요 없음

    ```kotlin
    abstract class AbsClass {
      abstract fun f()
    }
    
    class MyClass(): AbsClass() {
      override fun f() {}
    }
    ```

    

## Properties and Fields

- 프로퍼티 선언

  - 코틀린 클래스는 프로퍼티를 가질 수 있음

    ```kotlin
    class Address {
      var name: String = "Kotlin"
      val city: String = "Seoul"
    }
    ```

  - 프로퍼티 사용은 자바의 필드를 사용하듯이 하면 됨

    ```kotlin
    fun copyAddress(address: Address): Address {
      val result = Address()
      result.name = address.name
      
      return result
    }
    ```

- 프로퍼티 문법

  ```kotlin
  var <propertyName>[: <PropertyType>] [=<property_initializer>]
  	[<getter>]
  	[<setter>]
  ```

  - 생략 가능한 옵션
    - PropertyType
    - property_initializer
    - getter
    - setter

- `var`(mutable) 프로퍼티

  ```kotlin
  class Address {
    var initialized = 1
    
    // 에러 발생
    // default getter와 setter 사용한 경우
    // 명시적 초기화 필요
    var allByDefault: Int? 
  }
  ```

- val(immutable) 프로퍼티

  ```kotlin
  class Address {
    val initialized = 1
    
    // 에러 발생
    // default getter와 setter 사용한 경우
    // 명시적 초기화 필요
    var allByDefault: Int? 
  }
  ```

- Custom accessors (`getter`, `setter`)

  - 프로퍼티 선언 내부에, 일반 함수처럼 선언할 수 있음

    ```kotlin
    //getter
    val isEmpty: Boolean
    	get() = this.size == 0
    
    // setter
    // 관습적으로 setter의 파라미터 이름은 value
    var stringRepresentation: String
    	get() = this.toString()
      set(value) {
        setDataFromString(value)
      }
    ```

- 타입 생략

  - kotlin 1.1 이후로는  `getter`를 통해 타입을 추론할 수 있는 경우, 프로퍼티 타입 생략 가능

    ```kotlin
    val isEmpty
    	get() = this.size == 0
    ```

- accessor에 가시성 변경 또는 어노테이션이 필요한 경우 기본  accessor의 수정 없이 body 없는  accessor를 통해 정의 가능

  ```kotlin
  var setterVisibility: String = "abc"
  	private set
  var setterWithAnnotation: Any? = null
  	@Inject set
  ```

  - body를 작성해도 무관

- Backing Fields

  - kotlin의 클래스는 `field`를 가질 수 없음

  - `field`라는 식별자를 통해 접근할 수 있는 automatic backing field를 제공함

  - `field`는 프로퍼티의  accessor에서만 사용 가능

    ```kotlin
    var counter = 0
    	set(value) {
        if (value >= 0) field = value
      }
    ```

- Backing Fields 생성 조건

  - accessor 중 1개라도 기본 구현을 사용하는 경우

  - custom accessor에서 `field` 식별자를 참조하는 경우

    ```kotlin
    var counter = 0
    	set(value) {
        if (value >= 0) field = value
      }
    ```

  - 아래의 경우 backing field를 생성하지 않음

    ```kotlin
    val isEmpty: Boolean
    	get() = this.size == 0
    ```

- Implicit backing field 방식이 맞지 않는 경우에는 backing property 이용

  ```kotlin
  private var _table: Map<String, Int>? = null
  
  public val table: Map<String, Int>
  	get() {
      if (_table == null) {
        _table = HashMap()
      }
      return _table ?: throw AssertionError("null")
    }
  ```

- Complie-Time Constants

  - const modifier를 이용하면 컴파일 타임 상수를 만들 수 잇음

    - 이런 프로퍼티는 어노테이션에서도 사용 가능

  - 조건

    - top-level

    - object의 멤버

    - String이나 primitive 타입으로 초기화된 경우

      ```kotlin
      const val SUBSYSTEM_DEPRECATED: String = "This subsystem is deprecated"
      
      @Deprecated(SUBSYSTEM_DEPRECATED)
      fun foo() { ... }
      ```

- Late-Initialized Properties

  - 일반적으로 프로퍼티는 non-null 타입으로 선언됨

  - 간혹 non-null 타입 프로퍼티를 사용하고 싶지마느 생성자에서 초기화 해줄 수 없는 경우가 있음

    - Dependency Injection

    - Unit test의 setup 메서드

      ```kotlin
      public class MyTest {
        lateinit var subject: TestSubject
        
        @SetUp fun setup() {
          subject = TestSubejct()
        }
        
        @Test fun test() {
          subejct.method()
        }
      }
      ```

  - 조건
    - 클래스 바디에서 선언된 프로퍼티
      - 기본 생성자에서 선언된 프로퍼티는 안 됨
    - `var` 프로퍼티만 가능
    - custom accessor가 없어야 함
    - non-null 타입이어야 함
    - primitive 타입이면 안됨



## Data, Nested Class

### Data 클래스

- 데이터는 보유하지만 아무것도 하지 않는 클래스

  ```kotlin
  data class User(val name: String, val age: Int)
  ```

- 기본 생성자에서 선언된 속성을 통해, 아래의 기능들을 컴파일러가 자동으로 생성해 줌

  - `equals()`, `hashCode()`, `copy()`, `toString()`, `componentN`

- 명시적으로 정의해주는 경우에는 자동으로 생성해주지 않음

### 의미 있는  Data 클래스의 조건

- 기본 생성자에 1개 이상의 파라미터
- 기본 생성자의 파라미터가 `var`, `val`로 선언
- Data 클래스는 `abstract`, `open`, `sealed`, `inner`가 안됨
- 1.1이후로 Data 클래스 interface 구현 가능

###  기본 값

- 파라미터 없는 생성자가 필요한 경우 모든 프로퍼티에 기본 값을 설정해 주면 됨

  ```kotlin
  data class User(val name: String = "", val age: Int = 0)
  ```

### 복사

- 객체의 기존 값들은 유지하고, 일부 값만 고쳐서 새로운 객체를 만들고 싶은 경우

- Data 클래스에 컴파일러가  `copy`를 만들어 주기 때문에 바로 호출해서 사용하면 됨

  ```kotlin
  val jack = User(name = "Jack", age = 1)
  val olderJack = jack.copy(age = 2)
  ```

### Destructuring Declarations

- Data 클래스는 Destructuring Declarations 사용 가능

- 컴파일러가  `componentN` 함수를 자동으로 만들어 주기 때문

  ```kotlin
  val jane = User("Jane", 35)
  val (name, age) = jane
  ```

### Nested Classes

- 중첩 클래스

  - 클래스는 다른 클래스에 중첩될 수 있음

    ```kotlin
    class Outer {
      private val bar: Int = 1
      
      class Nested {
        fun foo() = 2
      }
    }
    
    val demo = Outer.Nested().foo()
    ```

- 내부 클래스

  - 클래스에  `inner`를 표기하면 바깥쪽 클래스 멤버에 접근할 수 있음

    ```kotlin
    class Outer {
      private val bar: Int = 1
      
    	inner class Inner {
        fun foo() = bar
      }
    }
    
    val demo = Outer.Nested().foo()
    ```



