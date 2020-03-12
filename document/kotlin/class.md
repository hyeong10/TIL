# Kotlin #class

## Class 선언

```kotlin
class class이름(data: type){
}
```

- 헤더와 바디는 옵션

```kotlin
class class이름
```

## 기본 생성자

- 클래스당 1개만 가능

```kotlin
class class이름 constructor(data: type){
}
```

- constructor는 생략가능 (어노테이션 접근지정자시 불가)


```kotlin
class class이름(data: type){
}
```

- 생성자내에 쓰고싶은 코드는 init키워드사용
- 기본생성자의 파라매터는 init 블록 안에서 사용가능!!

```kotlin
class class이름(data: type){
  init{
    logger.info("class 생성 확인 ${data}")
  }
}
```

- 기본생성자는 초기화 선언에도 사용가능

```kotlin
class class이름(data: type){
  val parameter: type = data
}
```

- 더 간결한 구문으로 초기화 가능

```kotlin
class class이름(val parameter: type){
}
```

## 보조생성자

- 여러개 사용 가능

```kotlin
class A{
  constructor(a: A){
  }
}
```


```kotlin
class A(val data: type){
  constructor(data: type,a: A) : this(data){
  // 직접적으로 A를 부른다
  }
  
  constructor() : this(temp_data,A()){
  // 간접적으로 위에 constructor를 부르고 이를 통해 A를 부른다
  }
}
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

