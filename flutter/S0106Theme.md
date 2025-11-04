
```dart
class HomePage extends StatelessWidget {
  
  static const String routeName = "/";
  
  const HomePage({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
        title: 'Google Devfest',
        debugShowCheckedModeBanner: false,
        theme: ThemeData(
              fontFamily: Devfest.google_sans_family,
              // 主题色
              primarySwatch: Colors.red,
              primaryColor: configBloc.darkModeOn ? Colors.black : Colors.white,
              disabledColor: Colors.grey,
              cardColor: configBloc.darkModeOn ? Colors.black : Colors.white,
              canvasColor:
                  configBloc.darkModeOn ? Colors.black : Colors.grey[50],
              brightness:
                  configBloc.darkModeOn ? Brightness.dark : Brightness.light,
              buttonTheme: Theme.of(context).buttonTheme.copyWith(
                  colorScheme: configBloc.darkModeOn
                      ? ColorScheme.dark()
                      : ColorScheme.light()),
              appBarTheme: AppBarTheme(
                //控制 Material 组件阴影效果的属性
                elevation: 0.0,
              ),
            ),
        home: HomePage(),    
        routes: {
            HomePage.routeName: (context) => HomePage(),
        }  
    );
  }
}
```