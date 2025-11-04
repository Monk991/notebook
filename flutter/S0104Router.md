
```dart
class HomePage extends StatelessWidget {
  
  static const String routeName = "/";
  
  const HomePage({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Google Devfest',
      debugShowCheckedModeBanner: false,
      home: HomePage(),    
      routes: {
        HomePage.routeName: (context) => HomePage(),
      }  
    );
  }
}
```