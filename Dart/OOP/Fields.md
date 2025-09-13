
## 🔹 1. Field Nedir?

- **Field** = sınıfın içinde tanımlanan **değişkenlerdir**.    
- Nesnenin **durumunu (state)** tutar.
- Nesne oluşturulduğunda değer saklar.

```dart
class Person {
  String name;   // field
  int age;       // field

  Person(this.name, this.age);
}

void main() {
  var p = Person("Ahmet", 25);
  print("${p.name}, ${p.age}");
}
```

---

## 🔹 2. Field Türleri

### 🟢 a) Instance Fields

- Her nesneye özel alanlardır.
- Nesne sayısı kadar kopyalanır.

```dart
class Car {
  String brand;
  int year;

  Car(this.brand, this.year);
}

void main() {
  var c1 = Car("BMW", 2022);
  var c2 = Car("Audi", 2023);

  print(c1.brand); // BMW
  print(c2.brand); // Audi
}
```

---

### 🟢 b) Static Fields

- Tüm sınıf için **tek kopya** bulunur.
- Nesneye değil → sınıfa aittir.
- `ClassName.fieldName` ile erişilir.

```dart
class Counter {
  static int count = 0;

  Counter() {
    count++;
  }
}

void main() {
  var c1 = Counter();
  var c2 = Counter();
  var c3 = Counter();

  print(Counter.count); // 3
}
```

---

### 🟢 c) Final Fields

- Sadece **bir kez atanabilir**.
- Sonradan değiştirilemez.

```dart
class User {
  final String username;

  User(this.username);
}

void main() {
  var u = User("TkMatE");
  print(u.username); // TkMatE
  // u.username = "Ahmet"; ❌ hata
}
```

---

### 🟢 d) Late Fields

- `late` → değer daha sonra atanacak demektir.
- Lazy initialization (gerektiğinde başlatma) için kullanılır.

```dart
class Config {
  late String apiKey;

  void loadApiKey() {
    apiKey = "SECRET-123";
  }
}

void main() {
  var cfg = Config();
  cfg.loadApiKey();
  print(cfg.apiKey); // SECRET-123
}
```

⚠️ Eğer `late` field kullanmadan erişilirse → `LateInitializationError` hatası çıkar.

---

### 🟢 e) Const Fields

- `static const` ile tanımlanır.
- Compile-time sabittir.

```dart
class MathConstants {
  static const double pi = 3.14159;
}

void main() {
  print(MathConstants.pi); // 3.14159
}
```

---

## 🔹 3. Field’lara Varsayılan Değer

Field’lar için **default value** atanabilir.

```dart
class Person {
  String name = "Guest";
  int age = 0;
}

void main() {
  var p = Person();
  print("${p.name}, ${p.age}"); // Guest, 0
}
```

---

## 🔹 4. Private Fields

- Dart’ta **`_` (alt çizgi)** ile başlayan field → **library-private** olur.
- Yani başka dosyadan erişilemez.

```dart
class BankAccount {
  double _balance = 0; // private field

  void deposit(double amount) {
    _balance += amount;
  }

  double get balance => _balance; // getter
}

void main() {
  var acc = BankAccount();
  acc.deposit(100);
  print(acc.balance); // 100
  // print(acc._balance); ❌ başka dosyada hata
}
```

---

# 📌 Özet

- **Instance fields** → nesneye özel.
- **Static fields** → sınıfa özel.
- **Final fields** → sadece bir kez atanır.
- **Late fields** → sonradan atanır.
- **Const fields** → compile-time sabiti.
- **Private fields** → `_` ile başlar, başka dosyadan erişilemez.
