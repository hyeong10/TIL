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

// 왠만하면 Default값이 없는 variable을 앞으로 두자!

```
