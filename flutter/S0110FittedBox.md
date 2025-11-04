
```dart

class SpeakerPage extends StatelessWidget {
    static const String routeName = "/speakers";

    Widget socialActions(context, Speaker speaker) => FittedBox(
        child: Row(
          mainAxisAlignment: MainAxisAlignment.spaceBetween,
          children: <Widget>[
            IconButton(
              icon: Icon(
                FontAwesomeIcons.facebookF,
                size: 15,
              ),
              onPressed: () {
                launch(speaker.fbUrl);
              },
            ),
            IconButton(
              icon: Icon(
                FontAwesomeIcons.twitter,
                size: 15,
              ),
              onPressed: () {
                launch(speaker.twitterUrl);
              },
            ),
          ],
        ),
      );

}
