
```dart
class Devfest {
  static const String app_name = "Devfest";

  //* Preferences
  static SharedPreferences prefs;
  static const String loggedInPref = "loggedInPref1";

  static bool isDebugMode = false;

  // * Url related
  static String baseUrl = "https://storage.googleapis.com/gdg-devfest";

  static initDebugConfig() {
      baseUrl = "https://storage.googleapis.com/gdg-devfest";
      isDebugMode = true;
  }

}
```

* main.dart

```dart
Future<void> main() async {

  WidgetsFlutterBinding.ensureInitialized();
  
  Devfest.prefs = await SharedPreferences.getInstance();

  Devfest.initDebugConfig();

  runApp(MyApp());
}
```