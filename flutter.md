# Flutter Widgets, Routing, and State Management Notes

## 1️⃣ Basic Flutter Widgets
### Structural Widgets:
- **Container** – A box model container.
  ```dart
  Container(
    width: 100,
    height: 100,
    color: Colors.blue,
  )
  ```
- **Column & Row** – Layout widgets for vertical & horizontal alignment.
  ```dart
  Column(
    children: [
      Text('Hello'),
      Text('World'),
    ],
  )
  ```
- **Stack** – Overlapping widgets.
  ```dart
  Stack(
    children: [
      Container(width: 100, height: 100, color: Colors.red),
      Positioned(top: 10, left: 10, child: Text("Overlay")),
    ],
  )
  ```

### Input & Interaction:
- **TextField** – User input field.
  ```dart
  TextField(
    decoration: InputDecoration(labelText: 'Enter text'),
  )
  ```
- **ElevatedButton** – Button with elevation.
  ```dart
  ElevatedButton(
    onPressed: () {},
    child: Text('Click me'),
  )
  ```

### Display & Styling:
- **Text** – Display text.
  ```dart
  Text('Hello, Flutter!', style: TextStyle(fontSize: 24))
  ```
- **Image** – Load images.
  ```dart
  Image.network('https://example.com/image.jpg')
  ```
- **ListView** – Scrollable list.
  ```dart
  ListView(
    children: [Text('Item 1'), Text('Item 2')],
  )
  ```

---

## 2️⃣ Advanced Flutter Widgets
- **FutureBuilder & StreamBuilder** – Async data handling.
  ```dart
  FutureBuilder(
    future: fetchData(),
    builder: (context, snapshot) {
      if (snapshot.connectionState == ConnectionState.waiting) {
        return CircularProgressIndicator();
      } else {
        return Text(snapshot.data.toString());
      }
    },
  )
  ```

- **AnimatedContainer** – Smooth animations.
  ```dart
  AnimatedContainer(
    duration: Duration(seconds: 1),
    width: 100,
    height: 100,
    color: Colors.blue,
  )
  ```

---

## 3️⃣ Routing in Flutter
### **Navigation Methods:**
```dart
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => SecondScreen()),
);
```
```dart
Navigator.pop(context);
```

### **Routing Libraries:**
- **go_router** (Recommended) – Simple, declarative routing.
  ```dart
  final GoRouter _router = GoRouter(
    routes: [
      GoRoute(path: '/', builder: (context, state) => HomeScreen()),
    ],
  );
  ```

---

## 4️⃣ State Management in Flutter
### **Basic State Management:**
- **setState** – Used within StatefulWidgets.
  ```dart
  setState(() {
    counter++;
  });
  ```

### **Provider Example:**
```dart
class Counter extends ChangeNotifier {
  int value = 0;
  void increment() {
    value++;
    notifyListeners();
  }
}
```

---

## 5️⃣ Useful Commands
```sh
flutter create my_app  # Create a new Flutter project
flutter run  # Run app in debug mode
flutter build apk  # Build an APK for Android
flutter build ios  # Build for iOS
flutter pub get  # Fetch dependencies
flutter doctor  # Check environment setup
```

---

These notes cover both **basic** and **advanced** concepts for Flutter development with **code examples**. 🚀

