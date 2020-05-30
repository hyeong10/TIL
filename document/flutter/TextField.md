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
  FocusNode nameFocusNode;

  final _nameController = TextEditingController();

  @override
  void initState() {
    // TODO: implement initState
    super.initState();
    nameFocusNode = FocusNode();
  }

  @override
  void dispose() {
    // TODO: implement dispose
    nameFocusNode.dispose();
    _nameController.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
        padding: const EdgeInsets.all(8.0),
        child: Form(
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
              TextField(
                controller: _nameController,
                onChanged: (text) {
                  print(text);
                },
                focusNode: nameFocusNode,
                // No validate!!, if you want, TextFormField use!
                decoration: InputDecoration(
                  hintText: 'What you want',
                  border: InputBorder.none,
                  labelText: '이름'
                ),
                autofocus: true,
              ),
              RaisedButton(
                onPressed: () {
                  FocusScope.of(context).requestFocus(nameFocusNode);
                },
                child: Text('Focus'),
              ),
              RaisedButton(
                onPressed: () {
                  print(_nameController.text);
                  showDialog(context: context,
                  builder: (context){
                    return AlertDialog(
                      content: Text(_nameController.text),
                    );
                  });
                },
                child: Text('get text'),
              )
            ],
          ),
        ),
      ),
    );
  }
}

```
