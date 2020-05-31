```dart
import 'package:flutter/material.dart';

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
      home: SwipeDismiss(),
    );
  }
}

class SwipeDismiss extends StatefulWidget {
  @override
  _SwipeDismissState createState() => _SwipeDismissState();
}

class _SwipeDismissState extends State<SwipeDismiss> {
  final _items = List<String>.generate(20, (index) => "$index");

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: ListView.builder(
          itemCount: _items.length,
          itemBuilder: (context, index) {
            final item = _items[index];
            return Dismissible(
              background: Container(color: Colors.red,),
              direction: DismissDirection.startToEnd,
              onDismissed: (direction) {
                setState(() {
                  if (direction == DismissDirection.startToEnd)
                    _items.removeAt(index);
                });
              },
              child: ListTile(
                title: Text('${_items[index]}'),
              ),
              key: Key(item),
            );
          }),
    );
  }
}

```
