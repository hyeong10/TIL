# Null

## NullPointerException, Nullable

- 자바에서는 null 체크를 하지않고 run time시 null이 들어오면 NullPointerException이 발생
- Kotlin에서는 타입뒤에 ```?```를 붙임으로서 null이 가능한 변수임을 표현한다
```kotlin
val a: String? = null
```
```kotlin
fun myFunc(a: String?): Int {
  return if(a != null) a.length else 0
}
// nullable하면 사용시 null 체크를 꼭해줘야한다
// 아닐시 컴파일 에러
```

## Null Safe Operator

- 변수값이 null이 아닐때만 사용하고 싶다면 ```?.``` 연산자를 사용하면 된다
- 이때 변수값이 null이라면 null을 반환한다

```kotlin
fun myFunc(a: String?): Int {
  val result = a?.length
  return if (result != null) result else 0
}
```

```kotlin
class Friend(val person: Person?)

class Person(val name: String)

fun myFunc(friend: Friend): String? {
  return friend.person?.name
}
```

## Elvis Operator
- null일 때 따로 default로 처리하고싶다면 ```?:``` 연산자를 사용하면된다
- 아래를 보면 쉽게 파악할 수 있다

```kotlin
fun myFunc(str: String?) {
  val tmp_str = str ?: "I'm Null"
  // val tmp_str = if (str != null) str else "I'm Null"
}
```

## !!
- Kotlin은 nullable한 값을 null check하지않고 사용시 컴파일에러가 발생
- 이때 강제적으로 이행하고 싶다면 ```!!``` 연산자를 사용한다
- 강제로 실행하기에 null값이 들어오면 NullPointerException이 발생한다

```kotlin
fun myFunc(a: String?) {
  val b: String = a!!
}
```

```kotlin
class Friend(val person: Person?)

class Person(val name: String)

fun myFunc(friend: Friend): String? {
  return friend.person!!.name
}
```
