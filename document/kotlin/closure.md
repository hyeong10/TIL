# Closure

- Outer Scope의 변수를 접근할 수 있는 함수
- 자기 영역에서 선언되지 않고 상위 영역에서 선언된 변수에 접근할 수 있는 것을 의미

```kotlin
fun myPrint(x: String): () -> Unit{
  return func() {
    print(x)
  }
}

fun main() {
  val myfunc = myPrint("Hello World")
  myfunc()
  // "Hello World"는 매개변수로 x에 할당된다
  // myPrint가 종료됨에 따라 x는 반환된다
  // 하지만 func()안의 Kotlin는 Closure를 지원하기에 변수 참조를 가능하게 한다
  // 그래서 myfunc를 실행하면 "Hello World"를 출력한다
}
```

```kotlin
var sum = 0
// ints is list of [1, 2, 3, 4, 5]
ints.forEach {
  sum += it
  // forEach는 함수를 인자로 받는다
  // sum += it 이라는 Lambda 함수식
  // sum은 함수 외부에서 선언되었으나 활용가능
}
print(sum)
// 15
```

```kotlin
var x = 5

view.setOnClickListener {
  println(x)
}
// x는 외부에서 선언되었다
// x값이 변함에 따라 내부의 x출력값도 같이 변함
```
