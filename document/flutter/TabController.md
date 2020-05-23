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
      home: TabController(),
    );
  }
}

class TabController extends StatefulWidget {
  @override
  _TabControllerState createState() => _TabControllerState();
}

class _TabControllerState extends State<TabController> {
  @override
  Widget build(BuildContext context) {
    return DefaultTabController(
      child: Scaffold(
        appBar: AppBar(
          title: Text("TabController"),
          bottom: TabBar(
            tabs: <Widget>[
              Tab(icon: Icon(Icons.home), text: 'one'),
              Text('Two'),
              Text('Three'),
            ],
          ),
        ),
        body: TabBarView(
          children: <Widget>[
            Icon(Icons.cloud),
            Center(
                child: Text("Two")
            ),
            Text("Three"),
          ],
        ),
      ),
      length: 3,
    );
  }
}
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
      home: TabController(),
    );
  }
}

class TabController extends StatefulWidget {
  @override
  _TabControllerState createState() => _TabControllerState();
}

class _TabControllerState extends State<TabController> {
  @override
  Widget build(BuildContext context) {
    return DefaultTabController(
      child: Scaffold(
        appBar: AppBar(
          title: Text("TabController"),
          bottom: TabBar(
            tabs: <Widget>[
              Tab(icon: Icon(Icons.home), text: 'one'),
              Text('Two'),
              Text('Three'),
            ],
          ),
        ),
        body: TabBarView(
          children: <Widget>[
            Icon(Icons.cloud),
            Center(
                child: Text("Two")
            ),
            Text("Three"),
          ],
        ),
      ),
      length: 3,
    );
  }
}

```
