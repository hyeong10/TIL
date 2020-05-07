# class

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

```kotlin
// 생성자 선언을 하지않으면 generated 생성자가 만들어진다
// 기본적으로 public이다
class #ClassName {
	...
}

// private한 class를 만들고 싶다면 아래와 같이 한다
class #ClassName private constructor() {
	...
}
```

## 인스턴스 생성

```kotlin
var #InstanceName = #ClassName(...)

val #InstanceName = #ClassName(...)
```

```kotlin
// class A
val a = A()
var b = A()

// class A(var x: Int)
var a = A(1)
val b = A(2)

// class A(var x: Int, val y: String)
val a = (1,"Hello")
var b = (2,"World")
```

## Inheritance

```kotlin
open class #ParentClass(...)
class #ChildClass(...): #ParentClass(...) {
	...
}
```


```kotlin
open class ParentA
class A(x: Int): ParentA()

open class ParentA(x: Int)
class A(val x: Int): ParentA(x)

open class ParentA(x: Int)
class A: ParentA()
// ERROR

open class ParentA(x: Int)
class A: ParentA(x)
// ERROR

open class ParentA(x: Int = 0)
class A: ParentA()

open class ParentA(a: Int)
class A(x: Int): ParentA(x)

open class ParentA(var a: Int)
class A(x: Int): ParentA(x)
// A(1).x -> 1

open class ParentA(var x: Int)
class A(var x: Int): ParentA(x)
// ERROR
// x를 override하지 않았으므로 ERROR발생

open class ParentA(x: String, var y: Int=0)
class A(x: String): ParentA(x)
// A("Hello").y -> 0

class A: Any()
// class A와 같다
// Any는 Kotlin의 최상위 클래스로 자동으로 상속된다


open class ParentA() {
	fun myPrint() {
		print("Hello World")
	}
}
class A: ParentA()
// A().myPrint() -> "Hello World"

open class ParentA(var x: Int){
	fun myPrint() {
		print(x)
	}	
}
class A(x: Int): ParentA(x)
// A(1).myPrint() -> 1


// 자식 class는 부모 class의 초기화 되지않은 parameter를 전부 채울 필요가 있다
// 물려받은 property와 method는 override하지않는다면 전적으로 부모의 것을 따른다
```

## Override method

```kotlin
open class #ParentClass (...) {
	...
	open fun #ParentFunction (...) {
		...
	}
	...
}
class #ChildClass (...): #ParentClass {
	...
	override fun #ParentFunction (...) {
		...
	}
	...
}

// 상속된 class의 자식들에게 fun의 overriding을 막고싶다면 final을 붙인다
class #ChildClass (...): #ParentClass {
	...
	final override fun #ParentFunction (...) {
		...
	}
	...
}
```

```kotlin
class ParentA {
	open fun myPrint(){
		print("Parent")
	}
}
class A: ParentA {
	override fun myPrint(){
		print("Child")
	}
}
// A().myPrint() -> "Child"

class ParentA {
	open fun myPrint(x: Int){
		print("Parent")
	}
}
class A: ParentA {
	override fun myPrint(){
		print("Child")
	}
}
// A().myPrint() -> ERROR
// override된 함수의 parameters는 맞춰야한다

class ParentA {
	open fun myPrint(){
		print("Parent")
	}
}
class A: ParentA {
	override fun myPrint(){
		super().myPrint()
		print("Child")
	}
}
// A().myPrint() -> "ParentChild"
```

## Overriding Properties

```kotlin
open class #ParentClass (open var #VariableName: #VariableType, ...)
class #ChildClass (override var #VariableName: #VariableType, ...): #ParentClass(...)
// Not recommeded

open class #ParentClass (open val #ValueName: #ValueType, ...)
class #ChildClass (override val #ValueName: #ValueType, ...): #ParentClass(...)
// Not recommeded

open class #ParentClass (...) {
	oepn val #ValueName: #ValueType = #DefaultValue
}
class #ChildClass (...): ParentClass(...) {
	oepn val #ValueName: #ValueType = #AnotherValue
}

open class #ParentClass (open var #VariableName: #VariableType, ...)
class #ChildClass (...): ParentClass(...) {
	open var #VariableName: #VariableType = #AnotherValue
}
```

```kotlin
open class ParentA (open var x: Int)
class A(a: Int): ParentA(a) {
	override var x: Int = a
}

open class ParentA (open var x: Int)
class A(x: Int): ParentA(x) {
	override var x: Int = x
}
// 위와 같다

open class ParentA (open var x: Int)
class A(x: Int): ParentA(x) {
	override var x: Int = 2
}
// A(1).x -> 2

open class ParentA {
	open var x: Int = 0
}
class A: ParentA() {
	override var x: Int = 2
}
// A().x -> 2

open class ParentA {
	open var x: Int = 0
}
class A(override var x: Int): ParentA()
// A(2).x -> 2

```

## Derived class initialization order

```kotlin
open class Base(val name: String) {

    init { println("Initializing Base") }

    open val size: Int = 
        name.length.also { println("Initializing size in Base: $it") }
}

class Derived(
    name: String,
    val lastName: String
) : Base(name.capitalize().also { println("Argument for Base: $it") }) {

    init { println("Initializing Derived") }

    override val size: Int =
        (super.size + lastName.length).also { println("Initializing size in Derived: $it") }
}
// 공식 kotlin 예시
```

```
// Derived("hello", "world")
Argument for Base: Hello
Initializing Base
Initializing size in Base: 5
Initializing Derived
Initializing size in Derived: 10
```
## Super

```kotlin
open class ParentA {
	var x: Int = 0
	open val y: String? = "Parent"
	fun X() {
		println("I'm Parent Func")
	}
	open fun Y() {
		println(y)
	}
}

class A: ParentA() {
	// var x: Int = super.x  -> ERROR, If you want to use this Function, you have to override
	override var y: String? = "Child"
	/* 
	fun X() {
		super.X()
		println("No! I'm Child Func")
	}
	ERROR, If you want to use this Function, you have to override
	*/
	override fun Y() {
		super.Y()
		println(y + super.y)
	}
}

// A().Y() -> "Parent/nChildParent"
```

## Abstract

```kotlin
abstract class #ClassName(...) {
	abstract var #VariableName: #VareiableType
	abstract fun #FunctionName (...) {
		...
	}
}
```

```kotlin
abstract class AbstractA {
	// abstract var x: Int = 0 , ERROR
	abstract var x: Int
	abstract fun X()
}
class A: AbstractA() {
	// var x = 0 , ERROR
	override var x = 1
	// fun X() , ERROR
	override fun X() {
		print("Hello World")
	}
}


open class ParentA {
	var x: Int = 0
	open val y: Int = 0
	fun X() {println("PX")}
	open fun Y() {println("PY")}
}
abstract class AbstractA: ParentA() {
	// abstract var x: Int , ERROR
	abstract override var y: Int
	// abstract override var y: Int = 0 , ERROR. Default값은 설정할 수 없다
	var z: Int = 1
	// abstract fun X() , ERROR
	abstract override fun Y()
	// abstract override fun Y() {} , ERROR. Body는 비워야한다
	fun Z() {println("AZ")}
}
class A: AbstractA() {
	override var y: Int = 0
    	override fun Y() {println("Y")}
	// 반드릿 abtract멤버는 override해줘야한다
}
// A().X() -> "PA"
// A().Y() -> "Y"
// A().Z() -> "AZ"
```

## Interface

```kotlin
interface #InterfaceName {
	var #VarialbeName: #VariableType
	val #ValueName: #ValueType
	fun #FunctionName(...) {
		// optional, 쓰게되면 굳이 자식 class에서 override하지 않아도 된다
	}
}
class #ClassName: #InterfaceName {
	...
}
```

```kotlin
// interface InterfaceA() , ERROR. Interface는 contructor가 없다
interface InterfaceA {
	var x: Int
	// var x: Int = 0 , ERROR
	fun X() { print("OptionX") }
	fun Y(x: Int)
	fun Z(x: Int) { print("OptionZ") }
}

class A: InterfaceA {
    override var x: Int = 0
    override fun X() { super.X() }
    override fun Y(x: Int) { print("Y") }
}
// 
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
