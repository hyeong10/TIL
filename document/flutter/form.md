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
      home: Forme(),
    );
  }
}

class Forme extends StatefulWidget {
  @override
  _FormeState createState() => _FormeState();
}

class _FormeState extends State<Forme> {
  final _formkey = GlobalKey<FormState>();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Form(
        key: _formkey,
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.center,
          children: <Widget>[
            TextFormField(
              validator: (value) {
                if (value.isEmpty) {
                  return "No!";
                }
              },
            ),
            Padding(
                padding: EdgeInsets.all(8.0),
                child: RaisedButton(
                  padding: EdgeInsets.all(8.0),
                  onPressed: () {
                    if (_formkey.currentState.validate()) {
                      Scaffold.of(_formkey.currentContext).showSnackBar(
                        SnackBar(content: Text("WoW"),)
                      );
                    }
                  },
                  child: Text("Press"),
                )
            ),
          ],
        ),
      ),
    );
  }
}

```
