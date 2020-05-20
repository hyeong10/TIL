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
      home: TabPage(),
    );
  }
}

class TabPage extends StatefulWidget {
  @override
  _TabPageState createState() => _TabPageState();
}

class _TabPageState extends State<TabPage> {
  int _position = 0;
  List _pages = [
    Scaffold(
      body: ListView(
        children: <Widget>[
          ListTile(
            title: Text('First Page1'),
          ),
          ListTile(
            title: Text('First Page2'),
          ),
          ListTile(
            title: Text('First Page3'),
          ),
        ],
      ),
    ),
    Scaffold(
      body: Text('Second Page'),
    ),
    Scaffold(
      body: Text('Third Page'),
    )
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text("Tab Study"),
      ),
      body: Center(
        child: _pages[_position],
      ),
      bottomNavigationBar: BottomNavigationBar(
        onTap: (index) {
          setState(() {
            _position = index;
          });
        },
        currentIndex: _position,
        items: <BottomNavigationBarItem>[
          BottomNavigationBarItem(icon: Icon(Icons.home), title: Text('First')),
          BottomNavigationBarItem(
              icon: Icon(Icons.alarm), title: Text('Second')),
          BottomNavigationBarItem(icon: Icon(Icons.cloud), title: Text('Third'))
        ],
      ),
    );
  }
}

```
