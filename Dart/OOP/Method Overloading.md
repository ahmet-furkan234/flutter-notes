
Ama şunu bilmen lazım:  
👉 Dart’ta **Java veya C# gibi doğrudan method overloading (aynı isim, farklı parametre imzası)** **desteklenmez**.  
Çünkü Dart derleyicisi fonksiyonları **isim üzerinden ayırt eder**, parametre sayısına bakmaz.

---

# 🔹 Peki Dart’ta method overloading yerine ne var?

Dart’ta overloading ihtiyacını şu yollarla çözeriz:

---

## 1️⃣ Opsiyonel Parametreler (Positional / Named)

En yaygın yöntem → tek bir method yazarsın, farklı çağrılara izin verir.

```dart
class Calculator {
  int add(int a, [int b = 0, int c = 0]) {
    return a + b + c;
  }
}

void main() {
  var calc = Calculator();
  print(calc.add(5));        // 5  (sadece a)
  print(calc.add(5, 10));    // 15 (a + b)
  print(calc.add(5, 10, 20)); // 35 (a + b + c)
}
```

📌 Burada aslında **method overloading yerine opsiyonel parametreler** kullandık.

---

## 2️⃣ Named Parameters

Overloading gibi davranır çünkü farklı kombinasyonlarla çağrılabilir.

```dart
class Greeting {
  void sayHello({String? name, int? age}) {
    if (name != null && age != null) {
      print("Merhaba $name, yaşın $age");
    } else if (name != null) {
      print("Merhaba $name");
    } else {
      print("Merhaba Misafir!");
    }
  }
}

void main() {
  var g = Greeting();
  g.sayHello();                    // Merhaba Misafir!
  g.sayHello(name: "TkMatE");      // Merhaba TkMatE
  g.sayHello(name: "TkMatE", age: 25); // Merhaba TkMatE, yaşın 25
}
```

---

## 3️⃣ Farklı İsimli Constructor’lar (Named Constructors)

Özellikle nesne oluştururken **constructor overloading** yerine **named constructor** kullanılır.

```dart
class Point {
  int x, y;

  Point(this.x, this.y);

  Point.origin() : x = 0, y = 0; // farklı constructor
  Point.unit() : x = 1, y = 1;
}

void main() {
  var p1 = Point(3, 4);
  var p2 = Point.origin();
  var p3 = Point.unit();

  print("p1: (${p1.x}, ${p1.y})"); // (3, 4)
  print("p2: (${p2.x}, ${p2.y})"); // (0, 0)
  print("p3: (${p3.x}, ${p3.y})"); // (1, 1)
}
```

---

## 4️⃣ Factory Constructors

Overloading gibi davranan başka bir teknik.  
Duruma göre farklı nesneler döndürebilir.

```dart
class Shape {
  final String type;

  Shape._(this.type);

  factory Shape.circle() => Shape._("Circle");
  factory Shape.square() => Shape._("Square");
}

void main() {
  var s1 = Shape.circle();
  var s2 = Shape.square();

  print(s1.type); // Circle
  print(s2.type); // Square
}
```

---

# ✅ Özet

- Dart’ta **doğrudan method overloading yok**.
- Onun yerine:
    1. **Opsiyonel parametreler `[ ]` / `{ }`**
    2. **Named constructors**
    3. **Factory constructors** kullanılır.
