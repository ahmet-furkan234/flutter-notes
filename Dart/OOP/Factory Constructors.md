
## 🔹 1. Factory Constructor Nedir?

- Normal constructor her zaman **yeni bir nesne** döndürür.
- **Factory constructor** ise:
    - Her zaman yeni bir nesne oluşturmak zorunda değildir.
    - Önceden var olan bir nesneyi döndürebilir.
    - Bir alt sınıf nesnesi döndürebilir.
    - Nesne oluşturma mantığını kontrol altına alır.


👉 Yani `factory` ile daha esnek bir constructor yazabilirsin.

---

## 🔹 2. Basit Örnek: Önceden var olan nesneyi döndürmek

```dart
class Logger {
  final String name;
  static final Map<String, Logger> _cache = {};

  factory Logger(String name) {
    return _cache.putIfAbsent(name, () => Logger._internal(name));
  }

  Logger._internal(this.name);
}

void main() {
  var l1 = Logger("UI");
  var l2 = Logger("UI");

  print(identical(l1, l2)); // true → aynı nesne
}
```

✅ `factory` burada aynı isimle çağırılan logger’ı tekrar tekrar oluşturmuyor, cache’den döndürüyor.

---

## 🔹 3. Alt sınıf döndürmek

Factory constructor, sınıfın kendisi yerine **alt sınıf** döndürebilir.

```dart
abstract class Shape {
  factory Shape(String type) {
    if (type == "circle") return Circle();
    if (type == "square") return Square();
    throw "Unknown shape type";
  }
}

class Circle implements Shape {}
class Square implements Shape {}

void main() {
  Shape s1 = Shape("circle");
  Shape s2 = Shape("square");

  print(s1.runtimeType); // Circle
  print(s2.runtimeType); // Square
}
```

✅ Burada `Shape` aslında abstract, ama `factory` sayesinde alt sınıf döndürülüyor.

---

## 🔹 4. Singleton Pattern (Tek Nesne)

Dart’ta singleton en çok **factory constructor** ile yapılır.

```dart
class Database {
  static final Database _instance = Database._internal();

  factory Database() {
    return _instance;
  }

  Database._internal(); // private constructor
}

void main() {
  var db1 = Database();
  var db2 = Database();

  print(identical(db1, db2)); // true → tek nesne
}
```

✅ Aynı `Database` nesnesi her yerde kullanılır.

---

## 🔹 5. JSON Parsing Örneği

Factory constructor genelde **veri dönüşümleri** için kullanılır.

```dart
class User {
  final String name;
  final int age;

  User(this.name, this.age);

  factory User.fromJson(Map<String, dynamic> json) {
    return User(json['name'], json['age']);
  }
}

void main() {
  var json = {"name": "TkMatE", "age": 25};
  var user = User.fromJson(json);

  print("${user.name}, ${user.age}"); // TkMatE, 25
}
```

✅ Daha temiz ve güvenli JSON’dan nesne oluşturma yöntemi.

---

# 📌 Özet

- **factory** constructor:
    - Nesne oluşturma sürecini kontrol eder.
    - Cache’den var olan nesne döndürebilir.
    - Alt sınıf döndürebilir.
    - Singleton oluşturmak için ideal.
    - Veri dönüşümlerinde (JSON, API vs.) sık kullanılır.