
```dart
ConstrainedBox(
    constraints: BoxConstraints.expand(
        height: MediaQuery.of(context).size.height * 0.2,
        width: MediaQuery.of(context).size.width * 0.3,
    ),
    child: CachedNetworkImage(
        fit: BoxFit.cover,
        imageUrl: speakers[i].speakerImage,
    ),
),
```