# Kotlin #class

## Class 선언

```kotlin
class #ClassName {
  ...
}
```

```kotlin
class A

class A {
  ...
}
```

## 기본 생성자

```kotlin
class #ClassName constructor(...) {
  ...
}

// constructor 생략가능
class #ClassName(...) {
  ...
}
```

```kotlin
class A constructor() {
}

class A constructor(x: Int) {
}

class A() {
}

class A(x: Int, y: String) {
}
```

```kotlin
/* 
parameter의 접두에 var나 val를 붙이면 property가 된다
var는 mutable, val는 read-only
*/
class #ClassName (...
  , var #VariableName: #VariableType
  , ...
  , val #ValueName : #ValueType,
  ...) {
  ...
}
```

```kotlin
class A (x: Int, var y: Int, val z: Int)
val a = A(1,2,3)
// a.x  ->  ERROR
// a.y  ->  2
// a.z  ->  3
// a.y = 1  =>  a.y  ->  1
// a.z = 1  ->  ERROR
```

```kotlin
class #ClassName (...) {
  init {
    ...
  }
  ...
}
```

```kotlin
class A {
  init {
    println("Creat A!!")
  }
}
// A() -> "Creat A!!"

class A(var x: Int) {
  init {
    x = 1
  }
}
// A(2).x -> 1

class A() {
  init {
    var x = 1
  }
}
// A().x -> ERROR

class A {
  var x = 1
  init {
    x = 2
  }
}
// A().x -> 2

class A(x: Int) {
  var x = 1
  init {
    this.x = x
  }
}
// A(2).x = 1
```

## Default

```kotlin
class #ClassName(..., #VariableName: #VariableType = #DefaultValue, ...) {
	...
}
```

```kotlin
class A(x: Int= 0) {
	init {
        	print(x)
	}
}
// A() -> 0
// A(1) -> 1

class A(var x: Int = 0, val y: Int = 1) {
	init {
        	print(x)
		print(y)
	}
}
// A() -> 01
// A(3) -> 31
// A(1,2) -> 12
// A(y=2) -> 02
// A(y=2,x=1) -> 12
// A(1,y=2) -> 12
// A(2,x=1) -> ERROR, 순서는 중요!
// Function의 Default와 비슷하니 Function의 Default 예제 참고
```

## 보조생성자

```kotlin
class #ClassName {
  constructor() {
    ...
  }
  ...
}

class #ClassName(...) {
  ...
  constructor(..., #Varibale: #VaiableType, ...): this(...) {
    ...
  }
  ...
}
```

```kotlin
class A {
  constructor() {
    println("Create A!!")
  }
}
// A() -> "Create A!!"

class A {
  constructor() {
    println("Second!")
  }
  init {
    print("Primary! ")
  }
}
// A() -> "Primary! Second!"

class A {
  init {
    print("I'm ")
  }
  constructor() {
    print("1")
  }
  constructor(x: Int) {
    print("2")
  }
  constructor(x: Int, y: String) {
    print("3")
  }
  constructor(x: Int, y: Int) {
    print("4")
  }
}
// A() -> "I'm 1"
// A(1) -> "I'm 2"
// A(1,"Hello") -> "I'm 3"
// A(1,2) -> "I'm 4"

class A {
  init {
    print("He")
  }
  constructor() {
    print("'s not called")
  }
  constructor(x: Int) {
    print("ll")
  }
  constructor(x: Int,y: Int): this(x) {
    print("o!")
  }
}
// A(1,2) -> "Hello!"
// A(1) -> "Hell"
// A() -> "He's not called"

class A {
  var x: Int? = null
  var y: String? = null
  var z: String = ""
  constructor() 
  constructor(x: Int) {
		this.x = x  
  }
  constructor(x: Int, y: String) : this(x) {
    this.y = y
  }
  constructor(x: Int, y: String, z: String) : this(x,y) {
    this.z = z
  }
}
// A().x -> null
// A(1).x -> 1
// A(1,"1").x -> 1
// A(1,"1","wow").y -> "1"

class A(x: Int) {
  constructor(x: Int, y: Int) : this(x) {
    print(x+y)
  }
  constructor(x: Int, y: String): this(x) {
    print(x)
    print(y)
  }
  constructor(x: Int, y: Int, z: Int): this(x,y) {
   print(x+y+z)
  }
}
// A(1) -> 
// A(1,2) -> 3
// A(1,"2") -> 12
// A(1,2,3) -> 6
```

```kotlin
/* 단순하게 parameter나 property를 입력할때는 아래와 같이 더 자주 사용한다 */

class A(x: Int, var y: Int = 0, val z: Int = 0)
// A(1).y -> 0
// A(1).z -> 0
// A(1,2).y -> 2
// A(1,2).z -> 0
// A(1,z=2).y -> 0
// A(1,z=2).z -> 2

class A<T> (var x: T,val y: Int = 0)
// A(1).x -> 1
// A("Hello").x -> "Hello"
// A(2,1).x -> 2
// A("Hello",1).x -> "Hello"
```

## generated 생성자

- 생성자 선언을 하지않으면 기본적으로 generated 생성자
- 별도의 지정이 없으면 public

```kotlin
class A{
// public
}
```


```kotlin
class A private constructor(){
}
```

## 인스턴스 생성

- 자바와 달리 new 키워드 없이 사용


```kotlin
val instance = my_class()
```

## data class

- 데이터만 표현하기 위한 class
- 프로퍼티에 대한 메소드를 자동으로 지원
- toString(), hashCode(), equals(), copy()

```kotlin
data class A (val B: type){
}
```

- data class의 생성자는 1개 이상의 프로퍼티를 선언해야됨
- 생성자는 val나 var로 선언해야됨
- 보안(abstract,open,sealed,inner)등은 불일 수 없음
- 상속불가


// A().a -> 2
```
