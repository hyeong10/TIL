# 람다 문법
- kotlin의 람다 문법은 자바와 비슷함
- {인자: 타입 -> 본문} 과 같은 형식을 가진다
- 타입은 생략이 가능하다. 다만 변수에 람다식을 담으면 생략이 불가하다

```kotlin
{x: Int, y -> x+y}
val sum = {x: Int, y: Int -> x+y}
sum(1,2) // 3
list.maxBy(){x: Int -> x} 
// list.maxBy({x: Int -> x}) 마지막인자면 위에같이 밖으로 뺄 수 있다
// list.maxBy{x: Int -> x} 인자가 하나면 ()를 생략가능하다
// list.maxBy{it} 람다의 파라메터가 하나고 추론가능하면 it을 사용할 수 있다
// people.maxBy{x: Person -> x.age}
// people.maxBy{it.age}
```
