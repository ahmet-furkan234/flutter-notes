
# 🔹 1. Temel Metot Tanımı

```dart
class Calculator {
  int add(int a, int b) {
    return a + b;
  }
}

void main() {
  var calc = Calculator();
  print(calc.add(3, 4)); // 7
}
```

- `add` → Metot ismi
- `(int a, int b)` → Parametreler
- `return a + b;` → Geri dönüş değeri

---

# 🔹 2. Void Metot (geri dönüşsüz)

```dart
class Printer {
  void printMessage(String msg) {
    print("Mesaj: $msg");
  }
}

void main() {
  var p = Printer();
  p.printMessage("Merhaba Dart!"); // "Mesaj: Merhaba Dart!"
}
```

---

# 🔹 3. Kısa (Arrow) Metot

Eğer metot tek satırdan oluşuyorsa `=>` kullanabiliriz.

```dart
class Math {
  int square(int n) => n * n;
}

void main() {
  var m = Math();
  print(m.square(5)); // 25
}
```

---

# 🔹 4. Optional Parameters (Opsiyonel Parametreler)

Dart’ta metot parametreleri **positional** veya **named** olabilir.

## a) Positional Optional

Köşeli parantez `[]` ile belirtilir.

```dart
class Greeting {
  void sayHello([String name = "Misafir"]) {
    print("Merhaba $name!");
  }
}

void main() {
  var g = Greeting();
  g.sayHello();        // Merhaba Misafir!
  g.sayHello("TkMatE"); // Merhaba TkMatE!
}
```

## b) Named Optional

Süslü parantez `{}` ile belirtilir.

```dart
class User {
  void login({String username = "guest", String password = "1234"}) {
    print("Kullanıcı: $username, Şifre: $password");
  }
}

void main() {
  var u = User();
  u.login(); // Kullanıcı: guest, Şifre: 1234
  u.login(username: "TkMatE", password: "abc123");
}
```

---

# 🔹 5. Static Methods

Sınıfın nesnesine gerek kalmadan doğrudan çağrılır.

```dart
class Utils {
  static double pi = 3.14;

  static double areaOfCircle(double r) => pi * r * r;
}

void main() {
  print(Utils.areaOfCircle(5)); // 78.5
}
```

---

# 🔹 6. Private Methods

`_` ile başlayan metotlar sadece **aynı dosya içinde** erişilebilir.

```dart
class Secret {
  void _hiddenMethod() {
    print("Bu gizli bir metot!");
  }
}
```

---

# 🔹 7. Instance Methods vs Class Methods

- **Instance method** → Nesne üzerinden çağrılır (default).
    
- **Static method** → Sınıf adı üzerinden çağrılır.
    

---

# 🔹 8. Method Overriding (Metot Ezme)

Alt sınıf, üst sınıfın metodunu ezebilir.

```dart
class Animal {
  void sound() => print("Bir ses çıkarır");
}

class Dog extends Animal {
  @override
  void sound() => print("Hav Hav!");
}

void main() {
  var dog = Dog();
  dog.sound(); // Hav Hav!
}
```

---

✅ Özet:

- **Instance methods** → Nesne davranışlarını tanımlar.
    
- **Static methods** → Nesneye gerek yok, sınıfa bağlıdır.
    
- **Optional params** → Esnek parametre kullanımı sağlar.
    
- **Override** → Kalıtımda özelleştirme yapar.
    

---

👉 TkMatE, sıradaki konu **inheritance (kalıtım)** olsun mu, yoksa metotlarda **ileri seviye (async methods, operator overloading)** örneklerine mi girelim?