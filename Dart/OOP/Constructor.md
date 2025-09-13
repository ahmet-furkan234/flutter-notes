
## 1. **Default / Positional Constructor**

En temel constructor → parametreler sırayla verilir.

```dart
class Person {
  String name;
  int age;

  Person(this.name, this.age); // positional constructor
}

void main() {
  var p1 = Person("Ahmet", 25);
  var p2 = Person("Ayşe", 30);

  print("${p1.name}, ${p1.age}"); // Ahmet, 25
  print("${p2.name}, ${p2.age}"); // Ayşe, 30
}
```

---

## 2. **Named Parameters (Adlandırılmış Parametreler)**

Parametreler süslü parantez `{}` ile tanımlanır.

```dart
class Car {
  String brand;
  int year;

  Car({required this.brand, required this.year});
}

void main() {
  var car1 = Car(brand: "BMW", year: 2022);
  var car2 = Car(year: 2023, brand: "Audi"); // sıraya gerek yok

  print("${car1.brand} - ${car1.year}"); // BMW - 2022
  print("${car2.brand} - ${car2.year}"); // Audi - 2023
}
```

👉 Ayrıca parametreleri opsiyonel yapabilirsin:

```dart
class Book {
  String title;
  String? author;

  Book({required this.title, this.author});
}

void main() {
  var b1 = Book(title: "Dart Guide");
  var b2 = Book(title: "Flutter", author: "TkMatE");

  print("${b1.title} - ${b1.author}"); // Dart Guide - null
  print("${b2.title} - ${b2.author}"); // Flutter - TkMatE
}
```

---

## 3. **Named Constructors**

Aynı sınıfta birden fazla constructor tanımlayabilirsin.

```dart
class User {
  String name;
  int age;

  User(this.name, this.age);

  // Guest constructor
  User.guest()
      : name = "Guest",
        age = 0;

  // FromJson constructor
  User.fromJson(Map<String, dynamic> json)
      : name = json['name'],
        age = json['age'];
}

void main() {
  var u1 = User("Ahmet", 23);
  var u2 = User.guest();
  var u3 = User.fromJson({"name": "Ali", "age": 40});

  print("${u1.name}, ${u1.age}"); // Ahmet, 23
  print("${u2.name}, ${u2.age}"); // Guest, 0
  print("${u3.name}, ${u3.age}"); // Ali, 40
}
```

---

## 4. **Initializer List**

Constructor gövdesinden önce çalışır. `final` değişkenler için çok kullanılır.

```dart
class Point {
  final int x;
  final int y;

  Point(int xVal, int yVal)
      : x = xVal,
        y = yVal {
    print("Point created: ($x, $y)");
  }
}

void main() {
  var p = Point(3, 5); // Point created: (3, 5)
}
```

Daha ileri kullanım:

```dart
class Circle {
  final double radius;
  final double area;

  Circle(this.radius) : area = 3.14 * radius * radius;
}

void main() {
  var c = Circle(5);
  print("Radius: ${c.radius}, Area: ${c.area}");
  // Radius: 5.0, Area: 78.5
}
```

---

## 5. **Redirecting Constructors**

Bir constructor başka bir constructor’ı çağırabilir.

```dart
class Rectangle {
  int width;
  int height;

  Rectangle(this.width, this.height);

  // Square constructor redirects to Rectangle
  Rectangle.square(int size) : this(size, size);
}

void main() {
  var r1 = Rectangle(10, 20);
  var r2 = Rectangle.square(15);

  print("Rectangle: ${r1.width}x${r1.height}"); // 10x20
  print("Square: ${r2.width}x${r2.height}");    // 15x15
}
```

---

## 6. **Const Constructors**

Compile-time sabit nesne üretir.

```dart
class ImmutablePoint {
  final int x;
  final int y;

  const ImmutablePoint(this.x, this.y);
}

void main() {
  const p1 = ImmutablePoint(1, 2);
  const p2 = ImmutablePoint(1, 2);

  print(identical(p1, p2)); // true → aynı nesne
}
```

Daha ileri örnek:

```dart
class Color {
  final int red;
  final int green;
  final int blue;

  const Color(this.red, this.green, this.blue);

  static const Color black = Color(0, 0, 0);
  static const Color white = Color(255, 255, 255);
}

void main() {
  var c1 = Color.black;
  var c2 = Color.white;

  print("Black: (${c1.red}, ${c1.green}, ${c1.blue})");
  print("White: (${c2.red}, ${c2.green}, ${c2.blue})");
}
```

---

📌 **Özet:**

- Positional → Sıra ile parametre
    
- Named Parameters → Daha okunaklı, sıradan bağımsız
    
- Named Constructors → Farklı senaryolar için birden fazla ctor
    
- Initializer List → Final/const alanlar için
    
- Redirecting → Tekrardan kaçınmak
    
- Const Constructor → Compile-time sabit nesneler
    

---

👉 TkMatE, istersen sıradaki konumuz **Class Members (fields, methods, getters, setters)** olsun mu, yoksa constructor’ların daha “ileri düzey kullanım senaryolarına” (ör. factory constructor) da bakalım mı?