# Property

## Declaring Properties

```kotlin
// Mutable one
var #VariableName: #VariableType = #DefaultValue

// Read-Only
val #ValueName: #ValueType = #DefaultValue
```

```kotlin
var x: Int = 2
val y: String = "Hello World"
val z: Int = 3
```

## Getter and Setter
```kotlin
// "val"은 Read-Only기에 setter를 사용할 수 없다 
// 'field'를 통해 parameter의 Backing field를 이용
var #VariableName: #VariableType = #DefaultValue
    set(#ParameterName) {
        ...
        field = #SetterValue
    }
    get() {
      ...
      return #GetterValue
    }
val #ValueName: #ValueType
    get() {
      ...
      return #GetterValue
    }
// val #ValueName: #ValueType = #DefaultValue



// How to Set
#InstanceName.#PropertyName = #SettingValue
// How to Get
#InstanceName.#PropertyName
```

```kotlin
class A {
	  var a: Int = 1
    
	  val b: Int = 1
    
    var c: Int = 1
    set(value) {
        field = value*2
    }
    
    var d: Int = 1
    get() = field * 3
    
    var e: Int = 1
    set(value) {
        field = value*2
    }
    get() {
        return field * 3
    }
    
    val f: Int
    get() {
        return 1
    }
}

var x = A()
// x.a -> 1
// x.a = 2  =>  x.a -> 2
// x.b -> 1
// x.b = 2 -> ERROR, val can't be resignned
// x.c -> 1
// x.c = 1  =>  x.c -> 2
// x.d -> 3
// x.d = 2  =>  x.d -> 6
// x.e -> 3
// x.e = 1  =>  x.e -> 6
// x.f -> 1
// x.f = 2 -> ERROR, val can't be resignned


class A {
    var x: Int = 0
    val y: Int
    get() {
        x = 1
        return 1
    }
}
var a = A()
print(a.x) // 0
print(a.y) // 1
print(a.x) // 1

// Private Set
class A {
    var a: Int = 0
    private set
    var b: Int = 0
    private set(value) {
      field = value
    }
}
// When using in the class
// this.a = 2  =>  A().a -> 2
// or A().a = 2  =>  A().a -> 2
// when using not in the class
// A().a = 2 -> ERROR


// Backing Properties: ?? 솔직히 backing field를 사용하지 않는다는 것뿐 뭐가 다른지 모르겠음
// kotlin 기본 예제
private var _table: Map<String, Int>? = null
public val table: Map<String, Int>
    get() {
        if (_table == null) {
            _table = HashMap() // Type parameters are inferred
        }
        return _table ?: throw AssertionError("Set to null by another thread")
    }
```
