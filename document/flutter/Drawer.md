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
      home: DrawerPage(),
    );
  }
}

class DrawerPage extends StatefulWidget {
  @override
  _DrawerPageState createState() => _DrawerPageState();
}

class _DrawerPageState extends State<DrawerPage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text("Drawer Study"),
        backgroundColor: Colors.yellow,
      ),
      drawer: Drawer(
          child: ListView(
        padding: EdgeInsets.zero,
        children: <Widget>[
          DrawerHeader(
            child: Center(
              child: Text("Drawer"),
            ),
            decoration: BoxDecoration(color: Colors.yellow),
          ),
          ListTile(
            title: Text("item 1"),
            onTap: () {
              Navigator.pop(context);
            },
          ),
          ListTile(
            title: Text("item 2"),
          ),
          ListTile(
            title: Text("item 3"),
          ),
        ],
      )),
    );
  }
}

```
