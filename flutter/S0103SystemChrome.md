

```dart
Future<void> main() async {
    SystemChrome.setSystemUIOverlayStyle(
        SystemUiOverlayStyle(
        statusBarColor: Colors.transparent,
        ),
    );

    //* Forcing only portrait orientation
    SystemChrome.setPreferredOrientations([DeviceOrientation.portraitUp, DeviceOrientation.portraitDown]);

    runApp(MyApp());
}
```