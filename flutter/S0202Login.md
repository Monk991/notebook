
```dart
new Container(
    padding: const EdgeInsets.all(40.0),
    child: new Form(
        autovalidate: true,
        child: new Column(
            mainAxisAlignment: MainAxisAlignment.start,
            children: <Widget>[
            new TextFormField(
                decoration: new InputDecoration(
                    labelText: "Enter Email",
                    fillColor: Colors.white),
                keyboardType: TextInputType.emailAddress,
            ),
            new TextFormField(
                decoration: new InputDecoration(
                labelText: "Enter Password",
                ),
                obscureText: true,
                keyboardType: TextInputType.text,
            ),
            new Padding(
                padding: const EdgeInsets.only(top: 60.0),
            ),
            new MaterialButton(
                height: 50.0,
                minWidth: 150.0,
                color: Colors.green,
                splashColor: Colors.teal,
                textColor: Colors.white,
                child: new Icon(FontAwesomeIcons.signInAlt),
                onPressed: () {},
            )
            ],
        ),
    ),
)
```