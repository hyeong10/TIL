# Higher-Order Function
- 함수를 변수로 넘겨주거나 반환하는 함수
- 말그대로 함수위의 고위함수

```kotlin
fun print(body: () -> String) {
  println(body())
}

fun main() {
  print({"Sample Test"})
  // "Sample Test"
}
```

```kotlin
fun print(body: (String) -> String) {
  println(body("Sample"))
}

fun main() {
  print({a -> "$a Test"})
  // print({$it Test})
  // print(){"$it Test"}
  // "Sample Test"
}
```

```kotlin
fun print(body: (String, String) -> String) {
  println(body("Sample", "Test"))
}

fun main() {
  print({a,b -> "$a $b"})
  // "Sample Test"
}
```
