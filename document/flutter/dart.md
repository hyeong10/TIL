# Dart
- java와 문법은 비슷
- 변수 선언시 java와 같이 타입선언 할 수 있고 var로 타입선언없이 할 수 있다
- dynamic은 아무 객체나 들어올 수 있는 변수를 의미한다 (java의 Object)
- dart는 서로다른 타입간의 타입캐스팅이 반드시 필요하다 (int a = 3; double b = a; ERROR!!)
- num 타임은 int와 double 둘다 가능한 타입
- final은 타입을 생략해서 쓸 수 있다 (final a = 1;, 동적으로 값 저장)
- const도 타입을 생략해서 쓸 수 있다 (컴파일시 값 저장)
- Collection은 List<int> item = [1,2,3]과 같이 할 수 있으나 타입 추론이 가능하기에 var item = [1,2,3]과 같이 할 수 있다
- List는 [], Set은 {}, Map은 {:}
- ...을 통해 Collection을 더할 수 있다 (var a = [1,2]; var b = [...a,3,4];  b는 [1,2,3,4]가 된다)
- 매개변수를 {}을 통해 옵션지정할수있다. 오버로드를 위해 사용 (void func({int a})란 함수가 있다면 함수 사용시 func(a: 10)과 같이 사용)
- 더 자세히 하면 옵션을 하고 싶은 매개변수만 옵션처리할 수 있다. 옵견은 Defalut값을 선언해 둘 수 있다((void func(int a, {int b, int c = 2}))
- 옵션을 함수 선언시 꼭 사용하게 하려면 @required을 쓴다 (void func({@required int a}))
- 일급 함수를 지원한다
- 타입 비교는 kotlin과 같이 is 사용(다를 땐 is!)
- 타입 캐스트는 as를 통해 가능하다 (b가 double일때, int a = b as int)
- 변수는 선언만 하면 null이 된다
- ??는 null일때 실행되는 것이다 (a ?? "이건 null")
- ?는 null이 아닐때만 실행하고 싶으면 사용 (a?.toLowerCase())
- class 할당시 new는 쓰지않아도 가능하다
- java와 같이 생성자를 쓸 수 있으나 더 간단히 표현가능하다 (MyClass(int a, int b){this.a = a, this.b = b}를 MyClass(this.a, {this.b})와 같이 간단히 사용가능)
- 첫어두에 _를 쓰면 private이다(기본적으로 public이다. int _a)
- getter와 setter는 set 변수명(타입명 변수명),타입명 get 변수명 {return 리턴값}와 같이 사용가능(set a(int a) , int get a{return _a})
- 함수는 간단히 하기위해 => 를 사용할 수 있다 (int get a => _a)
- ..을 통해 class의 멤버메서드 호출가능(??)
- class를 그냥 인터페이스처럼 implements를 통해 사용할 수 있다 (그래서 인터페이스가 없다?)
- 선택적으로 override하고 싶다면 implements대신 with를 사용한다 (abstract와 같게 생각하면 될듯)
- Future는 비동기 요청하는 method할 때 사용 (잘 모르겠으니 공부!), async, await
```dart
Future<void> networkRequest() async {
  print("시작");
  await Future.dalayed(Duration(seconds: 3));
  print("끝");
  return;
}

Future networkRequest() async {
  print("시작");
  await Future.dalayed(Duration(seconds: 3));
  print("끝");
}
```
- stream도 비동기 처리를 위해 사용되나 차이점은 Future는 단발적, stream은 오래연결
-  StreamController, StreamBuilder
- 비동기 부분은 따로 공부할 것!!
- ///를 통해 주석 문서화 가능 (?)
