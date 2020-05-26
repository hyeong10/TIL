```dart
void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
        visualDensity: VisualDensity.adaptivePlatformDensity,
      ),
      home: SnapBar(),
    );
  }
}

class SnapBar extends StatefulWidget {
  @override
  _SnapBarState createState() => _SnapBarState();
}

class _SnapBarState extends State<SnapBar> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      // Builder 중요!!
      body: Builder(
        builder: (context) => Center(
          child: RaisedButton(
            onPressed: () {
              final snackbar = SnackBar(
                content: Text('Hello World'),
                action: SnackBarAction(label: "WOW", onPressed: () {
                  // 눌렀을때 처리
                },),
              );
              Scaffold.of(context).showSnackBar(snackbar);
            },
          ),
        ),
      ),
    );
  }
}
```
