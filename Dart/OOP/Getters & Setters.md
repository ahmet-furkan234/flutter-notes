
## 🔹 1. Getter Nedir?

- Bir field’in (özelliğin) **okunmasını** kontrol eder.    
- `get` anahtar kelimesi ile tanımlanır.
- Normalde field gibi çağrılır, **metot gibi görünmez**.

### Örnek:

```dart
class Rectangle {
  final double width;
  final double height;

  Rectangle(this.width, this.height);

  // Alanı hesaplayan getter
  double get area => width * height;
}

void main() {
  var rect = Rectangle(5, 10);
  print(rect.area); // Çağırırken () yok → 50.0
}
```

> Burada `area` aslında bir method, ama `rect.area` şeklinde **field gibi** erişiyoruz.

---

## 🔹 2. Setter Nedir?

- Bir field’in **değerini değiştirmeyi** kontrol eder.
- `set` anahtar kelimesi ile tanımlanır.
- Parametre alır ve field gibi çağrılır.

### Örnek:

```dart
class BankAccount {
  double _balance = 0;

  // Getter
  double get balance => _balance;

  // Setter
  set balance(double amount) {
    if (amount >= 0) {
      _balance = amount;
    } else {
      print("Bakiye negatif olamaz!");
    }
  }
}

void main() {
  var account = BankAccount();
  account.balance = 100; // setter çağrılır
  print(account.balance); // getter çağrılır → 100.0

  account.balance = -50; // setter kontrol → "Bakiye negatif olamaz!"
}
```

---

## 🔹 3. Getter ve Setter ile Encapsulation (Kapsülleme)

- Private field’leri (`_` ile başlayanlar) koruyup, dışarıya kontrollü erişim verebiliriz.
- Böylece **iş kuralları (business rules)** sınıf içinde uygulanır.

### Örnek:

```dart
class Temperature {
  double _celsius = 0;

  // Celsius getter/setter
  double get celsius => _celsius;
  set celsius(double value) => _celsius = value;

  // Fahrenheit getter/setter
  double get fahrenheit => _celsius * 9 / 5 + 32;
  set fahrenheit(double value) => _celsius = (value - 32) * 5 / 9;
}

void main() {
  var temp = Temperature();
  temp.celsius = 25;
  print("Celsius: ${temp.celsius}");     // 25
  print("Fahrenheit: ${temp.fahrenheit}"); // 77

  temp.fahrenheit = 32;
  print("Celsius: ${temp.celsius}");     // 0
}
```

---

## 🔹 4. Sadece Getter veya Setter Kullanmak

- Bazı alanlar sadece okunabilir (`getter only`).
- Bazıları sadece yazılabilir (`setter only`, nadir kullanılır).

### Örnek:

```dart
class Circle {
  final double radius;
  Circle(this.radius);

  // sadece getter
  double get area => 3.14 * radius * radius;
}

void main() {
  var circle = Circle(3);
  print(circle.area); // 28.26
  // circle.area = 100; ❌ alan değiştirilemez
}
```

---

✅ Özet:

- **Getter** → Alan okumayı özelleştirir.
- **Setter** → Alan değiştirmeyi özelleştirir.
- Encapsulation sayesinde **field’leri koruyup** dışarıya kontrollü erişim veririz.
