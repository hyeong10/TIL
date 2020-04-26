```kotlin
/*

Making Function

fun #FunctionName (#Variable: #Type): #ReturnType {
  ...
}

*/

fun func_ex1(): Unit {
  print("Hello World")
}
// Unit시 return값이 없어도 된다

fun func_ex2() {
  print("Hello World")
}
// return 값이 없을 때는 Unit 생략가능 

fun func_ex3(x: String) {
  print(x)
}

fun func_ex4(): String {
  return "Hello World"
}

fun func_ex5(x: Stirng): String {
  y = "Hello World"
  print(x)
  return y
}

fun func_ex6(x: Int, y: Int): Int {
  return x+y
}


fun error_ex(x: Int, y: Int): Int, Int {
  return x, y
}
// ERROR
// return값은 항상 하나여야한다
```

```kotlin
/*

Default Arguments

fun #FunctionName (#VariableName: #Type = #DefaultValue, ...): #ReturnType {
  ...
}

*/

fun default_ex1(x: String = "Hello World"): Unit {
  print(x)
}
// default_ex1() -> "Hello World"
// default_ex2("Hello") -> "Hello"

fun default_ex2(x: Int, y: Int = 2): Int {
  return x + y
}
// default_ex2(1) -> 3
// default_ex2(x=1) -> 3
// default_ex2(1,3) -> 4


fun default_ex3(x: Int = 2, y: Int): Int {
  return x + y
}
// default_ex3(1,3) -> 4
// default_ex3(1) -> ERROR
// default_ex3(y=1) -> 3

fun default_ex4(x: Int, y: Int = 2, z: Int = 3): Int {
  return x + y + z
}
// defalut_ex4(1) -> 6
// default_ex4(1,1) -> 5
// default_ex4(1,1,1) -> 3
// default_ex4(1,z=1) -> 4

fun default_ex5(x: Int = 2, y: Int, z: Int = 3): Int {
  return x + y + z
}
// default_ex5(1) -> ERROR
// default_ex5(1,2) -> 6
// default_ex5(1,2,1) -> 4
// default_ex5(y=1) -> 6

fun default_ex6(x: Int, y: Int = 2, z: Int): Int {
  return x+ y + z
}
// default_ex6(1) -> ERROR
// default_ex6(1,2) -> ERROR
// default_ex6(1,2,3) -> 6
// default_ex6(x=1,z=1) -> 4

fun default_ex7(x: Int = 1, y: Int = 2, func: () -> Unit) {
  print(x)
  func()
  print(y)
}
// default_ex7(2){print("Hello World")} -> 2Hello World2
// default_ex7(2,{print("Hello World")}) -> ERROR

// argument는 항상 선언된 순서대로 들어간다
// default값이 있다면 생략 가능하나 건너뛸수는 없다
// 원하는 parameter는 선언된 이름을 통해 넘겨줄 수 있다
// argument의 순서는 항상 중요하고 이때문에 에러가 발생할 수 있다
// 왠만하면 Default값이 없는 variable을 앞으로 두면 쓰기 편하다!!
// override된 함수의 parameter의 default는 쓰지않아도 부모의 default를 가진다(바꿀 수 없다)
// lambda식이 마지막에 있다면 밖으로 빼서 따로 사용가능하다 (ex7)
```

```kotlin
/*

Sing-expression Function

fun #FunctionName (...): #ReturnType = #ReturnValue 

*/

fun single_expression_ex1(x: Int): Int = x * 2

fun single_expression_ex2(x: Int = 2): Int = x * 2

fun single_expression_ex3(x: Int, y: Int): Int = x + 
```

```kotlin
/*

Variable number of arguments

fun #FunctionName(vararg #VariableName: #VariableType, ...): #ReturnType {
  ...
}

*/

fun varargs_ex1(vararg x: Int): Int {
	return x.component1()
}

fun <T> varargs_ex2(vararg x: T): T {
	return x.component1()
}
```

```kotlin
/*

infix notation

infix fun #Type.#FunctionName(#Variable: #VariableType): #ReturnType {
	...
}

or

class #ClassName {
	infix fun #FunctionName(#Variable: #VariableType): #ReturnType {
		...
	}
}

*/

infix fun Int.infix_ex1(x: Int): Int {
	return this + x
}
// 2.infix_ex1(4) -> 6
// 2 infix_ex1 4 -> 6
// 2.infix_ex1(4*2) -> 10
// 2 infix_ex1 4*2 -> 10

infix fun String.infix_ex2(x: String): String = this + x
// "Hell".infix_ex2("o") -> "Hello"
// "Wor" infix_ex2 "ld" -> "World"

class sample {
    infix fun infix_ex3(x: Int): Int = x*x
    fun build() {
        print(this infix_ex3 2)
	print(this.infix_ex3(2))
	print(infix_ex3(2))
	// infix_ex3 2 -> ERROR, Don't doing this
    }
}
// sample().infix_ex3(2) -> 4
// sample().build() -> 444

// Member Function이나 Extension Function만 가능하다
// Parameter는 하나만 받는다
// Vararg와 Default는 사용할 수 없다
```

```kotlin
/*

Generic Function

fun <T> #FunctionName(#VariableName: T): #ReturnType {
	...
}

fun <T1, ...> #FunctionName(#VariableName: T1, ...): #ReturnType {
	...
}

*/

fun <T> generic_ex1(item: T): T {
	return item
}
// generic_ex1(1) -> 1
// generic_ex1("Hello World") -> "Hello World"

fun <hyeong> generic_ex2(item: hyeong): hyeong {
	return item
}
// generic_ex2(1) -> 1
// generic_ex2("Hello World") -> "Hello World"

fun <T1,T2> generic_ex3(item1: T1, item2: T2): T1 {
    	return item1
}
// generic_ex3(1,2) -> 1
// generic_ex3("Hello World",2) -> Hello World

fun <T1,T2> generic_ex4(item: T1): T1 {
	return item
}
// generic_ex4(1) -> ERROR
// generic_ex4(1,2) -> ERROR
// generic_ex4<Int,Any>(1) -> 1
// generic_ex4<String,Int>("Hello World") -> Hello World

```
